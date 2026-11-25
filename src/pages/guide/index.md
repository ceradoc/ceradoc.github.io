---
layout: ../../layouts/Markdown.astro
title: Documentation
description: Guides for parsing, building, rendering and trusting Ceradoc.
---

# Documentation

Ceradoc turns documents into a canonical CoreModel and presses that model
into any supported format. Start here:

1. **[Getting started](/guide/getting-started)** — install the gems, parse a
   document, press it into another format.
2. **[Architecture](/guide/architecture)** — hub and spokes, compiled
   grammars, and the bidirectional translation pairs.
3. **[The round-trip guarantee](/guide/round-trip)** — what "sealed" means:
   idempotence, the corpus, and the shrinking divergence catalogue.

## The gems

| Gem | Role |
| --- | --- |
| `ceradoc` | CoreModel hub — the canonical model |
| `ceradoc-adoc` | AsciiDoc front-end |
| `ceradoc-markdown` | Markdown front-end |
| `ceradoc-html` | HTML renderer |
| `ceradoc-docx` | DOCX renderer |
| `ceradoc-mirror` | ProseMirror-compatible JSON |

Full API documentation lives at
[www.ceradoc.org/ceradoc/](https://www.ceradoc.org/ceradoc/); sources at
[github.com/ceradoc/ceradoc](https://github.com/ceradoc/ceradoc).
