---
layout: ../layouts/Markdown.astro
title: About
description: Ceradoc — the seal of interoperable document information. The name, the mark, the origin, and the ecosystem.
---

# About Ceradoc

**Ceradoc** is a hub-and-spoke document transformation library. Documents are
parsed into a canonical **CoreModel**, and every supported format talks to
that hub — never to another format directly. Add a new format, and it converts
to and from all the others for free.

## The name

**Ceradoc** = **Cera** + **Doc**:

- **Cera** — Latin for *wax*. For over two thousand years, a document's
  authority traveled under a seal pressed into wax. The seal proved identity,
  integrity and origin; it was tamper-evident; and it was permanent — it
  could not be quietly rewritten without showing.
- **Doc** — *document*. The subject matter: semantically typed, faithful,
  interoperable documents.

Together: **the seal of interoperable document information**. The canonical
CoreModel is the matrix — the engraved stamp — and every output format is a
press of that stamp into fresh wax. The document that arrives is the document
that was sealed.

## The mark

The Ceradoc seal is a scalloped wax disc in sealing-wax red, with an
engraved inner ring and the Cera monogram. The scalloped edge is not
decoration — it is how real wax takes the impression of the matrix, and no
two presses are exactly alike.

## The colors

The palette comes from the seal itself and the desk it rests on:

- **Sealing wax** (oxblood red) — the wax body, primary accent
- **Brass** — the matrix and handle, used for highlights
- **Patina** (verdigris green) — what aged brass earns; links and quiet
  accents
- **Parchment ink** — the light of the page itself
- **Umber night** — the warm, wax-dark canvas

## Origin story

Ceradoc solves a concrete problem: standards documents (ISO, IEC, CEN and
friends) are authored in AsciiDoc and Markdown, consumed as XML, HTML, DOCX
and JSON, and every lossy hop between those formats erodes the document.
Rather than pair every format with every other format, Ceradoc gives them
one hub: parse into the CoreModel, press out any format, and keep the
round trip byte-stable.

The project began as **Coradoc** in the Metanorma ecosystem, became
**Coridoc** (cor, Latin for *heart* — the CoreModel as the heart every
document beats through), and is now **Ceradoc**: the heart keeps the model
beating, and the seal is what makes its output trustworthy.

## Mission statement

Ceradoc's mission is **interoperable document information** that never has
to choose between fidelity and reach. A document should keep its identity,
integrity and structure no matter how many formats it passes through.

## The ecosystem

| Gem | Role | Layer |
| --- | --- | --- |
| [ceradoc](https://rubygems.org/gems/ceradoc) | CoreModel hub — the canonical model | Hub |
| [ceradoc-adoc](https://rubygems.org/gems/ceradoc-adoc) | AsciiDoc front, compiled PARG grammar | Front |
| [ceradoc-markdown](https://rubygems.org/gems/ceradoc-markdown) | Markdown front, compiled PARG grammar | Front |
| [ceradoc-html](https://rubygems.org/gems/ceradoc-html) | HTML renderer | Press |
| [ceradoc-docx](https://rubygems.org/gems/ceradoc-docx) | DOCX renderer (uniword) | Press |
| [ceradoc-mirror](https://rubygems.org/gems/ceradoc-mirror) | ProseMirror-compatible JSON model | Press |

Under the hub sit the machinery gems: [lutaml-model](https://rubygems.org/gems/lutaml-model)
for typed serialization, [parsanol](https://rubygems.org/gems/parsanol) for
the compiled grammar runtimes, [leptris](https://rubygems.org/gems/leptris)
for HTML processing and [uniword](https://rubygems.org/gems/uniword) for
OOXML.

## Use cases

- **Standards authoring** — author in AsciiDoc, deliver HTML, DOCX and XML
  from one source, without hand-maintaining each.
- **Document conversion** — move between AsciiDoc and Markdown without the
  usual flattening of links, emphasis and lists.
- **Tooling and review** — read any supported format into the CoreModel and
  build editors, linters and previews on one typed model.
- **Faithful archives** — seal a document today; the round-trip harness
  keeps re-opening it as itself.

## The fidelity envelope

Ceradoc states its guarantees explicitly. Round trips through the CoreModel
are held byte-stable by a property harness that runs a real corpus —
including a full ISO standard document — on every change. Constructs the
model cannot yet seal are rejected loudly, never silently rewritten. The
catalogue of open divergences lives in the monorepo's round-trip harness and
only ever shrinks.
