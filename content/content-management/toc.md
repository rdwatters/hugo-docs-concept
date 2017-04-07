---
title: Table of Contents
linktitle:
description: Hugo can automatically parse Markdown content and create a Table of Contents you can leverage in your templates to guide readers to sections of longer pages.
date: 2017-02-01
publishdate: 2017-02-01
lastmod: 2017-02-01
categories: [content management]
tags: [table of contents, toc]
menu:
  main:
    parent: "Content Management"
    weight: 130
weight: 130	#rem
draft: false
aliases: [/extras/toc/,/content-management/toc/]
toc: false
---

Hugo can automatically parse Markdown content and create a Table of Contents you can leverage in your templates to guide readers to sections of longer pages.

{{% note "TOC Heading Levels are Fixed" %}}
Currently, the `{{.TableOfContents}}` [page variable](/variables/page/) does not allow you to specify which heading levels you want the TOC to render. [See the related GitHub discussion (#1778)](https://github.com/spf13/hugo/issues/1778). As such, the resulting `<nav id="TableOfContents"><ul></ul></nav>` is going to start at `<h1>` when pulling from `{{.Content}}`.
{{% /note %}}

## Usage

Create your markdown the way you normally would with the appropriate headings. Here is some example content:

```md
<!-- Your front matter up here -->

## Introduction

One morning, when Gregor Samsa woke from troubled dreams, he found himself transformed in his bed into a horrible vermin.

## My Heading

He lay on his armour-like back, and if he lifted his head a little he could see his brown belly, slightly domed and divided by arches into stiff sections. The bedding was hardly able to cover it and seemed ready to slide off any moment.

His many legs, pitifully thin compared with the size of the rest of him, waved about helplessly as he looked. "What's happened to me? " he thought. It wasn't a dream. His room, a proper human room although a little too small, lay peacefully between its four familiar walls.

### My Subheading

A collection of textile samples lay spread out on the table - Samsa was a travelling salesman - and above it there hung a picture that he had recently cut out of an illustrated magazine and housed in a nice, gilded frame. It showed a lady fitted out with a fur hat and fur boa who sat upright, raising a heavy fur muff that covered the whole of her lower arm towards the viewer. Gregor then turned to look out the window at the dull weather. Drops
```

Hugo will take this Markdown and create a table of contents from `## Introduction`, `## My Heading`, and `### My Subheading` and then store it in the [page variable][pagevars]`.TableOfContents`.

## Template Example: Basic TOC

The following is an example of a very basic [single page template][]:

{{% code file="layout/_default/single.html" download="single.html" %}}
```html
{{ define "main" }}
<main id="main">
    <header>
        <h1>{{ .Title }}</h1>
    </header>
        {{ .Content }}
    <aside id="toc">
        {{ .TableOfContents }}
    </aside>
</main>
{{ end }}
```
{{% /code %}}

## Template Example: TOC Partial

The following is a [partial template][partials] that adds slightly more logic for page-level control over your table of contents. It assumes you are using a `toc` field in your content's [front matter][] that, unless specifically set to `false`, will add a TOC to any page with a [`.WordCount`][] greater than 400. This example also demonstrates how to use [conditionals][] in your templating:

{{% code file="layouts/partials/toc.html" download="toc.html" %}}
```html
{{ if and (gt .WordCount 400 ) (ne .Params.toc "false") }}
<aside id="toc">
    <header>
    <h2 class="toc-heading">{{.Title}}</h2>
    </header>
    {{.TableOfContents}}
</aside>
{{ end }}
```
{{% /code %}}

{{% note %}}
With the preceding example, even pages with > 400 words *and* `toc` not set to false will not render a table of contents if there are no headings in the page for the `{{.TableOfContents}}` variable to pull from.
{{% /note %}}

[conditionals]: /templates/introduction/#conditionals/
[front matter]: /content-management/table-of-contents/
[pagevars]: /variables/page/
[partials]: /templates/partials/
[single page template]: /templates/single-page-templates/