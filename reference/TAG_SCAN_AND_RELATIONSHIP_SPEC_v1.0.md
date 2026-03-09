# TAG SCAN + RELATIONSHIP SPEC v1.0

## Goal

Enable the plugin to scan a large machine registry (400–500+ metrics/tags), then emit:

1. **Invisible machine tags** as HTML comments for per-paragraph indexing.
2. **Compressed YAML summary** for document-level aggregation.
3. **Graph relationship payloads** to recover dependency/support/contradiction structure.

---

## Registry Source of Truth

- Primary canonical public list: `reference/CANONICAL_TAG_TAXONOMY.md`.
- Extended machine registry (short codes, families, graph node hints):
  `reference/THEOPHYSICS_MACHINE_TAG_REGISTRY_v1.0.tsv`.

The scanner MUST treat the extended registry as additive and support both:
- canonical tags for output,
- short machine codes for matching/routing.

---

## Required Output Modes

### A) Invisible HTML marker mode (paragraph-level)

```html
<!-- @tphys tags="pillar/physics,χ_var/G,law/Law01" 
     codes="Pph,Xg,D01"
     rel="supports:AX-025|depends_on:P01|bridges:physics>theology"
     confidence="0.88" -->
```

Rules:
- Must be appended immediately after the paragraph block.
- Must not alter reading mode visual output.
- Must include both canonical tags and compact machine codes.

### B) YAML mode (document-level compressed summary)

```yaml
---
scan_version: tphys-scan-v1
scan_registry: theophysics-machine-v1.0
codes: [Pph, Xg, D01]
tags: [pillar/physics, χ_var/G, law/Law01]
relationships:
  depends_on: [P01]
  supports: [AX-025]
  bridges: [physics>theology]
coverage:
  matched_metrics: 147
  registry_size: 500
  recall_mode: high
---
```

Rules:
- YAML summary is required whenever inline scanning runs.
- Relationship buckets must be emitted even when empty.

### Compressed frontmatter integration (normative)

Scan payload does not replace existing compressed keys. It MUST be nested under:

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

---

## Relationship Extraction Contract

For each detected tag hit, scanner should optionally infer graph tuples:

- `depends_on`
- `supports`
- `contradicts`
- `tests`
- `extends`
- `bridges`
- `attacks`

Tuple format (normalized internal form):

```json
{
  "source_code": "Xg",
  "source_tag": "χ_var/G",
  "edge": "supports",
  "target": "AX-025",
  "strength": "moderate",
  "evidence_span": "paragraph_12"
}
```

---

## Matching Strategy (Required)

1. Normalize text (unicode, punctuation, case).
2. Match by ordered precedence:
   - exact code hit (`Xg`, `D01`, `BC4`)
   - exact canonical tag
   - alias/synonym
   - weighted semantic match
3. Threshold policy:
   - High precision mode for auto-write.
   - Medium confidence stored as candidate tags in metadata.
4. De-duplicate by canonical tag key.

---

## Canonical relationship mapping

Scan edge names MUST map to canonical structural tags from
`reference/CANONICAL_TAG_TAXONOMY.md`:

| Scan relationship key | Canonical structural tag |
|---|---|
| `depends_on` | `dependency` |
| `supports` | `supports` |
| `contradicts` | `contradicts` |
| `tests` | `falsification` |
| `extends` | `enables` |
| `bridges` | `isomorphism` |
| `attacks` | `falsification` |

## Expansion rule when relationships are empty

If all scan relationship arrays are empty, expansion to master schema MUST still satisfy
L20 (minimum one edge). Emit this synthetic weak edge:

```yaml
edges:
  depends_on:
    - target: "UNRESOLVED_CONTEXT"
      relationship: "structurally"
      strength: "weak"
```

Also append a note that no explicit relationship was detected during scan.

## Acceptance Criteria

- Supports extended registry scale (target: 500+ entries).
- Emits invisible HTML tags per paragraph.
- Emits YAML summary with tags + codes + relationships.
- Preserves canonical tag compatibility with existing taxonomy.

