# SEMANTIC AI PLUGIN — BUILD SPEC FOR INLINE TAGGING UPGRADE

## What This Bundle Contains

```
semantic-ai-bundle/
├── plugin/                          # The existing Obsidian plugin
│   ├── main.js                      # 5,588 lines, compiled JS (the working engine)
│   ├── manifest.json                # Plugin metadata
│   ├── data.json                    # Settings (API key, model, prompts, classifiers)
│   ├── styles.css                   # Plugin styling
│   ├── semantic-ai-prompts.json     # v2 prompts (CURRENT — updated 2026-03-07)
│   ├── semantic-ai-prompts-BACKUP.json  # Original prompts (pre-update)
│   ├── semantic-ai-prompts-v2.json  # Same as current (archive copy)
│   └── axiom-reference.md           # 189 axiom lossless matrix
├── reference/                       # Canonical docs the plugin must align to
│   ├── CANONICAL_FRAMING.md         # 10 settled structural claims
│   ├── CANONICAL_TAG_TAXONOMY.md    # 79 canonical tags (THE master list)
│   ├── AXIOM_DIAGRAM_TEMPLATES.md   # 10 visual shapes per content type
│   ├── AXIOM_MATRIX_LOSSLESS.md     # 189 axioms compressed (~6K tokens)
│   ├── theophysics-content-callouts.css  # 10 collapsible callout types
│   └── theophysics-inline-tag-hider.css  # Hides inline tags in Reading Mode
└── BUILD_SPEC.md                    # This file
```


## What Already Works

The plugin currently does DOCUMENT-LEVEL classification:
1. Opens a note in Obsidian
2. Sends full note text to OpenAI API (gpt-4o or gpt-4o-mini)
3. Classifies using 13 prompts + 8 custom classifiers
4. Returns structured output (tagged entities, relationships, etc.)
5. Generates Mermaid flow graphs
6. Appends YAML-style tags to the document

The classification engine is SOLID. The prompts were updated today
to output collapsed Obsidian callouts and use canonical variable names.

## What Needs to Be Added

### Feature 1: PARAGRAPH-LEVEL INLINE TAGGING

Instead of (or in addition to) document-level classification,
the plugin should tag EACH PARAGRAPH individually.

Current behavior:
- Scans whole document → outputs one classification block at bottom

Needed behavior:
- Scans document paragraph by paragraph
- For each paragraph, identifies which axioms/claims/evidence/laws apply
- Inserts an INVISIBLE inline tag after the paragraph
- Reader sees nothing in Reading Mode
- Knowledge graph can query every paragraph

### Feature 2: TWO OUTPUT MODES

MODE A — HTML Comment (invisible everywhere):
```markdown
The Master Equation demands seven conclusions.
<!-- @tag axiom:AX-025 vars:M,Q,S laws:01,06 forced:sin-ent status:verified -->
```

MODE B — Dataview inline field (invisible in Reading Mode with CSS):
```markdown
The Master Equation demands seven conclusions.
[axiom:: AX-025] [vars:: M,Q,S] [laws:: 01,06] [forced:: sin-ent]
```

Both modes use the same 79 canonical tags from CANONICAL_TAG_TAXONOMY.md.
User selects mode in plugin settings.


### Feature 3: OPTIONAL COLLAPSED CALLOUTS

When the user WANTS visible inline markers (for publication docs),
the plugin can also insert collapsed callouts:

```markdown
The framework predicts measurable coherence effects from prayer.

> [!prediction]- Prayer Coherence Effect
> Framework predicts ≥5σ significance in controlled REG experiments.
> **Supports:** AX-125, Law 02
> **Status:** untested
```

These use the CSS from theophysics-content-callouts.css.
10 callout types: axiom, law, evidence, hypothesis, prediction,
falsification, convergence, equation, timewall, isomorphism.

The user selects per-document or in settings:
- "tags only" (invisible inline tags)
- "callouts only" (visible collapsed blocks)
- "both" (callouts where important, tags on everything else)

### Feature 4: COMPRESSED YAML FRONTMATTER

After paragraph-level tagging, the plugin should ALSO generate
a compressed YAML frontmatter summary of the whole document:

```yaml
---
vars: [G, M, E, S]
pairs: [I, II]
laws: [01, 03, 06]
forced: [sin-ent, grace-neg]
fruits: []
evidence: [data-pear]
axioms: [AX-001, AX-009, AX-025, AX-039]
status: verified
domain: [physics, theology]
---
```

This is the document-level summary. The inline tags are
paragraph-level detail. Both should be generated in one pass.

#### Full-schema compatibility requirement

Compressed frontmatter is the transport format for fast note tagging.
When the user requests expanded metadata, map generated output to
`reference/THEOPHYSICS_MASTER_YAML_SCHEMA_v1.0.md` and defer to it as
normative for ALWAYS/conditional logic:
- L1 Identity: ALWAYS
- L2 Tree Position: ALWAYS
- L18 Claims & Evidence: ALWAYS for `paper`, `axiom`, `theorem`, `hypothesis`
- L20 Graph Edges: ALWAYS with minimum one edge


### Feature 5: EXTENDED MACHINE TAG REGISTRY + RELATIONSHIP SCAN

The scanner must ingest an extended machine registry (target scale: 400-500+ metrics)
and map each hit to canonical tags + graph relationship semantics.

Reference files:
- `reference/THEOPHYSICS_MACHINE_TAG_REGISTRY_v1.0.tsv` (machine codes, canonical tags, node types)
- `reference/TAG_SCAN_AND_RELATIONSHIP_SPEC_v1.0.md` (invisible HTML + YAML + graph contract)

Required behavior:
1. Scan paragraphs against machine codes, canonical tags, aliases, and semantic similarity
2. Emit invisible HTML comment markers per paragraph
3. Emit compressed YAML summary including `codes`, `tags`, and `relationships`
4. Emit relationship buckets: `depends_on`, `supports`, `contradicts`, `tests`, `extends`, `bridges`, `attacks`

Integration rules (compressed + scan):
- Scan output extends the existing compressed frontmatter and MUST be nested under `scan:`.
- Existing top-level compressed keys (`vars`, `pairs`, `laws`, `forced`, etc.) remain unchanged.
- Required nested shape:

```yaml
scan:
  version: tphys-scan-v1
  registry: theophysics-machine-v1.0
  codes: []
  tags: []
  relationships:
    depends_on: []
    supports: []
    contradicts: []
    tests: []
    extends: []
    bridges: []
    attacks: []
```

Zero-relationship expansion rule:
- If all relationship buckets are empty at scan time, expansion to master schema MUST still satisfy L20.
- In that case emit a synthetic weak edge:
  - `edges.depends_on[0] = { target: "UNRESOLVED_CONTEXT", relationship: "structurally", strength: "weak" }`
  - and add a note explaining no explicit relationship was detected during scan.

## THE 79 CANONICAL TAGS (complete reference in CANONICAL_TAG_TAXONOMY.md)

Content types (7): axiom, claim, law, evidence, equation, prediction, definition
Structural types (8): isomorphism, convergence, falsification, timewall, dependency, enables, contradicts, supports
Domain tags (6): physics, theology, information, consciousness, morality, mathematics
Variable tags (10): G, M, E, S, T, K, R, Q, F, C
Symmetry pairs (5): I, II, III, IV, V
Law tags (10): 01-10
Forced conclusions (7): sin-ent, grace-neg, faith-obs, term-obs, coh-con, open-sys, time-wall
Fruit tags (9): love, joy, peace, patience, kindness, goodness, faithfulness, gentleness, self-control
Evidence datasets (4): data-pear, data-gcp, data-prop-cosmos, data-oxford
Status tags (7): verified, partial, speculative, walled, falsified, canonical, unregistered
Operation tags (6): establish, derive, challenge, bridge, anchor, declare

## THE 189 AXIOM IDs (matching reference in AXIOM_MATRIX_LOSSLESS.md)

Format: AX-001 through AX-189
Each has: short name, compressed claim, falsification path
The axiom-reference.md file in the plugin folder has the full list.
The Excel (Master Theophysics Obsidian VAULT_TAG_SYSTEM_v1.xlsx,
sheet AXIOM_COMPRESSED) has each axiom with pre-built YAML blocks.

## TECHNICAL NOTES

- Plugin is Obsidian-compatible (uses Obsidian API via main.js)
- API calls go to OpenAI (gpt-4o-mini for step 1, gpt-4o for step 2)
- API key is in data.json (live key, DO NOT commit to public repos)
- The plugin already has batch processing with confirmation dialog
- Token estimation is built in (showTokenEstimate: true)
- Mermaid generation is built in (autoGenerateMermaid: true)
- Postgres sync capability exists but is disabled

## WHAT THE CODER SHOULD DO

1. READ the existing main.js to understand the plugin architecture
2. KEEP the existing classification engine (prompts + API calls)
3. ADD a paragraph splitter that feeds paragraphs individually
4. ADD an inline tag inserter (HTML comment or Dataview field)
5. ADD a callout generator (using the 10 callout types)
6. ADD a frontmatter YAML generator (compressed format)
7. ADD settings toggles for output mode selection
8. TEST on the Turtles paper (O:\_Theophysics_v3\04_THEOPYHISCS\
   The Convergence\The Turtles and the Floor\)

## WHAT NOT TO CHANGE

- The classification prompts (semantic-ai-prompts.json) — already updated
- The custom classifiers — already correct
- The API connection logic — already working
- The Mermaid generation — already functional

The upgrade is about WHERE the output goes (inline vs bottom)
and at WHAT GRANULARITY (paragraph vs document), not about
changing the classification logic itself.
