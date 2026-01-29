# Phases / Milestones Migration Plan

## Goal
Move from duplicated phase/milestone documents to a structure where:
- Phases describe the operating mode (mindshift, always-on objectives).
- Milestones define target states that reduce uncertainty and seed tasks.

## Current State (problem summary)
- Phases and milestones in `actionables/` are 1:1 duplicates in name and content.
- Phase docs read like milestone specs (objectives and deliverables are identical).
- This blurs process guidance and target-state checkpoints, making task creation
  less intentional.

## Target State (desired structure)
- Fewer, broader phases that describe how we work.
- Multiple milestones per phase, each a distinct target state.
- Milestones remain the only source for linear task breakdowns.
- `actionables/STATE.md` tracks active phase and current milestone explicitly.

## Proposed Phase Set (example)
- Phase A: Direction & Constraints (decision-making, policy, guardrails)
- Phase B: Build & Integrate (scaffold, templates, seams, fixtures)
- Phase C: Validate & Deliver (validation, guardrails enforcement, demo package)

## Proposed Milestone Mapping (using existing content)
- Phase A:
  - Milestone: Decisions & Policy Baseline (target state, renamed if needed)

- Phase B:
  - Milestone: Repo Scaffold & Templates Ready
  - Milestone: Integration Seams & Fixtures Validated

- Phase C:
  - Milestone: Guardrails Enforced & Validation Passing
  - Milestone: Demo Delivery Packaged & Reproducible

If we want more granular insight gates, split the first milestone into:
- Packaging model locked + artifact location agreed
- Base tag stability policy approved
- Demo documentation baseline complete

## Migration Steps

1) Define phase intent (no tasks)
- Update each phase `index.md` to include:
  - Type, focus, always-on objectives, entry/exit criteria, cadence.
- Remove or soften any acceptance-criteria language from phase docs.

2) Refactor milestones into target states
- Rename milestones to describe the achieved state (not the theme).
- Add a short "Questions answered / uncertainty reduced" section.
- Keep acceptance criteria and linear task breakdowns in milestones only.

3) Update references and indices
- Update `actionables/STATE.md` to list:
  - Active phase (mode)
  - Current milestone (target state)
- In phase docs, list included milestones.
- In milestone frontmatter, add `phase` reference (id or canonical name).

4) Fix dependency chains
- Rewire dependencies among milestones (not phases).
- Keep phase ordering as a high-level guide, not a dependency gate unless required.

5) Align agent/tooling references (if needed)
- Scan `.opencode/` prompts and plans that reference phases by name and update
  to the new phase names.
- Preserve milestone IDs to avoid breaking links.

## Validation Checklist
- No phase has a linear task breakdown.
- Every milestone has acceptance criteria and a task breakdown.
- Phase names are distinct from milestone names.
- `actionables/STATE.md` reports one active phase and one current milestone.

## Rollout Notes
- Prefer renaming content in place to preserve file history and links.
- If a milestone is split, keep the original as a wrapper with links to the new
  milestone docs until all references are updated.
