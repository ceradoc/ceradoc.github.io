---
layout: ../layouts/Markdown.astro
title: About
description: Coridoc — the heart of interoperable documents. Formerly Coradoc.
---

# About Coridoc

**Coridoc** is a hub-and-spoke document transformation library. Documents are
parsed into a canonical **CoreModel**, and every supported format talks to that
hub — never to another format directly. Add a new format, and it converts to
and from all the others for free.

## The name

**Coridoc** = **Cor** + **I** + **Doc**:

- **Cor** — Latin for *heart*. The CoreModel is the heart every document beats
  through.
- **I** — *interoperable*. Formats interoperate bidirectionally through the
  hub.
- **Doc** — *document*. The subject matter: semantically typed, faithful
  documents.

Together: **the heart of interoperable documents**.

## Formerly Coradoc

The project was formerly named **Coradoc** and lived at
[metanorma/coradoc](https://github.com/metanorma/coradoc). It is now **Coridoc**
and lives at [github.com/coridoc/coridoc](https://github.com/coridoc/coridoc).
The legacy `coradoc*` gems on RubyGems are frozen; new work happens under the
`coridoc*` names.

## The gem suite

| Gem | Role |
|-----------|---------------------------------------------|
| [coridoc](https://rubygems.org/gems/coridoc) | CoreModel hub |
| [coridoc-adoc](https://rubygems.org/gems/coridoc-adoc) | AsciiDoc front |
| [coridoc-markdown](https://rubygems.org/gems/coridoc-markdown) | Markdown front |
| [coridoc-html](https://rubygems.org/gems/coridoc-html) | HTML renderer |
| [coridoc-docx](https://rubygems.org/gems/coridoc-docx) | DOCX renderer |
| [coridoc-mirror](https://rubygems.org/gems/coridoc-mirror) | ProseMirror JSON model |

## Links

- Monorepo: [github.com/coridoc/coridoc](https://github.com/coridoc/coridoc)
- Documentation: [www.coridoc.org/coridoc/](https://www.coridoc.org/coridoc/)
- Gems: [rubygems.org/orgs/coridoc](https://rubygems.org/orgs/coridoc)
