---
layout: ../../layouts/Markdown.astro
title: Getting started
description: Install the ceradoc gems, parse a document into the CoreModel, and press it into another format.
---

# Getting started

Ceradoc ships as small gems around one hub. The parser gems read documents
into the CoreModel; the renderer gems press the CoreModel back out.

## Install

```sh
gem install ceradoc-adoc      # AsciiDoc front-end
gem install ceradoc-markdown  # Markdown front-end
gem install ceradoc-html      # HTML renderer
gem install ceradoc-docx      # DOCX renderer
```

The `ceradoc` gem itself carries the CoreModel and arrives as a dependency.

## Parse into the CoreModel

```ruby
require "ceradoc"
require "ceradoc/adoc"

core = Ceradoc.parse_file("document.adoc", format: :asciidoc)
```

The CoreModel is a typed tree: sections, blocks, inline elements, metadata —
every construct a real object, not a hash bag. What the parser cannot seal,
it rejects loudly.

## Inspect

```ruby
core.children.each do |node|
  puts "#{node.class.name}: #{node.respond_to?(:title) ? node.title : node.flat_text[0, 60]}"
end
```

## Press into another format

```ruby
html = Ceradoc.serialize(core, to: :html)  # requires ceradoc-html
adoc = Ceradoc.serialize(core, to: :asciidoc)
```

Or from the command line:

```sh
ceradoc convert document.adoc -t html
ceradoc convert document.adoc -t adoc   # byte-stable round trip
```

## What you get back

The document arrives sealed: headings and authored IDs keep their names,
links and emphasis keep their structure, and the round trip through the
CoreModel is held byte-stable by the property harness. See
[the round-trip guarantee](/guide/round-trip) for what that means and how it
is enforced.
