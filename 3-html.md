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
<em>I <strong>really</strong> mean that</em>.
```

Here we have emphasized text with strong text in the middle.

#### There's a crap ton of tags

I'll cover a few special ones and list as many as I know afterwards

<a name="tags-head"></a>
#### Head and Body Tags
