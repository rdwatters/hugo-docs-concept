---
title: highlight
linktitle: highlight
description: Takes a string of code and language declaration and uses Pygments to return syntax-highlighted HTML with inline-styles.
godocref:
date: 2017-02-01
publishdate: 2017-02-01
lastmod: 2017-02-01
categories: [functions]
tags: [highlighting,pygments,code blocks,syntax]
ns:
signature: ["highlight INPUT"]
workson: []
hugoversion:
relatedfuncs: []
deprecated: false
---

`highlight` takes a string of code and a language and then uses Pygments to return the syntax highlighted code in HTML.

[`highlight` is used in Hugo's built-in `highlight` shortcode][highlight].

See [Installing Hugo][installpygments] for more information on Pygments or [Syntax Highlighting][syntax] for more options on how to add syntax highlighting to your code blocks with Hugo.


[highlight]: /content-management/shortcodes/#highlight
[installpygments]: /getting-started/installing/#installing-pygments-optional
[syntax]: /tools/syntax-highlighting/
