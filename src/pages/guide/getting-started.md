---
layout: ../../layouts/Markdown.astro
title: Getting started
description: Install the Ceradoc gems and parse your first document into the CoreModel.
---

# Getting started

Ceradoc turns documents into a canonical **CoreModel** and back. This guide
walks through installing the gems and running your first conversion.

## Install

The hub gem is pulled in automatically by the fronts and renderers. To work
with AsciiDoc:

```console
$ gem install ceradoc-adoc
```

To also render HTML and DOCX:

```console
$ gem install ceradoc-html ceradoc-docx
```

## Parse a document into the CoreModel

The `ceradoc` CLI parses a source document into the canonical CoreModel:

```console
$ ceradoc parse document.adoc --to core
```

This produces the harmonized CoreModel representation of the document —
sections, blocks, tables, lists, inline content, metadata — independent of the
source format.

## Render to another format

Once a document is in the CoreModel, any registered renderer can consume it:

```console
$ ceradoc render document.adoc --to html
```

## Using the library from Ruby

End-to-end conversion routes through the hub:

```ruby
require "ceradoc"

core = Ceradoc.parse(text, format: :asciidoc)  # source -> CoreModel
html = Ceradoc.serialize(core, to: :html)      # CoreModel -> target
```

## What next?

- [Hub-and-spoke architecture](/guide/architecture) — how parse → CoreModel →
  render works, and what bidirectional ToCoreModel/FromCoreModel transformers
  do.
- [About Ceradoc](/about) — the name, the rename history, and the gem suite.
