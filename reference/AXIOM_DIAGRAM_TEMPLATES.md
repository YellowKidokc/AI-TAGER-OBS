---
title: "Axiom Diagram Templates — 10 Canonical Shapes"
date: 2026-03-07
classification: System
purpose: "Mermaid templates for visualizing each axiom type"
maps_to: CANONICAL_TAG_TAXONOMY.md
---

# Axiom Diagram Templates — 10 Canonical Shapes

Each shape corresponds to a content type in the Canonical Tag Taxonomy.
These templates can be used to auto-generate proof diagrams from axiom data.

| Shape | Tag | Callout | Key Question |
|-------|-----|---------|-------------|
| Axiom (A) | `axiom` | `[!axiom]-` | Can this be defeated? What does it open? |
| Definition (D) | `definition` | — | What does this mean and where does it go? |
| Equation (E) | `equation` | `[!equation]-` | What does each symbol represent? |
| Proposition (P) | `hypothesis` | `[!hypothesis]-` | How does this follow? What does it license? |
| Theorem (T) | `hypothesis`+`verified` | `[!hypothesis]-` | How is this proven? What does the proof open? |
| Corollary (C) | `hypothesis`+`dependency` | `[!hypothesis]-` | What does this add beyond its parent? |
| Boundary Condition (BC) | `falsification` | `[!falsification]-` | What satisfies this? What fails it? |
| Law Note (LN) | `isomorphism` | `[!isomorphism]-` | Where does established science say this? |
| Protocol (PROT) | `prediction` | `[!prediction]-` | What would actually break this? |
| Evidence (EV) | `evidence` | `[!evidence]-` | How strong is the support, honestly? |

See full Mermaid templates below.


---

## Shape 1 — AXIOM (A)
*Claim under pressure — what attacks it, what it withstands, what it opens.*

Structure: UPSTREAM → CLAIM → ATTACKS → HOLDS → ENABLES

Key elements:
- No upstream dependency for primitives
- Multiple attack vectors (steelmanned)
- Self-refutation trap demonstration
- Downstream enables list

## Shape 2 — DEFINITION (D)
*Term at center, components radiating, downstream uses anchoring.*

Structure: PARENT → TERM → COMPONENTS → USED_IN

## Shape 3 — EQUATION (E)
*Each variable gets its own node — domain, meaning, physical analogue.*

Structure: EQUATION → VARIABLES (each with domain) → MEANING → ENABLES

## Shape 4 — PROPOSITION (P)
*Inference path — what it follows from, what license it grants.*

Structure: FROM_AXIOMS → INFERENCE_STEP → PROPOSITION → GRANTS

## Shape 5 — THEOREM (T)
*Premises stack into conclusion, conclusion fans into corollaries.*

Structure: PREMISES → PROOF_STEP → THEOREM → COROLLARIES + IMPLICATIONS

## Shape 6 — COROLLARY (C)
*Parent → logical step → consequence → what it opens.*

Structure: PARENT_THEOREM → STEP → COROLLARY → NEXT + OBJECTION

## Shape 7 — BOUNDARY CONDITION (BC)
*What's constrained → requirement → what passes → what fails.*

Structure: SYSTEM → BC → WHY + PASS + FAIL → NEXT

## Shape 8 — LAW NOTE (LN)
*Known physics on one side, chi-framework on the other, mapping in middle.*

Structure: KNOWN_PHYSICS → MAPPING_BRIDGE → CHI_FRAMEWORK → WEIGHT

## Shape 9 — PROTOCOL (PROT)
*Theoretical claim → experiment → expected result → kill condition.*

Structure: CLAIM → EXPERIMENT → PREDICTED + KILL_CONDITION → HONEST_ASSESSMENT

## Shape 10 — EVIDENCE (EV)
*Claim → data → methodology → what it proves and what it doesn't.*

Structure: CLAIM → EVIDENCE → DATA + STRONG + WEAK → NET_WEIGHT

---

## INTEGRATION WITH PIPELINE

These templates connect to three systems:

1. **Semantic AI Plugin** — classifies content into these 10 types
2. **CSS Callouts** — renders inline collapsed versions in Obsidian
3. **Knowledge Graph** — stores as typed nodes with edges

When the Semantic AI identifies an axiom in a document:
- The YAML tag gets `axiom` from the taxonomy
- The callout gets `> [!axiom]- [ID] — [TITLE]`
- The Mermaid diagram can be auto-generated from Shape 1 template
- The knowledge graph gets a node of type Axiom with edges

Same content, four representations. One classification, four outputs.

---

*Source: Codex axiom diagram template system*
*Mapped to: CANONICAL_TAG_TAXONOMY.md (79 tags)*
*CSS: theophysics-content-callouts.css (10 types)*
