# HTML

**Quick Jump**

* [Elements](3-html.md#elements)
* [Tags](3-html.md#tags)
  * [Head/Body](3-html.md#tags-head)
  * [Meta](3-html.md#tags-meta)
  * [Link](3-html.md#tags-link)
  * [Script](3-html.md#tags-script)
  * [Many, many more...](3-html.md#tags-rest)
* [Attributes](3-html.md#attributes)
* [Example](3-html.md#exampe)

## Introduction

HTML, or HyperText Markup Language, is the standard markup language used to
create web pages. If you want to do web dev, you're going to write HTML.

<a name="elements"></a>
## Elements

An **element** is a part of webpage. They define the semantic meaning of their
content. Elements include two matching tags and everything in between. It
contains at least one tag (we'll go more in depth later about tags). Elements
can contain images, text, other elements, or even nothing.

```html
<div class="outer-element">
  <p class="inner-element"></div>
  <p class="another-inner-element"></div>
</div>
```

Here we see an outer element with two paragraphs as inner elements.

<a name="tags"></a>
## Tags

Since HTML is written in plain text (you can write it in notepad if you want
but please don't), there needs to be a way for browsers to know how to
render/display contents; this is where tags come in. Every time something is
surrounded by `<{{ tag }}>`, browsers think there's special meaning to that text.
Most tags need to be closed `</{{ tag }}>`. Some tags are self closing.

```html
<em>I <strong>really</strong> like penguins</em>.
```

Here we have emphasized text with strong text in the middle.

### There's a crap ton of tags

I'll cover a few special ones and list as many as I know afterwards

<a name="tags-head"></a>
#### Head and Body Tags

The `head` tag contains all the metadata (or information about the page/doc).
This includes the title tag, the various meta tags (see below), links to
stylesheets, and sometimes* scripts or script imports. Anything that you want
to show should not be in the `<head></head>` tag.

The `body` tag is where pretty much everything else goes.

*I say sometimes scripts because they can all be set in the `<head>` but that
could drastically slow down page load times so scripts tags are sometimes moved
to the bottom of the body. Some scripts must be in the head though. Angular,
for example should probably be loaded in the `<head>` before the body for
cleanest application launch.*

<a name="tags-meta">
#### Meta Tags

Meta data is data that is used to describe the data, or page/website/doc. Search
engines, such as Google, use meta tags to index your website and display
useful information in search results. Facebook and Pinterest use open graph
meta tags to get cool previews when you link something, Twitter has their own
thing. Pretty much the more meta tags, the better, but apply the law of diminishing
returns. Don't go crazy. I'm going to list the ones I use below.

You must include `title`
```html
<title>Page Title</title>
```

Tell the browser your HTML file is using the UTF-8 character set.
```html
<meta charset="UTF-8">
```

This if for IE8/9 support if you need it.
```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

Use the following to control layout on different size screen and responsive
 design.
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

A description of the webpage
```html
<meta name="description" content="">
```

Keywords about your webpage (think of these as hashtags)
```html
<meta name="keywords" content="">
```

The author of the webpage (probably you)
```html
<meta name="author" content="">
```

Name/title of your webpage
```html
<meta itemprop="name" content="">
```

A description of the webpage
```html
<meta itemprop="description" content="" />
```

A image for the webpage
```html
<meta itemprop="image" content="" />
```

###### Facebook/Open Graph meta tags

The pages title
```html
<meta property="og:title" content="">
```

Your website's name
```html
<meta property="og:site_name" content="">
```

The url of the webpage (link)
```html
<meta property="og:url" content="">
```

The description of the webpage
```html
<meta property="og:description" content="">
```

Type of webpage (article, website, product, etc.)
[Link to all of them](http://ogp.me/#types)
```html
<meta property="og:type" content="">
```

###### Twitter meta tags

A summary of the contents your webpage
```html
<meta name="twiiter:card" content="">
```

Your Twitter handle
```html
<meta name="twiiter:site" content="">
```

Title of your webpage
```html
<meta name="twiiter:title" content="">
```

Description of the your webpage
```html
<meta name="twiiter:description" content="">
```

Image for your webpage
```html
<meta name="twiiter:image:src" content="">
```

<a name="tags-link">
#### Link Tags

Link tags allow you to reference an external resource to include in your
document. This can be fonts, icons, stylesheets, etc. Here are a few that I
usually include.

These are icons for variable devices
```html
<link rel="apple-touch-icon" sizes="57x57" href="/favicon/apple-icon-57x57.png">
<link rel="apple-touch-icon" sizes="60x60" href="/favicon/apple-icon-60x60.png">
<link rel="apple-touch-icon" sizes="72x72" href="/favicon/apple-icon-72x72.png">
<link rel="apple-touch-icon" sizes="76x76" href="/favicon/apple-icon-76x76.png">
<link rel="apple-touch-icon" sizes="114x114" href="/favicon/apple-icon-114x114.png">
<link rel="apple-touch-icon" sizes="120x120" href="/favicon/apple-icon-120x120.png">
<link rel="apple-touch-icon" sizes="144x144" href="/favicon/apple-icon-144x144.png">
<link rel="apple-touch-icon" sizes="152x152" href="/favicon/apple-icon-152x152.png">
<link rel="apple-touch-icon" sizes="180x180" href="/favicon/apple-icon-180x180.png">
<link rel="icon" type="image/png" sizes="192x192"  href="/favicon/android-icon-192x192.png">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="96x96" href="/favicon/favicon-96x96.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon/favicon-16x16.png">
```

For stylesheets (css files), you can include more than one. Remember they are
cascading so later links will override previous ones.
```html
<link rel="stylesheet" type="text/css" href="style.css">
```

If you want to include nicer fonts, I recommend using
[Google Fonts](https://www.google.com/fonts) but you can include your own font
files if you want. Make sure you have the rights to them first.
```html
<link href='https://fonts.googleapis.com/css?family=Open+Sans' rel='stylesheet' type='text/css'>
```

<a name="tags-script">
#### Your script tags
Script tags are used to define a client-side scripts, probably Javascript stuff.
Scripts can be included in the `<head></head>` or in the `<body></body`. It's
generally preferred to have them at the end of your body for faster page loads.


You can either write Javascript in your HTML (but I recommend against it)...

```html
<script>
document.getElementById("app").innerHTML = "Hello World";
</script>
```

...or you can include an external script file (libraries, frameworks, or your own
scripts).

```html
<script src="app.js"></script>
```

<a name="tags-rest">
#### Many, many more tags

Even though you can do pretty much everything with a `<div>` and just style it
with CSS, it's good to know when to use certain tags. For example, heading tags
`<h1>`, `<h2>`, etc. should be used for headings so that that screen readers
know what the difference between text is for accessibility users.

Here's a list of tags I run into and use most often. They're linked to their
respective documentation.

*For more tags and their usage, check out Mozilla's HTML documentation
[here](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)*

* [a](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)
* [article](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/article)
* [blockquote](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote)
* [button](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button)
* [code](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/code)
* [div](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div)
* [fieldset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset)
* [footer](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/footer)
* [form](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)
* [h1-h6](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset)
* [header](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements)
* [img](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img)
* [input](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
  * [button](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
  * [checkbox](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
  * [radio](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
* [label](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label)
* [nav](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/nav)
* [ol](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ol)
  * [li](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/li)
* [p](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p)
* [pre](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/pre)
* [section](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/section)
* [select](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select)
  * [option](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/option)
* [span](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/span)
* [strike](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/strike)
* [strong](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/strong)
* [summary](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/summary)
* [table](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table)
  * [thead](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/thead)
  * [tbody](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tbody)
  * [tfoot](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tfoot)
  * [tr](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tr)
    * [th](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/th)
    * [td](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/td)
* [textarea](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea)
* [ul](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ul)
  * [li](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/li)
* [video](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)

Keep in mind that not all tags are compatible with older browsers. Some tags are
HTML5 and up only.

<a name="attributes">
## Attributes

Elements have attributes that add values or configurations to their behavior.
Below you'll find some common elements and widely used attributes.

*Check [here](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes) for
a comprehensive reference to all attributes and their related elements.*

```html
<div class=""></div>
```
`class` is a global attribute that can be used with any element. It's used with
CSS to style common elements.

```html
<div id=""></div>
```
`id` is also a global attribute that is used to identify/select specific
elements. The `id` value must be unique on the page.

```html
<a href=""></a>
```
`href` is used to specify the url or location for a link.

```html
<input name="" />
```
`name` is used by the server to identify fields on form submit

```html
<input placeholder="" />
```
`placeholder` providers hints for `input`, `textarea`

```html
<input required />
```
`required` makes an `input`, `select`, `textarea` required

```html
<input type="" />
```
`type` defines the type for the element. Common types for input are `radio`,
`email`, `password`, `number`, `button`, `checkbox`.

```html
<img src="" />
```
`src` is the url for the embedded content

```html
<div title />
```
`title` is a global attribute that is used to display text in the tooltip on
hover

<a name="example">
## Example

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <title>Hello World</title>

    <link rel="apple-touch-icon" sizes="57x57" href="/favicon/apple-icon-57x57.png">
    <link rel="apple-touch-icon" sizes="60x60" href="/favicon/apple-icon-60x60.png">
    <link rel="apple-touch-icon" sizes="72x72" href="/favicon/apple-icon-72x72.png">
    <link rel="apple-touch-icon" sizes="76x76" href="/favicon/apple-icon-76x76.png">
    <link rel="apple-touch-icon" sizes="114x114" href="/favicon/apple-icon-114x114.png">
    <link rel="apple-touch-icon" sizes="120x120" href="/favicon/apple-icon-120x120.png">
    <link rel="apple-touch-icon" sizes="144x144" href="/favicon/apple-icon-144x144.png">
    <link rel="apple-touch-icon" sizes="152x152" href="/favicon/apple-icon-152x152.png">
    <link rel="apple-touch-icon" sizes="180x180" href="/favicon/apple-icon-180x180.png">
    <link rel="icon" type="image/png" sizes="192x192"  href="/favicon/android-icon-192x192.png">
    <link rel="icon" type="image/png" sizes="32x32" href="/favicon/favicon-32x32.png">
    <link rel="icon" type="image/png" sizes="96x96" href="/favicon/favicon-96x96.png">
    <link rel="icon" type="image/png" sizes="16x16" href="/favicon/favicon-16x16.png">
    <meta name="msapplication-TileColor" content="#ffffff">
    <meta name="msapplication-TileImage" content="/favicon/ms-icon-144x144.png">
    <meta name="theme-color" content="#ffffff">

    <link href='https://fonts.googleapis.com/css?family=Merriweather:400,300,700' rel='stylesheet' type='text/css'>
    <link rel="stylesheet" type="text/css" href="/static/style.css">
  </head>
  <body>
    <div id="app">
      <div class="img-wrapper">
        <img src="http://goo.gl/ZqZXk6" />
      </div>
      <div class="img-wrapper">
        <img src="http://goo.gl/ZqZXk6" />
      </div>
      <div class="img-wrapper">
        <img src="http://goo.gl/ZqZXk6" />
      </div>
    </div>
    <article class="blurb">
      <header>
        <h2>
          Hello World
        </h2>
      </header>
      <section class="summary">
        <p>
          Blurbs are fun
        </p>
      </section>
      <section class="words">
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer
          semper massa in viverra consequat. Maecenas tempor luctus turpis, id
          vehicula.
        </p>
      </section>
      <footer>
        <p>
          Posted on <time datetime="2015-05-15 19:00">May 15</time>.
        </p>
      </footer>
    </article>
    <form action="/url" method="post">
      <label for="name">Name:</label>
      <input id="name" type="text">

      <label for="email">Email:</label>
      <input id="email" type="email">

      <input type="submit" value="Save">
    </form>
    <script src="/static/bundle.js"></script>
  </body>
</html>

```
