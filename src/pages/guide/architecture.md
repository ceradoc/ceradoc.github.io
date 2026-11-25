---
layout: ../../layouts/Markdown.astro
title: Hub-and-spoke architecture
description: How Ceradoc routes every conversion through the canonical CoreModel with bidirectional ToCoreModel/FromCoreModel transformers.
---

# Hub-and-spoke architecture

Ceradoc is a **hub-and-spoke** library. Every format is a spoke; the canonical
**CoreModel** is the hub. Documents never translate spoke-to-spoke — they
always pass through the hub.

## The transformation flow

```
Source text → Parser → Format model → ToCoreModel → CoreModel
                                                       │
Target text ← Serializer ← Target model ← FromCoreModel
```

- **Parse** — a format-specific parser (a PARG grammar for AsciiDoc and
  Markdown) reads source text into that format's own model.
- **ToCoreModel** — a transformer maps the format model into the canonical
  CoreModel.
- **FromCoreModel** — a transformer rebuilds a target format model from the
  CoreModel.
- **Serialize** — a serializer writes the target model back out as text.

Because both directions exist for every format, conversion is **bidirectional**:
`asciidoc → CoreModel → markdown` and `markdown → CoreModel → asciidoc` are the
same machinery in different order.

## The CoreModel

The CoreModel is the canonical document representation: structural elements,
blocks, lists, tables, images, inline content, metadata, footnotes and
bibliography. It is strongly typed — every attribute is a typed model, and no
format-specific concepts leak into the hub.

## The spokes

| Gem | Role |
|--------------------|--------------------------------------------|
| [ceradoc](https://rubygems.org/gems/ceradoc) | CoreModel hub |
| [ceradoc-adoc](https://rubygems.org/gems/ceradoc-adoc) | AsciiDoc front (parser + model + serializer + transformers) |
| [ceradoc-markdown](https://rubygems.org/gems/ceradoc-markdown) | Markdown front |
| [ceradoc-html](https://rubygems.org/gems/ceradoc-html) | HTML renderer |
| [ceradoc-docx](https://rubygems.org/gems/ceradoc-docx) | DOCX renderer |
| [ceradoc-mirror](https://rubygems.org/gems/ceradoc-mirror) | ProseMirror-compatible JSON document model |

## Adding a format

A new format is a new spoke: implement a parser with a **ToCoreModel**
transformer (ingress) and a model with a **FromCoreModel** transformer plus a
serializer (egress), then register it with the hub. No existing spoke changes —
once registered, the new format converts to and from every other format.

See [getting started](/guide/getting-started) to try it from the command line.
