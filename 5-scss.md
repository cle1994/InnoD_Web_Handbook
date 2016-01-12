# SCSS (Sass)

**Quick Jump**

* [Compiled](5-scss.md#compiled)
* [Nesting](5-scss.md#nesting)
* [Variables](5-scss.md#variables)
* [Mixins](5-scss.md#mixins)
* [Extending](5-scss.md#extending)
* [Import](5-scss.md#import)

## Introduction

"CSS with superpowers"

> Sass is the most mature, stable, and powerful professional grade CSS
> extension language in the world.

As your applications and style sheets become more complicated, writing and
maintaining pure CSS becomes a huge burden. Sass is a CSS preprocessor that
lets you use features like variables, nesting, mixins, inheritance, and many
more that aren't currently available with CSS. All this makes maintaining
your style sheets a lot easier.

Full documentation for Sass can be found [here](http://sass-lang.com/).

*I personally use the SCSS variant of Sass because I like that it looks like
normal CSS but feel free to explore the simplified syntax of Sass. From what
I've seen SCSS is more popular though.*

<a name="compiled"></a>
## Compiled

`SCSS` or `Sass` must be compiled to CSS before it is used. Browsers cannot
process Sass files of any kind.

The [Sass](http://sass-lang.com/install) website has plenty of instructions on
how to install and compile Sass.

At some point, I'll be added instructions on how to use Sass with
[Gulp](http://gulpjs.com/) and [Webpack](https://webpack.github.io/). If you're
interested my
[Angular Boilerplate](https://github.com/cle1994/boilerplate-angular) has a
`gulpfile.js` that uses gulp to compile Sass and my
[personal website](https://github.com/cle1994/personal-website)
has a webpack config for compiling Sass.

<a name="nesting"></a>
## Nesting

Much like how HTML has nested elements and a visual hierarchy, Sass allows you
to have that exact same hierarchy but for your style sheets.

For the following HTML

```html
<ul class="navigation">
  <li class="link">Home</li>
  <li class="link">About</li>
  <li class="link">Contact</li>
</ul>
```

here's what nested elements and their styles would look like in plain `CSS`

```css
.navigation {
  width: 100%;
  height: 64px;
  text-align: center;
}

.navigation .link {
  display: inline-block;
  margin: 0 10px;
}
```

and here's what it looks like in `SCSS`

```scss
.navigation {
  width: 100%;
  height: 64px;
  text-align: center;

  .link {
    display: inline-block;
    margin: 0 10px;
  }
}
```

As you can see it's a lot easier to understand how elements relate to each other
with Sass and it's a lot faster to write.

You can also use nesting for chaining multiple classes more easily. A common
example is with buttons where you have some base properties but descriptors to
change buttons colors.

Here is an example in plain `CSS`

```css
.btn {
  background: none;
  border-radius: 2px;
  border: 2px solid gray;
  color: gray;
}

.btn.btn--danger {
  border: 2px solid red;
  color: red;
}

.btn.btn--success {
  border: 2px solid green;
  color: green;
}
```

And here it is in `SCSS`

```scss
.btn {
  background: none;
  border-radius: 2px;
  border: 2px solid gray;
  color: gray;

  &.btn--danger {
    border: 2px solid red;
    color: red;
  }

  &.btn--success {
    border: 2px solid green;
    color: green;
  }
}
```

The ampersand (&) says to take the parent class and add whatever is after to it.

```scss
.paragraph {
  color: black;

  & .light {
    color: grey;
  }
}
```

is the same as

```scss
.paragraph {
  color: black;

  .light {
    color: grey;
  }
}
```

If you use Sass for nothing else, use it for the nesting.

<a name="variables"></a>
## Variables

Ever work on a website and had to keep checking the hex code for a color? How
about one where there's 20 different shades of the same brand color? Meet
variables for CSS, brought to you by Sass.

Short and simple you with a `$` in front of your variable name.

```scss
$font-stack: "Helvetica", "Roboto", "Arial", sans-serif;

$breakpoint--s: 640px;
$breakpoint--m: 880px;

$color--primary: #AA5999;
$color--danger: #FF2222;
$color--warning: #FFEE55;
$color--success: #33FF88;

.btn {
  width: 50%;
  margin: 0 auto;
  font: 100% $font-stack;
  color: gray;

  @media screen and (max-width: $breakpoint--m) {
    width: 75%;
  }

  @media screen and (max-width: $breakpoint--s) {
    width: 100%;
  }

  &.btn--primary {
    color: $color--primary;
  }

  &.btn--danger {
    color: $color--danger;
  }

  &.btn--warning {
    color: $color--warning;
  }

  &.btn--success {
    color: $color--success;
  }
}
```

<a name="mixins"></a>
## Mixins

When you find yourself writing the same thing over and over again, you can
probably write a mixin for it.

In CSS, you would probably be writing something like this over and over

```css
.container {
  position: relative;
  top: 50%;
  -webkit-transform: translateY(-50%);
  -moz-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  transform: translateY(-50%);
}

.box {
  position: relative;
  top: 50%;
  -webkit-transform: translateY(-50%);
  -moz-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  transform: translateY(-50%);
}
```

with a mixin you can do this

```scss
@mixin vertically-align {
  position: relative;
  top: 50%;
  -webkit-transform: translateY(-50%);
  -moz-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  transform: translateY(-50%);
}

.container {
  @include vertically-align();
}

.box {
  @include vertically-align();
}
```

You can also pass in variables to a mixin.

```scss
$color--danger: #FF2222;
$color--success: #33FF88;

@mixin btn($color) {
  background: none;
  border-radius: 2px;
  border: 2px solid $color;
  color: $color;
}

.btn--danger {
  @include btn($color--danger);
}

.btn--success {
  @include btn($color--success);
}
```

If you don't know how many arguments to use for your mixin

```scss
@mixin transition($transition...) {
  -webkit-transition: $transition;
  -moz-transition: $transition;
  -o-transition: $transition;
  transition: $transition;
}

.box {
  @include transition(background 0.2s, color 0.2s, border 0.2s);
}
```

Or if you need a helper function

```scss
@function calculateRem($size) {
    $remSize: $size / 16px;
    @return #{$remSize}rem;
}

@mixin font-size($size) {
    font-size: $size;
    font-size: calculateRem($size);
}
```

Play around with mixins, they can become quite powerful.

<a name="extending"></a>
## Extending/Inheritance

With Sass, you have the ability to inherit or extend properties from another
selector.

```scss
.border {
  border: 1px solid grey;
}

.container {
  @extend .border;
  border-color: #CCCCCC;
}

.btn {
  @extend .border;
  border-color: #33FF88;
}
```

Now you can have subclasses for you classes :grin:.

<a name="import"></a>
## Import

If your stylesheets get to long, split them into partials and use imports. No
one likes maintaining a 500+ line style sheet.

```scss
// _reset.scss

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

// base.scss
@import 'reset';

body {
  width: 100%;
}
```

Remember that if you're extending a class, using a variable, or using a
mixin/function, that class, variable, or mixin should come before the usage.
Also, Sass is still cascading so earlier imports could possibly be overwritten
by later imports.
