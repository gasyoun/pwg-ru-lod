# pwg-ru-lod — dereferenceable target for `w3id.org/sanskrit-lexicon`

_Created: 19-07-2026 · Last updated: 19-07-2026_

This repository is the redirect target behind the permanent identifier namespace
[`https://w3id.org/sanskrit-lexicon/`](https://w3id.org/sanskrit-lexicon/), served
via GitHub Pages at [gasyoun.github.io/pwg-ru-lod](https://gasyoun.github.io/pwg-ru-lod/).

It exists so that the IRIs minted by the PWG→RU LOD generator actually resolve. It is
deliberately thin: the w3id layer decouples the permanent identifiers from any host,
so this target can be replaced later (a Cologne endpoint, a project domain, a triple
store) without a single IRI changing.

## What is published here

| File | What it is |
|---|---|
| [shapes.ttl](https://github.com/gasyoun/pwg-ru-lod/blob/main/shapes.ttl) | SHACL profile pinning the modelling contract for entries, senses, citations, attestations and sense relations |
| [index.html](https://github.com/gasyoun/pwg-ru-lod/blob/main/index.html) | Human-readable namespace index — sub-namespaces, IRI scheme, documentation links |

## What is deliberately NOT published here

- **Graph data** (entries, senses, citations). The PWG→RU translation store is at present
  entirely machine-produced; publishing sense definitions is gated on an editorial
  sense-approval pass. Until that gate clears, instance IRIs under `/repwg/entry/…`,
  `/repwg/sense/…` and siblings will not resolve to data. This is intentional, not an outage.
- **The VoID/DCAT descriptor.** The version in
  [csl-standards](https://github.com/gasyoun/csl-standards/blob/main/standards/pwg-ru-lod/void.ttl)
  is an explicit stub template with unfilled counts, license and DOI slots. Publishing it
  as-is would put false dataset metadata on the open web.
- **The `pwglex:` vocabulary document.** 53 terms are in active use across the graph
  (`pwglex:evidenceGrade`, `pwglex:renouStratum`, `pwglex:dcsBand`, …) but none are yet
  formally declared anywhere. Authoring that vocabulary is the next prerequisite for a
  real RDF release; until then `vocab#` does not resolve.

## IRI scheme

See [index.html](https://gasyoun.github.io/pwg-ru-lod/) for the full table, and
[LOD_GRAPH.md](https://github.com/gasyoun/SanskritLexicography/blob/master/RussianTranslation/LOD_GRAPH.md)
for the model it encodes.

Instances use slash IRIs and resolve by 303 with content negotiation
(`text/turtle` → `.ttl`, otherwise HTML). The hash form is reserved for the
`pwglex:` vocabulary document.

## Provenance

The namespace base is emitted by
[`export_lod.py`](https://github.com/gasyoun/SanskritLexicography/blob/master/RussianTranslation/src/export_lod.py)
(`DEFAULT_BASE`, overridable with `--base-iri`); nothing downstream hard-codes it.
Registration prepared under handoff H1319 with Opus 4.8 (`claude-opus-4-8`).

## Maintainer

Dr. Mārcis Gasūns — [ORCID 0000-0003-4513-884X](https://orcid.org/0000-0003-4513-884X) ·
GitHub [@gasyoun](https://github.com/gasyoun)

_Dr. Mārcis Gasūns_
