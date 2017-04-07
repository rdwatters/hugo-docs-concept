---
title: md5
linktitle: md5
description: hashes the given input and returns its MD5 checksum.
godocref:
date: 2017-02-01
publishdate: 2017-02-01
lastmod: 2017-02-01
categories: [functions]
tags: []
ns:
signature: ["md5 INPUT"]
workson: []
hugoversion:
relatedfuncs: []
deprecated: false
aliases: []
---

The `md5` function hashes the given input and returns its MD5 checksum.

```html
{{ md5 "Hello world, gophers!" }}
<!-- returns the string "b3029f756f98f79e7f1b7f1d1f0dd53b" -->
```

This can be useful if you want to use [Gravatar](https://en.gravatar.com/) for generating a unique avatar:

```html
<img src="https://www.gravatar.com/avatar/{{ md5 "your@email.com" }}?s=100&d=identicon">
```
