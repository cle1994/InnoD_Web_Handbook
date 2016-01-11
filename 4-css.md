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
