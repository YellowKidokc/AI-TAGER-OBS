# THEOPHYSICS MASTER YAML SCHEMA v1.0

## Purpose

This reference defines the **layered frontmatter specification** for Theophysics notes, papers, axioms, protocols, and session logs. It is intended to be the authoritative source for YAML structure used by the Obsidian pipeline.

> "An axiom is not what you believe. It is what survives when everything else is dead."

---

## Layer Activation Rules

| Layer | Name | When Required |
|---|---|---|
| L1 | Identity | ALWAYS |
| L2 | Tree Position | ALWAYS (even when `q_level: null`) |
| L3 | Operation | Required for `axiom`, `theorem`, `paper`, `rebuttal`, `bridge` |
| L4 | Master Equation State | When χ variables are materially discussed |
| L5 | Physics Domains | When physics content is materially present |
| L6 | Theology | When theological concepts are developed |
| L7 | Trinity | When Trinitarian structure is materially engaged |
| L8 | Scripture & Consilience | When explicit scriptural argument/correlation is present |
| L9 | Experiments & Validation | When protocols, evidence, or tests are present |
| L10 | Mathematics | When equations/operators/proofs/formal definitions appear |
| L11 | Bridges & Isomorphisms | When cross-domain synthesis is explicitly claimed |
| L12 | Consciousness & AI | When consciousness or AI ontology is materially developed |
| L13 | Time & Causality | When temporal physics or causal structure is central |
| L14 | Principalities & Powers | When spiritual warfare dynamics are structurally engaged |
| L15 | Ethics & Moral Physics | When moral physics or virtue dynamics are central |
| L16 | Four Deviation Modes | When mode analysis is relevant |
| L17 | Boundary Conditions | When BCs are derived, tested, or mapped |
| L18 | Claims & Evidence | ALWAYS for `paper`, `axiom`, `theorem`, `hypothesis` |
| L19 | Classifier Hits | Auto-populated by machine classifier pipeline |
| L20 | Graph Edges | ALWAYS (minimum: one edge) |
| L21 | Worldview Tracking | When worldview survival analysis is present |
| L22 | Historical References | When key figures are materially engaged |
| L23 | Media & Attachments | When non-text content is present |
| L24 | Publication & Review | For papers in publication pipeline |
| L25 | Session Metadata | For conversation logs/session records |

---

## Full Schema (Canonical Template)

```yaml
schema_version: "theophysics-master-v1.0"

title: ""
uuid: ""
date_created: ""
date_modified: ""
authors:
  - "David Lowe"

doc_type: ""
status: ""
scope: ""
paper_number: ""
classification_tier: ""

discipline_weight:
  physics: 0.0
  theology: 0.0
  consciousness: 0.0
  mathematics: 0.0
  philosophy: 0.0
  information_theory: 0.0
  ethics: 0.0
  experimental: 0.0

confidence: ""
tags: []

file_management:
  publish_to_production: false
  publish_to_research: true
  publish_to_private: false
  publish_to_ai_commons: true

tree_position:
  q_level: null
  question_type: ""
  branch_taken: ""
  branch_answer: ""
  rival_branches:
    - branch_id: ""
      answer: ""
      death_condition: ""
      death_reason: ""
  propagation_status: ""
  propagation_failure_point: ""
  propagation_failure_reason: ""
  substrate_track: ""
  substrate_status: ""
  axiom_mapping: ""
  sys_mapping: ""

operation:
  type: ""
  op_target: ""
  op_result: ""
  op_vulnerability: ""
  op_unlocks: []

master_equation:
  form: "χ = ∭(G·M·E·S·T·K·R·Q·F·C)dxdydt"
  condensed: "χ(t) = σ(w₁G + w₂M + w₃E + w₄T + w₅K + w₆R + w₇Q + w₈F + w₉C - w₁₀S + Σaᵢⱼxᵢxⱼ)"
  dynamic: "dχ/dt = α·Constructive - β·Decoherent + γ·Coupling - δ·Drift"
  core_state:
    G: { active: false, weight: null, role: "" }
    M: { active: false, weight: null, role: "" }
    E: { active: false, weight: null, role: "" }
    S: { active: false, weight: null, role: "" }
    T: { active: false, weight: null, role: "" }
    K: { active: false, weight: null, role: "" }
    R: { active: false, weight: null, role: "" }
    Q: { active: false, weight: null, role: "" }
    F: { active: false, weight: null, role: "" }
    C: { active: false, weight: null, role: "" }
  coupling_terms: []
  coherence_direction: ""
  LLC_relevance: false
  LLC_form: "χ(t)(d/dt(G+M+E+S+T+K+R+Q+F+C))² - S·χ(t)"

physics:
  quantum_mechanics: { active: false, concepts: [] }
  relativity_cosmology: { active: false, concepts: [] }
  information_theory: { active: false, concepts: [] }
  consciousness_science: { active: false, concepts: [] }
  thermodynamics: { active: false, concepts: [] }
  field_theory: { active: false, concepts: [] }
  complexity_theory: { active: false, concepts: [] }

theology:
  active: false
  core_theology: []
  christology_salvation: []
  spiritual_dynamics: []
  ecclesiology: []
  eschatology: []

trinity:
  active: false
  trinitarian_dynamics: false
  father: { active: false, roles: [] }
  son: { active: false, roles: [] }
  spirit: { active: false, roles: [] }
  isomorphism_mapping:
    formal_triple: "Potential/Structure/Actualization"
    verified: false

scripture:
  active: false
  convergence_tags: []
  specific_texts: []
  scripture_refs: []
  EUID_refs: []
  prop_cosmos:
    active: false
    correlation_count: null
    sigma: null
    z_map: ""

experiments:
  active: false
  logos_protocols: []
  established_studies: []
  physiological_measures: []
  statistical_standards:
    significance_threshold: ""
    trial_count: null
    sigma_achieved: null
    pre_registered: false
    data_escrowed: false
    replication_status: ""
  falsification_criteria: []
  predictions: []
  prediction_status: []

mathematics:
  active: false
  equations_present: []
  formalisms: []
  operators: []
  variables_defined: []
  proofs_present: false
  derivations_present: false
  proof_type: ""

bridges:
  active: false
  cross_domain_bridges: []
  isomorphisms: []
  isomorphism_strength: ""
  bridge_survives_probe: null

consciousness_ai:
  active: false
  consciousness_concepts: []
  ai_concepts: []
  observer_state:
    consciousness_level: ""
    attention_type: ""
    intent_alignment: ""
    observer_type: ""
    phi_estimate: ""
    coupling_strength: ""

time_causality:
  active: false
  temporal_concepts: []
  causal_concepts: []

principalities_powers:
  active: false
  spiritual_agencies: []
  warfare_dynamics:
    mode_3_active: false
    attack_vector: ""
    defense_mechanism: ""
    ephesians_6_mapping: ""

ethics:
  active: false
  moral_physics: []
  sign_structure:
    sigma: null
    sign_change_mechanism: ""
    moral_conservation_eq: "dE/dt = -αD(t) + βC(Ψ,χ)"
    C_definition: ""
    beta_definition: ""
  virtue_measures: []
  ten_laws:
    active: false
    laws_engaged: []
    symmetry_pairs_active: []

deviation_modes:
  active: false
  M1_agentic: { active: false, status: "", description: "", remedy: "" }
  M2_entropic: { active: false, status: "", description: "", remedy: "" }
  M3_adversarial: { active: false, status: "", description: "", remedy: "" }
  M4_grace_attenuation: { active: false, status: "", description: "", remedy: "" }

boundary_conditions:
  active: false
  BC1: { active: false, derived_from: "Q7-B", status: "" }
  BC2: { active: false, derived_from: "T3.1", scripture_ref: "Ephesians 2:8-9", status: "" }
  BC3: { active: false, derived_from: "Q6-B", status: "" }
  BC4: { active: false, derived_from: "pending formal proof", honest_blank: true, status: "" }
  BC5: { active: false, derived_from: "Q6-B", scripture_ref: "Deuteronomy 30:19", status: "" }
  BC6: { active: false, derived_from: "Second Law requirement", status: "" }
  BC7: { active: false, derived_from: "Unitarity", status: "" }
  BC8: { active: false, derived_from: "Q10, BC5", scripture_ref: "Revelation 22:17", status: "" }

claims:
  primary_claims: []
  evidence:
    empirical: []
    logical: []
    scriptural: []
    mathematical: []
    testimonial: []
    consilience: []
  evidence_quality:
    strongest: ""
    weakest: ""
    overall_assessment: ""
  honest_blanks: []

classifier_hits: {}

edges:
  depends_on: []
  supports: []
  contradicts: []
  tests: []
  extends: []
  bridges: []
  attacks: []
  related_papers: []
  related_axioms: []
  related_boundary_conditions: []

worldview_tracking:
  active: false
  at_q_level: ""
  worldviews: {}

historical_references:
  active: false
  physicists: []
  philosophers: []
  theologians: []
  information_theorists: []

media:
  active: false
  images: []
  audio: []
  video: []
  pdf_attachments: []
  data_files: []
  visualizations: []

publication:
  active: false
  target_platform: ""
  series: ""
  paper_position: ""
  peer_review:
    stage: ""
    journal: ""
    submitted_date: ""
    reviewers: []
    review_outcome: ""
  adversarial_review:
    gpt_review: false
    gpt_review_file: ""
    fixes_applied: []
  abstract: ""
  keywords_publication: []

session:
  active: false
  session_title: ""
  session_date: ""
  ai_partner: ""
  model_version: ""
  session_type: ""
  what_discussed: []
  what_decided: []
  what_changed: []
  what_next: []
  files_touched: []
  breakthroughs: []

notes: |
  Freeform uncertainty log, rationale, and unresolved questions.
```

---

## Selection Rules (Decision Engine)

### Strength rubric

- **Strong**: Central to thesis/mechanism/argument → assign.
- **Medium**: Developed supporting concept → assign.
- **Weak**: Adjacent mention only → omit.

### Layer selection summary

- **L1/L2** are always present.
- **L3** only when the document actively grounds/chains/attacks/bridges/anchors/declares.
- **L4-L17** only when materially central.
- **L18** always for formal claims (`paper`, `axiom`, `theorem`, `hypothesis`).
- **L19** machine-populated.
- **L20** always (minimum one edge).
- **L21-L25** conditional.

### Pruning test

After generation: remove each assigned tag mentally and ask,
"Does the document lose essential identity/structure?"
If no, delete the tag.

### Propagation test

For tree-positioned claims, propagate branch logic through downstream Q-levels to Q12.
If the branch breaks, explicitly mark failure point and reason.

---

## Minimum Viable YAML (quick note)

```yaml
---
schema_version: "theophysics-master-v1.0"
title: "Note Title"
uuid: ""
date_created: ""
doc_type: note
status: draft
confidence: medium
tags: [pillar/physics]
tree_position:
  q_level: null
edges:
  depends_on:
    - target: "UNRESOLVED_CONTEXT"
      relationship: structurally
      strength: weak
  related_papers: []
notes: |
  Quick working note.
---
```

## Logos Paper starter block

```yaml
---
schema_version: "theophysics-master-v1.0"
title: "Paper Title"
uuid: ""
date_created: ""
doc_type: paper
status: draft
paper_number: P02
classification_tier: tier_2_derived
confidence: medium
tags: [pillar/physics, pillar/theology, logos/field]
tree_position:
  q_level: Q6
  question_type: Type1
  branch_taken: "Q6-B"
  propagation_status: propagates_cleanly
operation:
  type: CHAIN
  op_target: "Observer requirement"
  op_result: "Participatory universe established"
  op_vulnerability: "Decoherence-only interpretation"
  op_unlocks: ["Q7 terminal observer", "BC1 derivation"]
claims:
  primary_claims:
    - claim: "Observer participation is required for this branch."
      type: logical
      confidence: medium
      support: "Q6-B derivation chain"
      vulnerability: "Decoherence-only interpretation"
      testable: false
  evidence:
    logical: ["Q6-B derivation"]
  evidence_quality:
    strongest: "Branch-level logical derivation"
    weakest: "Interpretive dependence on measurement framing"
    overall_assessment: medium
  honest_blanks: []
edges:
  depends_on:
    - target: "P01"
      relationship: structurally
      strength: strong
  related_papers: ["P01", "P06"]
notes: |
  Keystone paper.
---
```
