# AI-TAGER-OBS: Semantic AI Bundle (Final Claude Branch)

This branch contains a complete handoff bundle for the Obsidian Semantic AI plugin.

## Bundle Contents

- `plugin/`
  - Full working Semantic AI plugin (8 files)
  - `main.js` contains the active classification engine
  - Prompt packs updated in current cycle
- `reference/`
  - 6 canonical reference documents for tag meaning and display behavior
  - Includes taxonomy, framing, matrix, and CSS display rules
- `BUILD_SPEC.md`
  - Build instructions for the next implementation pass
  - Defines what already works, what to add, and what must remain unchanged

## Current State

Already working in this bundle:

1. Document-level classification
2. Prompt-driven tagging flow (standard + custom classifiers)
3. Mermaid output support
4. API connection path

## Next Build Targets

Implement only the insertion/output layer:

1. Paragraph-level tagging
2. Two output modes
3. Optional callout rendering
4. Compressed YAML frontmatter output

## Do Not Change

1. Existing classification logic
2. Prompt definitions and routing
3. API connection architecture

## Canonical Tag Source

Use `reference/CANONICAL_TAG_TAXONOMY.md` as the single source of truth for canonical tags.

## Validation Target

Primary test document: Turtles paper workflow.

