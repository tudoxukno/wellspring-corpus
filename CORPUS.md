# Wellspring — corpus inventory and source families

Status: authoritative inventory. Adopted September 16, 2026. Rights notes are working assessments, **not legal advice**; every "verify" must be resolved before a text ships.

Rule: generated placeholder copy is never silently converted into research data. Anything flagged below stays flagged until replaced by a provenanced source or explicitly kept as a labeled research prompt.

## Part 1 — Current resources (as in `src/data/corpus.js`, 0.4.1)

### 1.1 Sources with text (10)

| ID | Work / range | Family | Language | Translation / edition | Provenance recorded | Full text | Rights | Status | Flags |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `genesis1` | Genesis 1:1–3 | Scripture | English | KJV | "public-domain English text" | 3 verses only | PD (UK Crown patent applies to printing in the UK) | Implemented | Excerpt only; edition (1769 Blayney vs 1611) not recorded |
| `psalm2` | Psalm 2:1–2 | Scripture | English | KJV | same | 2 verses | PD | Implemented | Excerpt; brief expects 2:1–12 |
| `isaiah9` | Isaiah 9:6–7 | Scripture | English | KJV | same | 2 verses | PD | Implemented | Excerpt |
| `isaiah61` | Isaiah 61:1–3 | Scripture | English | KJV | same | 3 verses | PD | Implemented | Excerpt |
| `daniel7` | Daniel 7:13–14 | Scripture | English | KJV | same | 2 verses | PD | Implemented | Excerpt |
| `james1` | James 1:2–4 | Scripture | English | KJV | same | 3 verses | PD | Implemented | Excerpt; text spot-checked against KJV |
| `enoch46` | 1 Enoch 46:1–6 | Extra-biblical | English | R.H. Charles (1917) via Internet Sacred Text Archive | recorded, with URL | 6 verses | PD | Implemented | Provenance contains an odd editorial note ("Verse 3 follows the text following the angel's reply") — **verify transcription against Charles 1917 and rewrite the note** |
| `enoch62` | 1 Enoch 62:6–9 | Extra-biblical | English | R.H. Charles (1917) via ISTA | recorded, with URL | 4 verses | PD | Implemented | — |
| `zulu` | "uMsindisi uyabuya" | Oral tradition | isiZulu / English | "English gloss supplied in product brief" | explicitly unverified | 1 line | n/a | Research prompt | **Placeholder / invented.** Originates as an illustrative line in the brief. No community, narrator, collector, date, or locality. Must not become research data. Options: replace with a documented entry, or keep only as a clearly labeled prompt. |
| `ethiopian` | "Ethiopian tradition: a comparative study" | Comparative | English | "Editorial research prompt" | explicitly unverified | 1 research question | n/a | Research prompt | **Placeholder.** No primary source. Also **misclassified**: Ethiopian Orthodox Tewahedo material belongs in the Christian-sources / Ge'ez-witness families, not a generic "comparative" bucket. |

Text-accuracy note: KJV excerpts and Charles excerpts were spot-checked, not systematically proofed. A full-text ingestion pass replaces these excerpts and should re-verify.

### 1.2 Catalog entries without text (9)

| Title | Family | Status | Flags |
| --- | --- | --- | --- |
| 2 Enoch | Extra-biblical | Awaiting text | Candidate edition: Morfill & Charles (1896) or Forbes & Charles in APOT (1913), both PD (verify). |
| 3 Enoch | Extra-biblical | Awaiting text | Odeberg (1928): PD in the US since 2024; **still in copyright in the UK/EU** (author d. 1973). Alexander (1983, OTP) is copyrighted. Decide jurisdiction before ingest. |
| Jubilees | Extra-biblical | Awaiting text | Charles (1902 / 1913 APOT), PD (verify). |
| Kebra Nagast | Extra-biblical | Awaiting text | Budge (1922), PD in US and UK (verify). Label as a translation from Ge'ez; record Budge's known limitations. |
| Xhosa Imbongo | Oral tradition | Awaiting text | **Questionable naming.** "Imbongi" is the praise poet; "izibongo" the praise poems. "Imbongo" appears to be a mockup label. No archive exists behind it. |
| Sotho Dithuto | Oral tradition | Awaiting text | Generic label ("teachings"). No archive behind it. |
| Yoruba Ifa Lore | Oral tradition | Awaiting text | Ifá is a living religious/divinatory system with its own literature (Odù). Requires careful sourcing and community-aware framing, not "lore". |
| Akan Anansi Tales | Oral tradition | Awaiting text | Genre label. Published collections (e.g., Rattray 1930) have varying rights; verify. |
| Shona Oral Tradition Entries | Oral tradition | Awaiting text | Generic label. |
| Ancient Egyptian / Nubian Tradition | Comparative | Awaiting text | Needs decomposition into concrete sources (texts, inscriptions, archaeology) — not one "tradition". |
| West African Traditional Systems | Comparative | Awaiting text | Same — decompose. |
| Zulu Indaba | Oral tradition | Has 1 placeholder entry | Generic label ("matter / gathering / account"). No archive behind it. |

Conclusion for the oral archive: **none of the six named archives exist as sources.** They are mockup labels. The product definition requires community-as-source records with full provenance (see `DOMAIN_MODEL.md` › TraditionEntry). These labels should be retired in favor of records named by community, collector, and date once real material exists.

### 1.3 Other data files that touch the corpus

- `src/data/literature-plan.js` — 98-resource registry (66 KJV books, the 14-work 1611 Apocrypha grouping, 5 additional books, 13 archive/tool entries). Planning only, no text. Retained as the KJV ingestion checklist; its `format` field is vestigial.
- Cover artwork and carousel copy files were removed September 17, 2026; covers and featured cards are now generated (`src/ui/cover.js`, `src/data/featured.js`).
- `seedNotes` in `corpus.js` — two demo notes with fixed dates. Demo user data; label as such in the seed spec and exclude from any real account.

### 1.4 Concepts (8 curated + 6,782 computed)

**Computed ontology (Sept 18, 2026)** — `content/concepts/` built by `scripts/ingest/concepts.mjs` (`npm run ingest:concepts`): 6,782 nodes from Nave’s and Torrey’s headings merged on slug (5,045 with verse lists) and Easton’s entries (4,055 definitions; 1,126 Easton-only nodes for people, places and things Nave’s does not head). Each node carries a lexical profile from the KJV Strong’s tags (3,082 nodes; lemmas weighted by inverse verse frequency, stop-list plus a 1.2% ceiling), typed edges — Nave’s see-also, co-occurrence (≥3 shared verses and Jaccard ≥0.02, or ≥12 shared), shared leading lemma — and mentions in the installed works by chapter (unigram/bigram of the head name; generic words and names under four letters skipped; 3,759 nodes). Rights: derived from public-domain and CC BY-SA sources; the method and counts are in `content/concepts/source.json`. Nothing computed is interpretation; the curated eight remain a labelled layer with `[FOUNDER]` definitions pending.


`messiah`, `creator`, `judgment`, `covenant`, `restoration`, `deliverer`, `king`, `izwi`. Definitions are short curated prose without citations. Under the domain model, `uMsindisi`, `uMdali`, `uMgwebo`, `iSiVumelwano` are **Titles/terms in isiZulu** paired with English concepts; the pairing itself is a Relationship that needs evidence (a lexical citation). `izwi` carries an honest note that its relationships are editorial prompts. See `SEED_GRAPH.md`.

## Part 2 — Source families (long-term)

Each family lists representative works and a working rights assessment. Inclusion is deliberate, by product decision, with taxonomy, provenance, rights, and rationale recorded here first.

### 2.1 Biblical texts

| Resource | Rights (working) | Notes |
| --- | --- | --- |
| KJV (default English) | PD | **Ingested Sept 17, 2026** — `content/kjv/`: 1769 text with 1611 Apocrypha, 80 books, 36,824 verses, word-level Strong's tags, footnotes; upstream eBible.org (sha256 in source.json). |
| Hebrew: Westminster Leningrad Codex | Open (CC) | **Ingested Sept 17** as `content/uhb/` — unfoldingWord® Hebrew Bible (OSHB/WLC) with lemma, Strong's and morphology on every word, CC BY-SA 4.0; 39 books, 23,145 verses; concordance built. |
| Greek NT: unfoldingWord® Greek NT (CC BY-SA 4.0; CNTR Bunning base); SBLGNT (CC BY 4.0); Byzantine/Majority (PD); Nestle 1904 (PD) | Open / PD | **UGNT ingested Sept 17** as `content/ugnt/` — lemma, Strong's, morphology; 27 books, 7,958 verses; concordance built. SBLGNT/Byzantine can follow as parallel witnesses. |
| Septuagint: Brenton (1851) Greek and English | PD | **Ingested Sept 17** as `content/lxx/` (Greek, 52 books incl. Greek Daniel/Esther, 3–4 Maccabees, Odes-less) and `content/brenton/` (English column, 53 books); eBible.org text; `witness: Septuagint`. Rahlfs-Hanhart remains copyrighted. |
| Vulgate: Clementine (1592) | PD | **Ingested Sept 17** as `content/vul/` — 73 books, 35,809 verses; eBible.org `latVUC`; `witness: Vulgate`. |
| Targum Onkelos (Aramaic) | PD text; digitisation licence to verify | Text is ancient; the freeware editions (Mechon Mamre, Hebrew Wikisource, Al HaTorah) derive from the Yemenite *Taj* first edition. Sefaria's edition credits Wikisource (CC BY-SA expected). **Rights check Sept 17: viable via Hebrew Wikisource under CC BY-SA; not yet ingested.** |
| Peshitta (Syriac OT/NT) | PD editions exist; clean digital text not yet found under an open licence | Lee (1823) OT and the BFBS 1905/1920 NT are public domain in print; syri.ac lists only public-domain resources; the CAL digital OT is research-use. **Rights check Sept 17: hold until an openly licensed transcription is confirmed.** |
| Ge'ez / Ethiopic witnesses (Dillmann editions, 19th c.) | PD (verify) | Needed for Enoch, Jubilees, Kebra Nagast, Ethiopian canon. **Rights check Sept 17:** STEP Bible lists a Ge'ez Bible (licence per version to confirm); Beta maṣāḥǝft carries open TEI transcriptions per manuscript; Dillmann's Octateuch (1853) is PD as scans. No clean openly licensed full text confirmed yet; hold. Fonts: Noto Serif Ethiopic. |
| Textual variants / apparatus | Mostly copyrighted | Cite scholarship; do not ingest apparatus without license. |
| Additional translations | Per license | Only where properly licensed. **NLT** (Tyndale) and **NKJV/NIV/ESV** are not redistributable: options are an API.Bible key (non-commercial tier, text fetched live, never stored) or a publisher license. Founder decision pending. |

### 2.1a Reference data ingested

| Resource | Rights | Status |
| --- | --- | --- |
| Strong's Hebrew and Greek dictionaries (1894) — Open Scriptures JSON edition | CC BY-SA 3.0 (underlying PD) | **Ingested Sept 17, 2026** — `content/lexicon-strongs/`: 8,674 Hebrew/Aramaic + 5,523 Greek entries. Attribute Open Scriptures. |
| KJV Strong's concordance (derived from the tagged KJV) | PD (derived) | **Built Sept 17, 2026** — `content/kjv/concordance/`: 14,047 numbers, 348,884 tagged words, lazy blocks. |
| Coptic SCRIPTORIUM: Sahidic OT (CoptOT), Sahidica NT, Bohairic NT | CC BY-SA 4.0 / Sahidica free-electronic-only (© J. Warren Wells) / CC BY 4.0 | **Ingested Sept 18, 2026** — `content/sahot` (46 books, 20,051 verses), `content/sahnt` (27 books, 7,906), `content/bohnt` (27 books, 7,957); Greek/Hebrew/Latin loanword spans kept (`sp.loan`). Sahidica may not be printed or sold without the editor’s permission. |
| Homiletics manuals: Broadus 1870, Brooks 1877, Spurgeon 1875 | PD (Internet Archive scans) | **Ingested Sept 18, 2026** — `content/broadus1870`, `content/brooks1877`, `content/spurgeon1875` under Commentaries & Reference; OCR uncorrected; Broadus loses several chapter heads to OCR (chapters merge), Spurgeon’s lecture titles supplied from the printed contents. Perkins 1592 held. |
| Ge’ez (Beta maṣāḥǝft; Charles 1906 Ethiopic Enoch) | CC BY-SA 4.0 / PD | **Held Sept 18, 2026** — Beta maṣāḥǝft publishes TEI transcriptions of individual manuscripts, not a verse-aligned Enoch or Jubilees; Charles’s Ethiopic text needs Ge’ez OCR. The Ge’ez shelf waits for a usable edition. |
| OpenBible.info Bible Geocoding Data (places) | CC BY 4.0 (coordinates via OpenStreetMap ODbL and Wikidata) | **Ingested Sept 18, 2026** — `content/places/`: 1,342 places (1,335 located), 8,742 verse references, best modern identification with precision; base map `public/assets/atlas/levant.svg` from Natural Earth 1:50m land (public domain) by `scripts/ingest/basemap.mjs`. |
| OpenBible.info Bible Geocoding Data (geometry) | CC BY 4.0; river and wadi paths derive from OpenStreetMap (ODbL) | **Ingested Sept 20, 2026** — `content/places/geometry.json` by `scripts/ingest/geometry.mjs`: 75 ancient regions as confidence isobands (drawn as bands, never borders; at most four rings) and 120 water paths, Douglas–Peucker simplified at 0.005°. Modern country polygons deliberately not taken. |
| Bible Routes from UBS Project MARBLE (Dr Leen Ritmeyer) | CC BY-SA 4.0 (© United Bible Societies 2023) | **Ingested Sept 20, 2026** — `content/routes/routes.json` (+ `LICENSE.md`) by `scripts/ingest/routes.mjs`: 179 GeoJSON journeys, Abram to Paul, each tagged with a named era; shown one at a time as a credited reconstruction (“the text names stations, not roads”). Share-alike: any derivative of the routes file carries the same licence. |
| Africa and the text (curated) | Claims authored for Wellspring; every claim names its edition — Breasted ARE IV (1906), Luckenbill ARAB II (1927), Sayce & Cowley (1906), Cowley (1923), Littmann DAE IV (1913), Budge (1928), McCrindle (1897), Payne Smith (1860), Evetts (1895, 1904–15), and held ANF/NPNF, Josephus, Kebra Nagast | **Authored Sept 20, 2026** — `content/places/africa.json`: 14 sites, 19 claims typed inscription / textual / tradition, each with KJV references verified against the held text and a “what this does not show” line. No route, border or lineage. Macadam’s Kawa (1949) is cited, not reproduced (in copyright). |
| OpenBible.info image records → site photographs | Each photograph its own open licence (PD, CC0, CC BY 2.0–4.0, CC BY-SA 1.0–4.0); copyright, satellite and GFDL-only records excluded | **Ingested Sept 20, 2026** — `content/places/photos/` (565 WebP at 320 px, 9 MB) + `photos.json` by `scripts/ingest/photos.mjs`: one per identified site, a view of the site before a detail, never a street or drawing; author, licence and Commons link shown on the card; fetched once from Wikimedia Commons (never hotlinked). |
| Itiner-e roads of the Roman Empire (static 2024) | CC BY 4.0 | **Ingested Sept 20, 2026** — `content/places/roads.json` by `scripts/ingest/roads.mjs`: 10,131 segments within the map bounds (857 certain, 8,919 conjectured, 355 hypothetical), unprojected from EPSG:3395, simplified 0.008°; drawn only under the Roman eras. |
| DARE (Digital Atlas of the Roman Empire) places, low tier | CC BY-SA 3.0 (via klokantech/roman-empire) | **Ingested Sept 20, 2026** — `content/places/ancient-names.json`: 1,398 Latin/Greek names with the modern place; labels only, Roman eras only. |
| Brown–Driver–Briggs, A Hebrew and English Lexicon of the Old Testament (1906) — Open Scriptures XML edition | PD text; edition and Lexical Index CC BY 4.0 | **Ingested Sept 21, 2026** — `content/lexicon-bdb/` by `scripts/ingest/lexicons.mjs`: 11,845 entries in 46 parts, 8,673 Strong’s numbers keyed through the Lexical Index (letters where BDB divides finer). The transcription is in progress upstream: ~3,300 entries carry BDB’s full text with references (`done`/`ref`/`new`), ~8,500 are outlines (senses only); each entry states which, with its 1906 page. Shown on Word Study under “In the lexicon”. |
| Abbott-Smith, A Manual Greek Lexicon of the New Testament (1922) — STEPBible “Translators Brief lexicon of Extended Strongs for Greek” (Tyndale House) | PD text; edition CC BY 4.0 (credit STEPBible.org and Tyndale House; refer to github.com/STEPBible as the source; note changes) | **Ingested Sept 21, 2026** — `content/lexicon-abbott-smith/`: 11,035 entries under 10,847 base Strong’s numbers (extended numbers a–z shown together), references linked through STEPBible’s book codes. A few words lack an Abbott-Smith entry and carry a Middle Liddell or STEPBible definition, as the source states. |
| STEPBible “Translators Brief lexicon of Extended Strongs for Hebrew” (TBESH) | CC BY 4.0 file, but the definitions derive from Online Bible’s abridged BDB — the file says permission must be obtained from Online Bible | **Not taken** (Sept 21, 2026). BDB itself covers Hebrew. |
| Treasury of Scripture Knowledge — CrossReferences.org phrase-anchored edition | TSK is public domain; the phrase-anchored, lightly curated edition is CC BY 4.0 (attribute CrossReferences.org) | **Ingested Sept 21, 2026** — `content/crossrefs-tsk/books/<osis>.json` by `scripts/ingest/tsk.mjs`: 63,668 anchored phrases, 336,859 references (KJV anchoring). Shown in the Reader’s Connections section under OpenBible’s vote-ranked list, by phrase; long lists fold at twelve. |
| Nave's Topical Bible (1896) + Torrey's New Topical Textbook (1897) | PD (structured build: j86schroeder/topical-bible-search, MIT pipeline, errata tracked) | **Ingested Sept 17, 2026** — `content/topics/`: 5,941 topics, 116,553 references. Limitations recorded in source.json: nineteenth-century Protestant headings, KJV-centric, no African or extra-biblical sources. |

### 2.2 African-language biblical material (first-class research languages)

**Ingested September 17, 2026 from eBible.org (Biblica open editions, CC BY-SA 4.0; license read from each package's copyright page at ingest and refused unless open):** chiShona (`sna`), isiNdebele/Zimbabwe (`nde`), Kiswahili Neno (`swh`), Yorùbá (`yor`), Asante Twi (`twi`), Igbo (`ibo`), Hausa (`hau`) — each the complete 66-book Bible. Also available on eBible under the same terms, not yet ingested: Akuapem Twi, Ewe, Chichewa, Gikuyu, Luganda, Lingala, Dholuo, Setswana (NT), Wolof, Somali, Yao (NT), Coptic NT (public domain), Swahili 1850 NT (public domain). **Amharic NT** (UBS 1962/2003) is listed as redistributable but its copyright page states no open license — verify with UBS before ingesting.

**Not on eBible (the Nguni/Sotho gap):** isiZulu, isiXhosa, Sesotho, Sepedi, Xitsonga, Tshivenda, siSwati — all Bible Society of South Africa copyrights. Routes: (1) a BSSA license; (2) digitize public-domain historical editions — isiZulu 1883 (American Board), isiXhosa 1859/1889 (Appleyard), Sesotho 1881 (Paris Mission) — via OCR + proofreading, which is feasible for Latin-script languages and would give Wellspring texts nobody else carries digitally, clearly labeled as historic editions.

| Language | Known editions | Rights (working) |
| --- | --- | --- |
| isiZulu | 1959 Bible (Bible Society of South Africa); 2020 translation | **Copyright BSSA — license required** |
| isiXhosa | 1975 / 1996 | Copyright BSSA — license required |
| Sesotho | 1909 (Southern Sotho) | Possibly PD by age; verify with BSSA |
| Shona | 1949 Union Shona; 2001 | Copyright (Bible Society of Zimbabwe) — verify |
| Yoruba | Crowther/Bible Society 1884–1900 | Historic edition likely PD; modern revisions copyrighted |
| Akan/Twi | Christaller 1871 | Likely PD; modern revisions copyrighted |
| Others | — | Add per decision |

Language tools (term, transliteration, gloss, occurrences) depend on these texts; licensing is the gating item, not code.

### 2.3 Apocrypha, pseudepigrapha, related literature

**Ingested Sept 18, 2026:** `content/kebra/` — the **Kebra Nagast** in Budge's 1922 translation (Internet Archive item `kebranagast`, OCR), 108 of 117 chapter headings separated; the nine the OCR could not separate (11, 35, 36, 81, 92, 101, 110–112) are recorded on the package and their text sits within the preceding chapter. Comparative Traditions category. `content/bookofdead/` — Budge, *The Book of the Dead* (British Museum, 1920; Gutenberg #7145): an introduction with translated extracts, nine chapters. Held for a cleaner source: *Enuma Elish* (King 1902 — the Archive item lacks OCR text), Egyptian texts beyond Budge's extracts.

1 Enoch (Charles 1917, PD — **ingested Sept 17** from Wikisource as `content/enoch1/`, 108 chapters, 1,012 verses, Charles's editorial markers preserved), 2 Enoch (Morfill/Charles 1896, PD), 3 Enoch (jurisdiction-dependent), Jubilees (Charles, PD), Kebra Nagast (Budge 1922, PD), 1611 Apocrypha (KJV, PD), Dead Sea Scrolls (Hebrew/Aramaic transcriptions: some open; major English translations copyrighted). Every work carries manuscript, edition, translation, provenance, and per-tradition canonical status.

### 2.4 Ancient Jewish sources

**Ingested Sept 17, 2026 (Whiston 1737, public domain, Project Gutenberg):** `content/antiquities/` (20 books + preface, 257 chapters, 1,428 sections), `content/wars/` (7 books + preface, 109 chapters, 666 sections), `content/apion/` (2 books, 77 sections), `content/life/` (76 sections). Whiston's footnotes omitted (translator's commentary); section numbering follows Whiston; chapter ids `antiquities.AntI.3`. Category: Ancient Histories. Ingester `scripts/ingest/gutenberg.mjs`.

Josephus (Whiston, PD), Philo (Yonge, PD), Mishnah (Danby 1933 — PD in UK, US status pending until 2029; Sefaria open translations available under CC), Talmud (Soncino copyrighted; William Davidson Talmud CC BY-NC — non-commercial restriction matters), Midrash (mostly copyrighted). Presence ≠ endorsement.

### 2.5 Early Christian sources

**Ingested Sept 18, 2026 (CCEL ThML, public-domain text; CCEL edition credited, `rightsFlag: credit-ccel`):** `content/anf01/` (Apostolic Fathers, Justin, Irenaeus — 42 works), `content/anf02/` (Hermas, Tatian, Athenagoras, Theophilus, **Clement of Alexandria** — 12 works), `content/anf03/` (**Tertullian of Carthage** — 25 works), `content/npnf101/` (**Augustine of Hippo**: Confessions and Letters — 19 works), `content/npnf102/` (Augustine: The City of God, On Christian Doctrine — 31 works). Category: Early Church Writings. Ingester `scripts/ingest/ccel.mjs` (kind `work`).

Apostolic Fathers (Lightfoot, PD), Ante-Nicene / Nicene & Post-Nicene Fathers (Schaff, PD), council canons (PD in older translations), African Christian writers (Tertullian, Cyprian, Augustine, Origen, Athanasius, Clement of Alexandria — PD in ANF/NPNF), Coptic material (mixed), Ethiopian/Eritrean Tewahedo tradition (Ge'ez liturgy and literature; older editions PD), Nubian Christian material (scholarship copyrighted; primary inscriptions PD).

### 2.6 Islamic sources (comparative)

**Ingested Sept 17, 2026:** `content/quran/` — Pickthall, *The Meaning of the Glorious Koran* (1930), 114 surahs, 6,236 ayat, surah names (Arabic, transliterated, English) and place of revelation from Tanzil metadata. **Rights flag:** the translation is public domain (US from 2026; UK, translator d. 1936), but the digital text comes from Tanzil.net under non-commercial terms (`rightsFlag: non-commercial-source`); re-source from a public-domain scan before any commercial use. Wikisource's Pickthall transcription is incomplete; Rodwell (1861) is complete there but reorders the surahs. Ingester `scripts/ingest/quran.mjs`.

Qur'an Arabic text (PD); translations: Rodwell/Palmer (PD), Pickthall (PD in most jurisdictions), Sahih International and others (copyrighted). Hadith and tafsir: mostly copyrighted translations. Never placed in the Scripture canonical category; `canonicalStatus` for Islamic works is `not-applicable`.

### 2.7 African history, oral tradition, living traditions (differentiator)

**Ingested Sept 18, 2026 (`scripts/ingest/archive-essay.mjs`, `npm run ingest:essay <id>`):** `content/junod1908/` — Junod, “The Balemba of the Zoutpansberg (Transvaal)”, *Folk-Lore* 19 (1908), 56 units from the IGNCA scan of the volume (OCR mediocre, uncorrected); linked from the Lemba dossier. `content/faitlovitch1920/` — Faïtlovitch, *The Falashas* (JPS, 1920; reprinted from the American Jewish Year Book 5681; author d. 1955, PD in life-plus-70 countries from 2026), 29 units; linked from the Beta Israel dossier. **Held:** Flad, *The Falashas (Jews) of Abyssinia* (1869) — the only scan (Bombay copy) is cropped at the margins and about half its OCR lines lose characters; the dossier says so. Halévy, “Travels in Abyssinia” (1877) — not on the Archive as a scanned text; the 1877 *Prières des Falashas* (Ge’ez with French) is, and is a candidate for the Ge’ez shelf.

**Ingested Sept 18, 2026 (CCEL ThML, `scripts/ingest/ccel.mjs`):** Ante-Nicene Fathers 4–7 (Origen, Cyprian of Carthage, Dionysius of Alexandria, Julius Africanus, Arnobius, Lactantius, the Apostolic Constitutions and the Liturgy of St Mark), Nicene and Post-Nicene Fathers 2.1 (Eusebius, Church History), 2.4 (Athanasius) and 2.14 (the Seven Ecumenical Councils), and Calvin’s Commentary on Genesis (two volumes, King’s translation) as a commentary beside Henry and JFB; Smith’s Bible Dictionary (1884 ed., 4,561 entries) and Schaff’s A Dictionary of the Bible (1880, 5,087 entries; CCEL’s ThML for both mirrored in neuu-org/bible-dictionary-dataset, since ccel.org no longer serves the XML) as dictionaries beside Easton’s — a concept page links every dictionary that carries its headword. The International Standard Bible Encyclopedia (1915; 9,349 signed articles) is read directly from CrossWire’s public-domain SWORD module by `scripts/ingest/sword-zld.mjs` (`npm run ingest:isbe`; the zLD layout is documented in the script) — the fourth dictionary, and the deepest: Ethiopia, Cush, Sheba and the like have full articles with their scripture references. Philo of Alexandria (Yonge’s four volumes, 1854–55; `scripts/ingest/archive-book.mjs`, `npm run ingest:philo`): 49 treatises as chapters from the volumes’ capitalised title blocks, 11,061 paragraph units, under Histories & Accounts beside Josephus; OCR uncorrected (Yonge’s section numerals stay inline). Held: the Jewish Encyclopedia (1901–06) — the Archive scans are three-column pages whose OCR interleaves columns; the clean text at jewishencyclopedia.com is not offered as a dataset.

**Ingested Sept 18, 2026 (layout-aware OCR; `scripts/ingest/archive-tales.mjs`, `npm run ingest:chatelain`):** `content/chatelain/` — Chatelain, *Folk-Tales of Angola* (1894; Memoirs of the American Folk-Lore Society 1; PD), 50 tales headed by their Roman numerals, Kimbundu text with Chatelain’s literal English paired paragraph by paragraph (tale I, printed interlinear, split by the language of each line), 577 endnotes attached to the units carrying their numbers, the informant note for tale 11 attached as printed. Limits recorded in `source.json › method`: paragraph pairing depends on the OCR’s indentation and can drift within a tale; units without an English counterpart keep the Kimbundu as their text; OCR errors are not corrected.

**Ingested Sept 18, 2026 (layout-aware OCR; `scripts/ingest/archive-columns.mjs`, `npm run ingest:callaway`):** `content/callaway/` — Callaway, *The Religious System of the Amazulu* (1868–70; Folk-Lore Society reprint 1884; PD), 9 parts by running head, 1,962 units of which 1,335 are bilingual (Zulu paragraph with the facing English, paired by position from the DjVu word coordinates), 16 named narrators folded from OCR variants (Umpengula Mbanda, Ufulatela Sitole, Unolala Zondi, Ushunguiwane Zimase, Unsukuzonke Memela, Ukoto Mhlongo, Uguaise Mdunga, Usetemba Dhladhla…), 417 footnotes attached to the unit carrying the number and shown as study notes. Known limits, recorded in `source.json › method`: paragraph pairing can slip by a sentence where the columns run unevenly; OCR errors in the Zulu (the printer’s ‘hl’ ligature often reads as ‘/tl’) are not corrected; Callaway’s own full-width dialogues appear as unpaired English units. The Zulu is the primary text and is shown first.

**Ingested Sept 18, 2026 (Internet Archive OCR, conservatively cleaned; `scripts/ingest/archive.mjs`):** `content/theal1882/` — Theal, *Kaffir Folk-lore* (1882), displayed as “Xhosa Tales (Theal, 1882)” with the original title in the edition and citation fields: 21 Xhosa narratives in English, Oral Tradition Archive. `content/stern1862/` — Stern, *Wanderings among the Falashas in Abyssinia* (1862), 18 of 20 chapters separated (two headings merged; recorded), Histories & Accounts; linked from the Beta Israel dossier. **Callaway's Religious System of the Amazulu:** the two-column Zulu/English scan OCRs into interleaved blocks with unreliable Zulu; it needs a layout-aware transcription (hOCR columns) before ingest — held, not faked. **Chatelain's Folk-Tales of Angola:** Kimbundu/English interleaved; same hold.

No ingestible corpus exists yet. This family is built by **collection and licensing**, not download:

- Documented traditions of communities such as the Lemba and Beta Israel — primary oral testimony must be collected with consent or licensed from existing archives; existing scholarship (e.g., Parfitt; Kaplan; Quirin) is copyrighted and enters as secondary sources.
- Published early collections (Callaway 1868–70 on Zulu religious tradition; Rattray on Ashanti; Junod on Tsonga; Casalis on Basotho) are PD but are **colonial-era collections** — record collector bias and transmission context.
- Every record follows the TraditionEntry shape: community, people, narrator, collector, date, location, language, verbatim and normalized transcription, translation, translator, notes, variants, provenance, permissions, media.

### 2.8 Western and modern scholarship

**Ingested Sept 18, 2026 — public-domain commentaries and reference (CCEL):** `content/mhc/` (Matthew Henry's complete Commentary, six volumes merged, 66 books, 4,258 sections), `content/mhcc/` (the Concise Commentary, 4,131 sections keyed to verse ranges), `content/jfb/` (Jamieson–Fausset–Brown, 20,958 sections), `content/ebd/` (Easton's Bible Dictionary, 3,964 entries with Scripture cited). Shown as named-author interpretation in the Passage Guide, Resource Panel and Reader; the dictionary at `/dictionary/ebd`. Next: Matthew Henry complete (6 vols), Calvin, Barnes/Gill/Clarke (source to confirm), ISBE, Smith's, Jewish Encyclopedia.

Commentaries, dictionaries, encyclopedias, monographs, journals, dissertations, atlases, archaeological reports, textual criticism, linguistics. Mostly copyrighted: enters as **citable references** (metadata + citation), with full text only where licensed or open access.

### 2.9 African and Black scholarship (deliberately foregrounded)

**Peoples dossiers (Sept 18, 2026):** `src/data/peoples.js` — **Lemba** (8 sources: Junod 1908 PD; van Warmelo 1935; Mathivha 1992; Parfitt 1992; Spurdle & Jenkins 1996; Thomas et al. 2000; le Roux 2003; Soodyall 2013 open access) and **Beta Israel** (11 sources: Bruce 1790, Stern 1862, Flad 1869, Halévy 1877, Faitlovitch 1905 — all PD; Leslau 1951, Ullendorff 1968, Kaplan 1992, Quirin 1992, Lucotte & Smets 1999, Behar et al. 2010 — cited). Each source states its access; public-domain accounts are the next full-text ingest (Stern, Flad, Halévy from scans; Junod's Folk-Lore article). Claims carry typed evidence; genetic evidence is labeled as lineage ancestry only (ADR 014). Le Roux's open-access articles (HTS / Verbum et Ecclesia, CC BY) are full-text candidates.

African biblical scholarship, African history, archaeology, linguistics, theology; Black biblical scholarship; diaspora scholarship. Same rights posture as 2.8; foregrounding is a curation and ranking decision, not an authority claim.

### 2.10 Non-textual evidence families

Archaeological reports, material culture, iconography, historical geography, population genetics (journal articles). These enter as `Evidence` with a mandatory `evidenceType` and recorded `limitations`, cited rather than ingested.

## Part 3 — Ingestion order (recommendation, not yet approved)

1. Full KJV (PD; unlocks Reader, Search, Passage navigation, Scripture insertion).
2. 1 Enoch complete, Jubilees, Kebra Nagast, 2 Enoch (PD Charles/Budge editions).
3. Hebrew (WLC) and Greek (SBLGNT) base texts for Word Study foundations.
4. One licensed African-language Bible (isiZulu is the natural first; license conversation with BSSA required).
5. First provenanced TraditionEntry records (replace the six placeholder archive labels).
6. Jewish and early Christian PD sources.
7. Everything else by product decision.

## Runtime dependencies that are not content (Sept 18, 2026)

- **WebLLM** (`@mlc-ai/web-llm`, Apache-2.0) is imported from `https://esm.run/@mlc-ai/web-llm` only after a user turns the study assistant on with “On this device”. Model weights come from the MLC model hub on Hugging Face and are cached in the user’s browser; none are shipped in this repository. Offered models and their licences: Qwen 2.5 1.5B and 7B (Apache-2.0), Qwen 2.5 3B (Qwen research licence), Llama 3.2 3B (Llama 3.2 community licence), Phi 3.5 mini (MIT). Nothing a model says is content: it is never cited, never a source, never authoritative (ADR 013, ADR 017).

## Rights pass against "free, with optional contributions" (Sept 18, 2026 — Execution plan, Phase 3)

Wellspring is free to use, operated by an LLC, with optional voluntary contributions planned. Read against each licence's actual text:

- **Tanzil (Pickthall's Qurʾan, `content/quran`)** — Tanzil's translations page: "translations provided at this page are for non-commercial purposes only. If used otherwise, you need to obtain necessary permission from the translator or the publisher"; a link back is required when more than three translations are used. Wellspring uses one, charges nothing, and shows no advertising; the translation itself is public domain (published 1930; US public domain from 2026; translator d. 1936). **Conclusion:** acceptable at launch as non-commercial use, with a credit line and a link to Tanzil on the package; **re-source from the 1930 Knopf scan (Internet Archive) before any revenue beyond voluntary contributions**, so no Tanzil terms apply at all. Recorded on the package as `rightsFlag: non-commercial-source`.
- **Sahidica (`content/sahnt`)** — "free of charge for use in free electronic editions with the full title and copyright credited; written permission required for print." Wellspring is a free electronic edition and credits the full title and copyright. **Conclusion:** acceptable; a user printing a sermon that contains a Sahidic verse is personal use, not Wellspring publishing in print. Recorded as `free-electronic-only`.
- **Coptic OT (CC BY-SA 4.0), Bohairic NT (CC BY 4.0), eBible.org translations (CC BY-SA 4.0, Biblica), unfoldingWord UHB/UGNT (CC BY-SA 4.0), Open Scriptures Strong's (CC BY-SA 3.0), OpenBible places (CC BY 4.0)** — attribution shown on each package; texts unmodified; the `concepts` package derives lexical profiles from the CC BY-SA Strong's data and is therefore **CC BY-SA itself** (recorded). No commercial restriction. **Conclusion:** acceptable.
- **CCEL digital editions (sixteen packages flagged `credit-ccel`: anf01–07, npnf101/102/201/204/214, calgen1/2, ebd, jfb, mhc, mhcc, smith, schaffdict)** — CCEL's policy: editions "may be used for personal, educational, or non-profit purposes"; "Contact us for permission to republish CCEL works or to use them commercially." The underlying texts are public domain; CCEL asserts rights in its digital editions. Wellspring republishes them. **Conclusion: founder action before launch — write to CCEL for permission to republish under Wellspring's free, non-commercial terms (commonly granted to free projects), and record the reply here. Fallback if refused:** re-source each from Internet Archive scans by OCR (the `archive-book` ingester exists), with OCR limits stated.
- **Public-domain scans (Internet Archive, University of Toronto):** no restriction; OCR limits stated per package.

Nothing here changes the shelf today. Two items carry conditions into launch: Tanzil (re-source before revenue) and CCEL (permission or re-source).
