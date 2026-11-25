---
layout: ../layouts/Markdown.astro
title: About
description: Ceradoc — the seal of interoperable document information. Formerly Coridoc.
---

# About Ceradoc

**Ceradoc** is a hub-and-spoke document transformation library. Documents are
parsed into a canonical **CoreModel**, and every supported format talks to that
hub — never to another format directly. Add a new format, and it converts to
and from all the others for free.

## The name

**Ceradoc** = **Cera** + **Doc**:

- **Cera** — Latin for *wax*. For two thousand years a document's authority
  traveled under a seal pressed into wax: identity, integrity, origin —
  tamper-evident and permanent.
- **Doc** — *document*. The subject matter: semantically typed, faithful,
  interoperable documents.

Together: **the seal of interoperable document information**. Press the
canonical CoreModel into any format and the document arrives sealed —
faithful, verifiable, round-trip-intact.

## Formerly Coradoc, then Coridoc

The project was formerly named **Coradoc**, then **Coridoc**. It started at
[metanorma/coradoc](https://github.com/metanorma/coradoc). It is now **Ceradoc**
and lives at [github.com/ceradoc/ceradoc](https://github.com/ceradoc/ceradoc).
The legacy `coradoc*` gems on RubyGems are frozen; new work happens under the
`ceradoc*` names.

## The gem suite

| Gem | Role |
|-----------|---------------------------------------------|
| [ceradoc](https://rubygems.org/gems/ceradoc) | CoreModel hub |
| [ceradoc-adoc](https://rubygems.org/gems/ceradoc-adoc) | AsciiDoc front |
| [ceradoc-markdown](https://rubygems.org/gems/ceradoc-markdown) | Markdown front |
| [ceradoc-html](https://rubygems.org/gems/ceradoc-html) | HTML renderer |
| [ceradoc-docx](https://rubygems.org/gems/ceradoc-docx) | DOCX renderer |
| [ceradoc-mirror](https://rubygems.org/gems/ceradoc-mirror) | ProseMirror JSON model |

## Links

- Monorepo: [github.com/ceradoc/ceradoc](https://github.com/ceradoc/ceradoc)
- Documentation: [www.ceradoc.org/ceradoc/](https://www.ceradoc.org/ceradoc/)
- Gems: [rubygems.org/gems/ceradoc](https://rubygems.org/gems/ceradoc)
