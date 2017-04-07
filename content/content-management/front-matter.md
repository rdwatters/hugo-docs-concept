---
title: Front Matter
linktitle:
description: Hugo allows you to add front matter in yaml, toml, or json to your content files.
date: 2017-01-09
publishdate: 2017-01-09
lastmod: 2017-02-24
categories: [content management]
tags: ["front matter", "yaml", "toml", "json", "metadata", "archetypes"]
menu:
  main:
    parent: "Content Management"
    weight: 30
weight: 30	#rem
draft: false
aliases: [/content/front-matter/]
toc: true
---

**Front matter** allows you to keep metadata attached to an instance of a [content type][]---i.e., embedded inside a content file---and is one of the many features that gives Hugo its strength.

## Front Matter Formats

Hugo supports three formats for front matter, each with their own identifying tokens.

TOML
: identified by opening and closing `+++`.

YAML
: identified by opening and closing `---` *or* opening `---` and closing `...`

JSON
: a single JSON object surrounded by '`{`' and '`}`', followed by a new line.

### TOML Example

```toml
+++
title = "spf13-vim 3.0 release and new website"
description = "spf13-vim is a cross platform distribution of vim plugins and resources for Vim."
tags = [ ".vimrc", "plugins", "spf13-vim", "vim" ]
date = "2012-04-06"
categories = [
  "Development",
  "VIM"
]
slug = "spf13-vim-3-0-release-and-new-website"
+++
```

### YAML Example

```yaml
---
title: "spf13-vim 3.0 release and new website"
description: "spf13-vim is a cross platform distribution of vim plugins and resources for Vim."
tags: [ ".vimrc", "plugins", "spf13-vim", "vim" ]
lastmod: 2015-12-23
date: "2012-04-06"
categories:
  - "Development"
  - "VIM"
slug: "spf13-vim-3-0-release-and-new-website"
---
```

### JSON Example

```json
{
    "title": "spf13-vim 3.0 release and new website",
    "description": "spf13-vim is a cross platform distribution of vim plugins and resources for Vim.",
    "tags": [ ".vimrc", "plugins", "spf13-vim", "vim" ],
    "date": "2012-04-06",
    "categories": [
        "Development",
        "VIM"
    ],
    "slug": "spf13-vim-3-0-release-and-new-website"
}
```

## Front Matter Variables

### Predefined

There are a few predefined variables that Hugo is aware of. See [Page Variables][pagevars] for how to call many of these predefined variables in your templates.

`aliases`
: an array of one or more aliases (e.g., old published paths of renamed content) that will be created in the output directory structure . See [Aliases][aliases] for details.

`date`
: the datetime at which the content was created; note this value is auto-populated according to Hugo's built-in [archetype][].

`description`
: the description for the content.

`draft`
: if `true`, the content will not be rendered unless the `--buildDrafts` flag is passed to the `hugo` command.

`expirydate`
: the datetime at which the content should no longer be published by Hugo; expired content will not be rendered unless the `--buildExpired` flag is passed to the `hugo` command.

`isCJKLanguage`
: if `true`, Hugo will explicitly treat the content as a CJK language; both `.Summary` and `.WordCount` work properly in CJK languages.

`keywords`
: the meta keywords for the content.

`layout`
: the layout Hugo should select from the [lookup order][] when rendering the content.

`lastmod`
: the datetime at which the content was last modified.

`linktitle`
: used for creating links to content; if set, Hugo defaults to using the `linktitle` before the `title`. Hugo can also [order lists of content by `linktitle`][bylinktitle].

`markup`
: **experimental**; specify `"rst"` for reStructuredText (requires`rst2html`) or `"md"` (default) for Markdown.

`publishdate`
: if in the future, content will not be rendered unless the `--buildFuture` flag is passed to `hugo`.

`slug`
: appears as the tail of the output URL. A value specified in front matter will override the segment of the URL based on the filename.

`taxonomies`
: these will use the field name of the plural form of the index; see the `tags` and `categories` in the above front matter examples.

`title`
: the title for the content.

`type`
: the type of the content; this value will be derived from the directory (i.e., the [section][]) automatically if unset.

`url`
: the full path to the content from the web root. It makes no assumptions about the path of the content file. It also ignores any language prefixes of
the multilingual feature.

`weight`
: used for [ordering your content in lists][ordering].

{{% note "Hugo's Default URL Destinations" %}}
If neither `slug` nor `url` is present and [permalinks are not configured otherwise](/content-management/urls/#permalinks), Hugo will use the filename of your content to create the output URL. See [Content Organization](/content-management/organization) for an explanation of paths in Hugo and [URL Management](/content-management/urls/) for ways to customize Hugo's default behaviors.
{{% /note %}}

### User-Defined

You can add fields to your front matter arbitrarily to meet your needs. These user-defined key-values are placed into a single `.Params` variable for use in your templates.

The following fields can be accessed via `.Params.include_toc` and `.Params.show_comments`, respectively. The [Variables][] section provides more information on using Hugo's page- and site-level variables in your templates.

```yaml
include_toc: true
show_comments: false
```

{{% note %}}
Field names are always normalized to lowercase; e.g., `camelCase: true` is available as `.Params.camelcase`.
{{% /note %}}

## Ordering Content Through Front Matter

You can assign content-specific `weight` in the front matter of your content. These values are especially useful for [ordering][ordering] in list views. You can use `weight` for ordering of content and the convention of [`<TAXONOMY>_weight`][taxweight] for ordering content within a taxonomy. See [Ordering and Grouping Hugo Lists][] to see how `weight` can be used to organize your content in list views.

## Overriding Global Blackfriday Configuration

It's possible to set some options for Markdown rendering in a content's front matter as an override to the [BlackFriday rendering options set in your project configuration][config].

## Front Matter Format Specs

* [TOML Spec][TOML Spec]
* [YAML Spec][YAML Spec]
* [JSON Spec][JSON Spec]

[aliases]: /content-management/urls/#aliases/
[archetype]: /content-management/archetypes/
[bylinktitle]: /templates/lists/#by-link-title
[config]: /getting-started/configuration/ "Hugo documentation for site configuration"
[content type]: /content-management/types/
[contentorg]: /content-management/organization/
[json]: /documents/ecma-404-json-spec.pdf "Specification for JSON, JavaScript Object Notation"
[lookup]: /content-management/l
[ordering]: /templates/lists/ "Hugo provides multiple ways to sort and order your content in list templates"
[pagevars]: /variables/page/
[section]: /content-management/sections/
[taxweight]: /content-management/taxonomies/
[toml]: https://github.com/toml-lang/toml "Specification for TOML, Tom's Obvious Minimal Language"
[urls]: /content-management/urls/
[variables]: /variables/
[yaml]: http://yaml.org/spec/ "Specification for YAML, YAML Ain't Markup Language"
