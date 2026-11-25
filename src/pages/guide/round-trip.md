---
layout: ../../layouts/Markdown.astro
title: The round-trip guarantee
description: What "sealed" means — idempotence, the corpus, and the shrinking catalogue.
---

# The round-trip guarantee

"Sealed" is not a metaphor without receipts. Ceradoc pins its fidelity with
a property harness that runs on every change.

## The properties

1. **Idempotence** — serializing the re-parse of a serialization reproduces
   it byte-for-byte. A document that has been through the hub once is a
   fixed point.
2. **Catalogued divergence** — every case the harness cannot yet hold is
   listed in `known_failures.yml` with a reason. The list may only shrink:
   a catalogued case that starts passing must have its entry removed, and
   an uncatalogued failure fails the suite.

## The corpus

The harness runs fixtures, generated edge cases, and a standing real-world
corpus — currently the full ISO 14911 *Rice* standard document set from
`mn-samples-iso`: forty-six files across body sections, annexes,
bibliography and translations.

## How to read a failure

The checker reports a stage (`parse`, `model`, `canonical`, `timeout`), a
JSON-path to the first differing node, and both snippets. A `model`-stage
failure means the CoreModel itself changed across the round trip; a
`canonical` failure means serialization is not a fixed point.

## Sealing rules

- Constructs the model cannot seal are **rejected loudly** (an explicit
  error), never silently rewritten into prose.
- Document attributes, authored IDs, include edges and emphasis constraint
  are carried by the CoreModel as first-class typed slots.
- When a guarantee cannot hold for a construct, the guarantee is stated as
  an envelope in the documentation instead of being implied.
