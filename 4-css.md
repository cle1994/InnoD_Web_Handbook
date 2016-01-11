# CSS

**Quick Jump**

* [Selectors](4-css.md#selectors)
* [Media Queries](4-css.md#media-queries)
* [Before/After](4-css.md#before)
* [Animations/Key-frames](4-css.md#animations)
* [Prefixing](4-css.md#prefixing)
* [Examples](4-css.md#examples)

## Introduction

CSS, cascading style sheets, is a language used to describe the presentation
for markup languages. It's most commonly used to style web pages. The reasoning
behind *cascading* is that styles found later in the style sheets "override"
previous ones.

Fun fact, since CSS is cascading, browsers
apply styles right to left which means a "child", or more deeply nested element,
is applied first, then it checks the "parent" for properties not already
applied. You can see the benefits of not having to recursively check properties,
and not having to wait for the entire DOM to render. This is partially the
reason why, in many cases, not all, it's faster, and more stylistic, to use
`class` over `id`. There are plenty of articles about this stuff, Google away if
you're interested.

While I would love to sit here and list all the possible properties you can use
it's conveniently available
[here](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference) with examples
thanks to Mozilla.

I will, however, go over some ideas to get you started with all those possible
properties.

<a name="selectors"></a>
## Selectors

Selectors allow you to select which elements you want to style via the css
properties.

#### By tag

The simplest form of selection is through tags. You can simply say which tag
should be styled.

```css
p {
  background: blue;
}
```

Here we're saying that all `p` (paragraph) elements should have a blue
background. Though this can work with name spacing (see below) it's not always
the best route to take. Say I have the following css:

```css
div {
  color: red;
}
```

All `div` elements will have a text color of red, unless you override it. this
is probably not what you wanted, so you should use a more specific selector.

#### By class

Classes are the most likely way you will be styling your elements. Classes can
be applied to 1 or more elements. If your element has class `center`.

```html
<div class="center">
  All this text will be centered.
</div>
<div class="center">
  So will the text here.
</div>
```

then you can select all the elements with class `center` in css by adding a
period `.` before the classname, like so

```css
.center {
  text-align: center;
}
```

#### By ID

IDs are probably the second most common way to style elements. IDs should be
unique to an element so styles for an ID will be applied to the first found
element with that ID.

```html
<div id="hello">
  Hello World
</div>
```

You would select this element in CSS with a pound sign, hashtag, whatever and
then the ID.

```css
#hello {
  background: green;
}
```

IDs will always override classes, so even if a class is after id in the style
sheet, the IDs properties will be used first. This is because IDs should be
more specific that classes.

#### By pseudo-classes

Pseudo classes are special keywords added to other selectors that specify
state, such as *hovering*, *visited*, *focus*, *first-child*, etc. There's a
bunch that I don't remember off the top of my head, but the syntax for all
pseudo-classes is a selector (tag, id, class) followed by a `:`, colon,
followed by it's pseudo class.

```css
a.big {
  color: black;
}

a.big:hover {
  color: green;
}
```

This means that an `a` tag with class `big` would normally be black but on
hover it's green.

#### By relation

You can select an element by relation. Say you know the class of an element,
and you want to style it's next sibling, you can do that. Or you have a parent
and you want to style it's direct child, you can do that too.

```css
.parent .child {
  // Stuff
}
```

This says you style elements of class child that are within elements of class
parent. Class child can be a direct child or a child of child, etc.

```css
.parent > .direct-child {
  // Stuff
}
```

If you want a direct child (not grandchildren, great grandchildren, etc.) then
you do `parent > child`

```css
.hello + .world {
  // Stuff
}
```

This is for selecting siblings. So element with class world is a sibling of
element of class hello.

<a name="media-queries"></a>
## Media Queries

Media queries are used mainly for responsive design. They allow you to limit
certain styles and properties for different media type and screen size.

A lot of people will be asking, *"why would you need to worry about media
queries or responsive design when there are tools like bootstrap"*. Well for
one, bootstrap is relatively heavy and it doesn't allow for great customization
unless you're willing to hack things around it. Even though bootstrap allows you
to pick and choose the parts you need, there's a lot dependencies and you'll end
up with bloat you might not need. Another reason is that it's extremely
limiting to your designs, there's a strict 12 column grid system that breaks
at specific widths and your design must fit into those guidelines. Problem is
content doesn't always flow well at those specific widths and columns so it's
better to use your own media queries and breakpoints that match your design.

#### Using media queries

In it's simplistic form, you do the following

```css
.hello {
  width: 80%;
  margin: 0 auto;
  font-size: 20px;
  font-size: 1.25rem;
}

@media (max-width: 880px) {
  .hello {
    width: 100%;
  }
}
```

There's a class hello that normally would have a width of `80%` but when the
screen is less than `880px` the width will be `100%`.

If you want to have multiple expressions you can chain them together with the
and operator.

```css
.hello {
  width: 80%;
  margin: 0 auto;
  font-size: 20px;
  font-size: 1.25rem;
}

@media (max-width: 880px) and (min-width: 640px) {
  .hello {
    width: 100%;
  }
}
```

Here the properties only apply with the screen is between `640px` and `880px`.

Check out[Mozilla's documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)
for all the possible expressions you can use.

<a name="before"></a>
## Before and After

`::before` and `::after` are pseudo-elements you can add in CSS to add cosmetic
or visual content to an element. They must have a content property and are by
default display inline.

When using `::before` the pseudo-element is added as the first child to the
selected element. `::after` acts as the last child of the selected element.

```html
<div class="hello">Hello World</div>
```

```css
.hello::before {
  content: '&lt;';
  margin-right: 10px;
}

.hello::after {
  content: '&gt;';
  margin-left: 10px;
}
```

would be similar to doing

```html
<span class="hello-flank--left">&lt;</span>
<span class="hello">Hello World</span>
<span class="hello-flank--right">&gt;</span>
```

```css
.hello-flank--left {
  margin-right: 10px;
}

.hello-flank--right {
  margin-left: 10px;
}
```

#### Cooler Example

When making a hamburger menu icon, you could import an image or you can use
three separate elements like so

```html
<div class="hamburger">
  <div class="bar bar1"></div>
  <div class="bar bar2"></div>
  <div class="bar bar3"></div>
</div>
```

and style each bar element separately, for you can simplify the markup and use
`::before` and `::after` in css.

```html
<div class="hamburger">
  <div class="bar"></div>
</div>
```

```css
.hamburger {
  position: absolute;
  top: 20px;
  right: 20px;
  width: 30px;
  height: 23px;
  display: none;
  cursor: pointer;
}

.hamburger .bar {
  position: absolute;
  top: 0px;
  width: 30px;
  height: 3px;
  background: #cccccc;

  transition: all 0.2s;
}

.hamburger .bar::before {
  position: absolute;
  top: 10px;
  width: 30px;
  height: 3px;
  background: #cccccc;

  transition: all 0.2s;
}

.hamburger .bar::after {
  position: absolute;
  top: 20px;
  width: 30px;
  height: 3px;
  background: #cccccc;

  transition: all 0.2s;
}

.hamburger.close .bar {
  top: 10px;
  transform: rotate(45deg);
}

.hamburger.close .bar::before {
  opacity: 0;
  width: 0px;
  height: 0px;
}

.hamburger.close .bar::after {
  top: 10px;
  transform: rotate(-45deg);
}
```

<a name="animations"></a>
## Animations and Key-frames

Animations and key-frames allow you to control steps to animate your element.

```css
@keyframe move {
  0% {
    top: 0;
    left: 0;
  }
  25% {
    top: 10px;
    left: 10px;
  }
  50% {
    top: 20px;
    left: 20px;
  }
  75% {
    top: 50px;
    left: 50px;
  }
  100% {
    top: 100px;
    left: 100px;
  }
}
```

The element will move from `(0, 0)` to `(100, 100)` but you notice it isn't
a linear movement. The percentages say at that percentage in time, do apply
these properties.

You can see a cool example below :smiley:

[Innovative Design Ripple](http://codepen.io/cle1994/pen/QwwXjx)

Again, check out
[Mozilla's documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/@keyframes)
for comprehensive documentation.

<a name="prefixing"></a>
## Prefixing

Because browser run different rendering engines, you need need to prefix some
CSS properties so the browser knows how to render them. These are mostly
applicable to transitions, keyframes, and animations.

The general rules are:
* -moz- for Mozilla Firefox
* -ms- for Internet Explorer
* -o- for Operator
* -webkit- for Chrome and Safari

There are tools such as
[autoprefixer](https://github.com/postcss/autoprefixer)
and [cssnano](https://github.com/ben-eb/cssnano) that will do prefixes
for you and remove unnecessary ones but we'll cover that another day.

```css
-webkit-transform: rotate(-45deg);
-moz-transform: rotate(-45deg);
-o-transform: rotate(-45deg);
transform: rotate(-45deg);
```

Go to [caniuse.com](http://caniuse.com/) to see what you need to prefix.

<a name="examples"></a>
## Examples

Here are some useful CSS snippets that can make your life easier.

##### Center a <div>

```css
.center {
  width: 50%;
  margin: 0 auto;
}
```

##### Vertically align an element

```css
.vertically-align {
  position: relative;
  top: 50%;
  transform: translateY(-50%);
}
```

##### Center and display elements inline
```css
.parent {
  text-align: center;
}

.parent .inline-child {
  display: inline-block;
  margin: 0 10px;
}
```

##### Arrows

```css
.arrow-up {
	width: 0;
	height: 0;
	border-left: 10px solid transparent;
	border-right: 10px solid transparent;
	border-bottom: 10px solid black;
}

.arrow-down {
	width: 0;
	height: 0;
	border-left: 10px solid transparent;
	border-right: 10px solid transparent;
	border-top: 10px solid #f00;
}

.arrow-right {
	width: 0;
	height: 0;
	border-top: 10px solid transparent;
	border-bottom: 10px solid transparent;
	border-left: 10px solid green;
}

.arrow-left {
	width: 0;
	height: 0;
	border-top: 10px solid transparent;
	border-bottom: 10px solid transparent;
	border-right:10px solid blue;
}
```

These are just some random snippets I thought of on the spot, open some issues
if you want to see more! I'll try to not out a couple a day.
