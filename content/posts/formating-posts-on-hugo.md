---
author: ["Chris Achinga"]
title: "Formating Posts on a Hugo Site"
date: "2025-05-21"
description: "Hugo makes it easier to have whatever i have in my head on text, well on markdown. this is my go-to documentation for that"
tags: ["markdown", "technical writing", "hugo"]
ShowToc: true
---


this is my go to documentation for editing posts on this hugo site. it still uses markdown, but with some touch of style here and there.

## Article frontmatter:

>Use front matter to add metadata to your content.

https://gohugo.io/content-management/front-matter/


```md
---
author: ["Hugo Authors", "PaperMod Contributors", "Aditya Telange"]
title: "Comprehensive Frontmatter Example"
date: "2019-03-11"
description: "A comprehensive guide showcasing Markdown, shortcodes, syntax, and formatting for HTML elements."
summary: "Sample article demonstrating various frontmatter fields and their usage."
tags: ["markdown", "shortcodes", "privacy", "syntax", "code", "gist", "css", "html", "themes", "emoji"]
categories: ["themes", "syntax"]
series: ["Themes Guide"]
FAtags: ["markdown", "css", "html", "themes"]
FAcategories: ["themes", "syntax"]
FAseries: ["Themes Guide"]
aliases: ["migrate-from-jekyl"]
cover:
  image: images/msg.png
  caption: "Generated using [OG Image Playground by Vercel](https://og-playground.vercel.app/)"
social:
  fediverse_creator: "@adityatelange@mastodon.social"
math: true
weight: 2
ShowToc: true
TocOpen: true
ShowBreadCrumbs: false
---
```

## Inline Code

`This is Inline Code`

### Only `pre`

<pre>
This is pre text
</pre>

### Code block with backticks

```{hl_lines=[2,8]}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Example HTML5 Document</title>
    <meta
      name="description"
      content="Sample article showcasing basic Markdown syntax and formatting for HTML elements."
    />
  </head>
  <body>
    <p>Test</p>
  </body>
</html>
```

### Code block with backticks and language specified

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Example HTML5 Document</title>
    <meta
      name="description"
      content="Sample article showcasing basic Markdown syntax and formatting for HTML elements."
    />
  </head>
  <body>
    <p>Test</p>
  </body>
</html>
```

### Code block with backticks and language specified with line numbers

```html {linenos=true}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Example HTML5 Document</title>
    <meta
      name="description"
      content="Sample article showcasing basic Markdown syntax and formatting for HTML elements."
    />
  </head>
  <body>
    <p>Test</p>
  </body>
</html>
```

### Code block with line numbers and <mark>highlighted</mark> lines

- PaperMod supports `linenos=true` or `linenos=table`

```html {linenos=true,hl_lines=[2,8]}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Example HTML5 Document</title>
    <meta
      name="description"
      content="Sample article showcasing basic Markdown syntax and formatting for HTML elements."
    />
  </head>
  <body>
    <p>Test</p>
  </body>
</html>
```

- <del>With `linenos=inline` line <mark>**might not** get highlighted</mark> properly.<del>
- This issue is fixed with [045c084](https://github.com/adityatelange/hugo-PaperMod/commit/045c08496d61b1b3f9c79e69e7d3d243a526d8f3)

```html {linenos=inline,hl_lines=[2,8]}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Example HTML5 Document</title>
    <meta
      name="description"
      content="Sample article showcasing basic Markdown syntax and formatting for HTML elements."
    />
  </head>
  <body>
    <p>Test</p>
  </body>
</html>
```

### Code block indented with four spaces

    <!doctype html>
    <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>Example HTML5 Document</title>
    </head>
    <body>
      <p>Test</p>
    </body>
    </html>

### Code block with Hugo's internal highlight shortcode

{{< highlight html >}}

<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
</html>
{{< /highlight >}}

### Github Gist

https://gohugo.io/shortcodes/gist/

```markdown
{{< gist user 23932424365401ffa5e9d9810102a477 >}}
```

To display a specific file within the gist:

```markdown
{{< gist user 23932424365401ffa5e9d9810102a477 list.html >}}
```
### Emoji

Emoji can be enabled in a Hugo project in a number of ways.

<!--more-->

The [`emojify`](https://gohugo.io/functions/emojify/) function can be called directly in templates or [Inline Shortcodes](https://gohugo.io/templates/shortcode-templates/#inline-shortcodes).

To enable emoji globally, set `enableEmoji` to `true` in your site's [configuration](https://gohugo.io/getting-started/configuration/) and then you can type emoji shorthand codes directly in content files; e.g.

<p><span class="nowrap"><span class="emojify">🙈</span> <code>:see_no_evil:</code></span>  <span class="nowrap"><span class="emojify">🙉</span> <code>:hear_no_evil:</code></span>  <span class="nowrap"><span class="emojify">🙊</span> <code>:speak_no_evil:</code></span></p>
<br>

The [Emoji cheat sheet](http://www.emoji-cheat-sheet.com/) is a useful reference for emoji shorthand codes.

---

**N.B.** The above steps enable Unicode Standard emoji characters and sequences in Hugo, however the rendering of these glyphs depends on the browser and the platform. To style the emoji you can either use a third party emoji font or a font stack; e.g.

{{< highlight html >}}
.emoji {
font-family: Apple Color Emoji, Segoe UI Emoji, NotoColorEmoji, Segoe UI Symbol, Android Emoji, EmojiSymbols;
}
{{< /highlight >}}

{{< css.inline >}}

<style>
.emojify {
	font-family: Apple Color Emoji, Segoe UI Emoji, NotoColorEmoji, Segoe UI Symbol, Android Emoji, EmojiSymbols;
	font-size: 2rem;
	vertical-align: middle;
}
@media screen and (max-width:650px) {
  .nowrap {
    display: block;
    margin: 25px 0;
  }
}
</style>

{{< /css.inline >}}


This article offers a sample of basic Markdown syntax that can be used in Hugo content files, also it shows whether basic HTML elements are decorated with CSS in a Hugo theme.


## Headings

The following HTML `<h1>`—`<h6>` elements represent six levels of section headings. `<h1>` is the highest section level while `<h6>` is the lowest.

# H1

## H2

### H3

#### H4

##### H5

###### H6


```md
# H1

## H2

### H3

#### H4

##### H5

###### H6
```



## Paragraph

>just type stuff 

```md
Xerum, quo qui aut unt expliquam qui dolut labo. Aque venitatiusda cum, voluptionse latur sitiae dolessi aut parist aut dollo enim qui voluptate ma dolestendit peritin re plis aut quas inctum laceat est volestemque commosa as cus endigna tectur, 
offic to cor sequas etum rerum idem sintibus eiur? Quianimin porecus evelectur, cum que nis nust voloribus ratem aut omnimi, sitatur? Quiatem. Nam, omnis sum am facea corem alique molestrunt et eos evelece arcillit ut aut eos eos nus, sin conecerem erum fuga. 
Ri oditatquam, ad quibus unda veliamenimin cusam et facea ipsamus es exerum sitate dolores editium rerore eost, temped molorro ratiae volorro te reribus dolorer sperchicium faceata tiustia prat.

Itatur? Quiatae cullecum rem ent aut odis in re eossequodi nonsequ idebis ne sapicia is sinveli squiatum, core et que aut hariosam ex eat.
```

## Blockquotes

The blockquote element represents content that is quoted from another source, optionally with a citation which must be within a `footer` or `cite` element, and optionally with in-line changes such as annotations and abbreviations.

### Blockquote without attribution

> Tiam, ad mint andaepu dandae nostion secatur sequo quae.
> **Note** that you can use _Markdown syntax_ within a blockquote.

```md
> Tiam, ad mint andaepu dandae nostion secatur sequo quae.
> **Note** that you can use _Markdown syntax_ within a blockquote.
```

### Blockquote with attribution

> Don't communicate by sharing memory, share memory by communicating.
>
> — <cite>Rob Pike[^1]</cite>
[^1]: The above quote is excerpted from Rob Pike's [talk](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.


```md
> Don't communicate by sharing memory, share memory by communicating.
>
> — <cite>Rob Pike[^1]</cite>
[^1]: The above quote is excerpted from Rob Pike's [talk](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.
```


## Tables

Tables aren't part of the core Markdown spec, but Hugo supports them out-of-the-box.

| Name  | Age |
| ----- | --- |
| Bob   | 27  |
| Alice | 23  |

#### Inline Markdown within tables

| Italics   | Bold     | Code   |
| --------- | -------- | ------ |
| _italics_ | **bold** | `code` |


## List Types

#### Ordered List

1. First item
2. Second item
3. Third item

#### Unordered List

-   List item
-   Another item
-   And another item

#### Nested list

-   Fruit
    -   Apple
    -   Orange
    -   Banana
-   Dairy
    -   Milk
    -   Cheese

## Other Elements — abbr, sub, sup, kbd, mark

<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

H<sub>2</sub>O

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

Press <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> to end the session.

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.


Mathematical notation in a Hugo project can be enabled by using third party JavaScript libraries.

<!--more-->

In this example we will be using [KaTeX](https://katex.org/)

-   Create a partial under `/layouts/partials/math.html`
-   Within this partial reference the [Auto-render Extension](https://katex.org/docs/autorender.html) or host these scripts locally.
-   Include the partial in your templates ([`extend_head.html`](../papermod/papermod-faq/#custom-head--footer)) like so:
-   refer [ISSUE #236](https://github.com/adityatelange/hugo-PaperMod/issues/236)

```bash
{{ if or .Params.math .Site.Params.math }}
{{ partial "math.html" . }}
{{ end }}
```

-   To enable KaTex globally set the parameter `math` to `true` in a project's configuration
-   To enable KaTex on a per page basis include the parameter `math: true` in content files

**Note:** Use the online reference of [Supported TeX Functions](https://katex.org/docs/supported.html)

{{< math.inline >}}
{{ if or .Page.Params.math .Site.Params.math }}

<!-- KaTeX -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI" crossorigin="anonymous" onload="renderMathInElement(document.body);"></script>
{{ end }}
{{</ math.inline >}}

### Examples

{{< math.inline >}}

<p>
Inline math: \(\varphi = \dfrac{1+\sqrt5}{2}= 1.6180339887…\)
</p>
{{</ math.inline >}}

Block math:

$$
 \varphi = 1+\frac{1} {1+\frac{1} {1+\frac{1} {1+\cdots} } }
$$


## RIch content

Hugo ships with several [Built-in Shortcodes](https://gohugo.io/content-management/shortcodes/#use-hugos-built-in-shortcodes) for rich content, along with a [Privacy Config](https://gohugo.io/about/hugo-and-gdpr/) and a set of Simple Shortcodes that enable static and no-JS versions of various social media embeds.

<!--more-->

---

## Figure Shortcode ([PaperMod enhanced](https://github.com/adityatelange/hugo-PaperMod/commits/master/layouts/shortcodes/figure.html))

{{< figure src="https://images.unsplash.com/photo-1702382930514-9759f4ca5469" attr="Photo by [Aditya Telange](https://unsplash.com/@adityatelange?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash) on [Unsplash](https://unsplash.com/photos/Z0lL0okYjy0?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash)" align=center link="https://unsplash.com/photos/a-person-sitting-on-a-rock-wall-looking-out-at-the-ocean-Z0lL0okYjy0" target="_blank" >}}

---

## YouTube

{{< youtube hjD9jTi_DQ4 >}}

---

## X (Twitter) Shortcode

{{< x user="adityatelange" id="1724414854348357922" >}}

---

## Vimeo Shortcode


{{< vimeo 152985022 >}}
