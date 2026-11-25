---
layout: ../../layouts/Markdown.astro
title: Architecture
description: Hub and spokes, compiled grammars, and the bidirectional translation pairs.
---

# Architecture

Ceradoc is a hub-and-spoke library. Everything routes through the CoreModel;
nothing talks from format to format directly.

## The three stages

1. **Serialization syntax** — the grammar of each format lives in a single
   `.parg` source, compiled by [parsanol](https://rubygems.org/gems/parsanol)
   into a sealed artifact. The grammar source is the only source of truth.
2. **Serialization model** — each format has its own typed model classes
   (AsciiDoc's document model, Markdown's document model), generated and
   checked against the grammar.
3. **The CoreModel** — the harmonized hub. Every format translates into it
   on the way in and out of it on the way back.

## Bidirectional pairs

Each front-end ships two transformers that are equally load-bearing:

- `ToCoreModel` — parse direction: format model to CoreModel.
- `FromCoreModel` — rebuild direction: CoreModel to format model.

One-aspect lossiness is not accepted as one-directionality: the CoreModel
carries what round trips need — authored IDs, nested lists, include edges,
document attributes, emphasis constraint — so the rebuild is the document.

## Why compiled grammars

The parsers do not hand-walk text. Each `.parg` grammar compiles to a
checksum-sealed artifact and runs on a native engine, with a Ruby engine as
parity reference. Differential specs hold both engines to identical output,
and grammar-level parity specs cover a standing corpus.

## The harness

The round-trip property harness runs a real corpus — fixtures, generated
edge cases, and a full ISO standard document — on every change. It enforces
serialization idempotence and catalogues known divergences that may only
shrink. See [the round-trip guarantee](/guide/round-trip).

## Adding a format

A new format is two transformers (`ToCoreModel`, `FromCoreModel`), a grammar,
and a model set. No hub changes. That is the hub-and-spoke contract.
