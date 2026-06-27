# Literature Review — Drafting Context

## Project

Honours thesis: **Enhancing the literature search process through a knowledge-graph enhanced search engine.** The system ingests paper metadata from OpenAlex into a pre-defined knowledge graph schema, and runs a search pipeline combining LLM-based natural-language-to-structured-query extraction, BM25 over keyword/topic text, graph traversal over pivot entities, and planned dense embedding retrieval. See `schema/schema.yaml` for the KG schema and `search_pipeline_proposal.md` for pipeline details.

## Document this literature review sits inside

IEEEtran, onecolumn, journal class. The lit review is one chapter of a larger thesis document (intro, lit review, methodology, results, discussion, conclusion). It does not need its own intro or conclusion — those live at the thesis level.

## LaTeX sectioning

- `\section{Literature Review}` — the chapter title, one occurrence.
- `\subsection{}` — the five lit review sections (History of scholarly search, Recent research advances, Current available KGs and pipelines with benchmarks, Benchmarks for scholarly retrieval, Limitations of existing systems and research gaps).
- `\subsubsection{}` — broken-down components within each section.

No sectioning below `\subsubsection{}`.

## Target length

~7,600 words total, roughly 10–12 pages in IEEEtran onecolumn. Distribution as drafted:

- 1. History of scholarly search: ~1,100 words
- 2. Recent research advances: ~3,000 words
- 3. Current KGs and pipelines: ~1,700 words (plus Table I)
- 4. Benchmarks for scholarly retrieval: ~700 words (plus Table II)
- 5. Limitations of existing systems and research gaps: ~1,100 words

## Argumentative spine

The five sections form a narrative cascade, not a taxonomy:

1. **History** — five-era succession (pre-digital indexing, early digital bibliographic databases, web-era keyword search, modern scholarly infrastructure with structure re-introduced over full-text, and AI-enhanced tools layered on top). Each generation carries forward its substrate, resolves a dominant limitation of the previous era, and introduces a new one. The structured / free-text tension is the through-line. The section closes by setting up the four method threads of section 2 as the field's current attempt to reconcile the two paradigms rather than choose between them.
2. **Recent research advances** — four threads: scholarly embeddings and dense retrieval, graph-augmented retrieval, natural-language-to-structured-query translation, and LLM-based query reformulation. The section opens by stating the thesis's stance toward each (dense retrieval kept as a hybrid signal; graph-augmented methods motivate KG ingestion but supply no scientific-NL baseline to copy; structured-query translation is the chosen path via an intermediate JSON; reformulation is set aside) and develops each stance within the relevant subsection. Arguments about vocabulary mismatch and ceilings on single-vector dense retrieval (carried empirically by LitSearch) live inside these subsections rather than in a standalone limitations section. The Weller-driven case against generative expansion for strong retrievers lives in the reformulation subsection.
3. **Current KGs and pipelines** — three clusters: scholarly KGs as data infrastructure (MAKG, OpenAlex, SemOpenAlex, S2AG, OAG/OAG-Bench, AceKG, ORKG, OpenCitations), traditional scholarly search engines (Google Scholar, Dimensions, Lens, OpenAlex-native, CORE, BASE, Semantic Scholar, Scite, Connected Papers, Research Rabbit, Inciteful), and LLM-augmented/agentic systems (PaperQA2, OpenScholar, Ai2 Scholar QA, ORKG Ask). Closes with three analytical axes (text-centric vs graph-native retrieval; NL vs structured queries; evaluation modes) along which the landscape stratifies.
4. **Benchmarks for scholarly retrieval** — analytical survey mapped onto pipeline components: general IR benchmarks (MS MARCO, TREC DL, BEIR, LoTTE), scientific retrieval benchmarks (SciDocs, CSFCube, LitSearch, SciFact, NFCorpus, TREC-COVID, TREC Genomics), and scholarly KG / citation / QA benchmarks (DBLP-QuAD, SciQA, with the long-form-QA cluster scoped out). Identifies that no benchmark jointly exercises NL retrieval, structured-query translation and graph traversal over a scholarly substrate — the absence section 5 sharpens into the central gap.
5. **Limitations of existing systems and research gaps** — four sub-threads: scholarly KGs as imperfect data infrastructure (citation incompleteness, missing affiliations, contested concept hierarchies); the joint-coverage gap across methods, systems and benchmarks; sparse user-facing evaluation; and a closing synthesis subsection framing the KG as primary semantic interface, positioning the agentic/RAG cluster as consumers rather than competitors of the proposed pipeline, and stating the specific gap. The gap statement hands off to the methodology chapter.

## Inputs

- `lit_review_inputs/section1.tex` through `section6.tex` — deep research outputs used as source material. These are drafts to synthesise from, not prose to port verbatim.
- `lit_review_inputs/bibliography.bib` — consolidated, deduplicated bibliography.
- `schema/schema.yaml` — the KG schema.
- `tex_files/1.ProjectDescription.tex` — proposal framing to reuse (not recopy) in the lit review.

## Drafting principles

1. **Synthesis, not summary.** Most paragraphs should have 2–4 sources in dialogue. If a paragraph cites only one source, it's probably a summary.
2. **Student voice.** Prose should read as the author's own critical engagement. Plan to rewrite 30–50% of sentences from the source material. Include evaluative statements where appropriate.
3. **Reporting verbs signal stance.** "Demonstrates", "argues", "contends", "contrasts with" — not flat "says" or "shows".
4. **Primary source engagement.** Key papers that must be read directly rather than cited through the deep research summary: Weller et al. 2024 (expansion failure modes), LitSearch 2024, SPECTER2 / SciRepEval, OpenScholar, PaperQA2, SemOpenAlex.
5. **Continuous academic prose.** No bullet points, no numbered lists.

## Conventions

- Citation style: `\cite{key}` throughout, IEEEtran default rendering.
- Citation keys: `author_year_shortword` (e.g. `weller_expansions_2024`).
- British English spelling throughout (consistent with the proposal).
- Tables must be IEEEtran-compatible without column overflow.

## Known issues to resolve during drafting

- The proposal mentions biomedical as the "representative vertical" but the schema is domain-general. The lit review should acknowledge this scoping shift somewhere in section 3 or 5.
- Cross-source deduplication is out of scope (OpenAlex only) — don't over-cover the entity resolution literature.
- Research-paper recommendation is explicitly scoped out; a one-sentence acknowledgement of the Beel 2016 boundary appears in section 2 (within the NL-to-structured-query subsection) and should stay.