---
title: singularize
linktitle: singularize
description: Converts a word according to a set of common English singularization rules.
godocref:
date: 2017-02-01
publishdate: 2017-02-01
lastmod: 2017-02-01
categories: [functions]
tags: [strings,singular]
ns:
signature: ["singularize INPUT"]
workson: []
hugoversion:
relatedfuncs: []
deprecated: false
aliases: []
---

`singularize` converts a word according to a set of common English singularization rules.

`{{ "cats" | singularize }}` → "cat"

See also the `.Data.Singular` [taxonomy variable](/variables/taxonomy/) for singularizing taxonomy names.

