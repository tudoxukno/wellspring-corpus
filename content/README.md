# Content packages

Versioned, reviewable corpus data. Produced by `scripts/ingest/*`, never edited by hand. Each package is a folder under `content/<id>/`.

## Scripture package (`content/<translation>/`)

- `source.json` — the `Source` + `Translation` record (DOMAIN_MODEL.md): title, abbreviation, language, translator/edition/date, `rights` and `rightsNote`, per-tradition `canonicalStatus`, `provenance` (upstream URL, project, fetch date, sha256 of the upstream file, license text), `origin: primary`, feature flags.
- `index.json` — `{translation, books:[{osis, usfm, name, testament: ot|nt|apoc, title, short, chapters:[verseCount…]}]}`. This is the **versification grid**: canonical IDs are `psg:<translation>.<osis>.<chapter>.<verse>`, and parallel display aligns other translations to this grid by ID.
- `books/<osis>.json` — `{translation, osis, name, testament, title, chapters:[{n, title?, verses:[verse…]}]}`.

### Verse shape

```json
{"n":13, "text":"I saw in the night visions, …",
 "sp":{"w":[[2,5,"H1934"],[13,18,"H3916"]], "add":[[41,44]], "nd":[[4,8]], "wj":[[0,141]]},
 "notes":[[85,"1.4 the light from…: Heb. between the light and between the darkness"]],
 "q":1, "br":1, "heading":"…", "through":14}
```

- `text` is normalized plain text (single spaces, trimmed). **Offsets in `sp` and `notes` index into `text`** — highlight anchors, Word Study and Passage Guide key on them, so `text` must never be re-normalized downstream.
- `sp` spans by type, each `[start, end]` or `[start, end, strong]`: `w` tagged word (Strong's), `add` supplied words (KJV italics), `nd` divine name (LORD), `wj` words of Jesus, `tl` transliterated word.
- `notes` are translator footnotes anchored at an offset. `q` marks a poetry line, `br` a paragraph start, `heading` a section heading before the verse, `through` a verse range (e.g. 13–14 combined), `title` on a chapter is a psalm superscription.

## Rules

- A package enters only with `rights` and `provenance` recorded (ADR 012) and a config in `scripts/ingest/translations.mjs` whose rights are documented in `docs/CORPUS.md`.
- Re-running an ingest is deterministic for the same upstream file; `sha256` in `source.json` says which one.
- The app fetches `index.json` eagerly and `books/<osis>.json` lazily.
