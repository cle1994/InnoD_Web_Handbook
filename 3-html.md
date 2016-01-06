# HTML

**Quick Jump**

* [Elements](3-html.md#elements)
* [Tags](3-html.md#tags)
  * [Head/Body](3-html.md#tags-head)
  * [Meta](3-html.md#tags-meta)
  * [Link](3-html.md#tags-link)
  * [Many, many more...](3-html.md#tags-rest)
* [Attributes](3-html.md#attributes)
* [Coding Style](3-html.md#style)

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
thing. Pretty much the more meta tags, the better, but law of diminishing
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

And fonts, if you want to include nicer fonts. I recommend using
[Google Fonts](https://www.google.com/fonts) but you can include your own font
files if you want. Make sure you have the rights to them first.
```html
<link href='https://fonts.googleapis.com/css?family=Open+Sans' rel='stylesheet' type='text/css'>
```

<a name="tags-rest">
#### Oh so many more tags
