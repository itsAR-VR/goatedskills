---
name: phase-plan
description: Convert the current conversation into a new numbered planning phase; creates docs/planning/phase-N/ with root and subphase plan.md scaffolds.
---

# Instructions

Read all references in `references/` before using this skill.

## Multi-Agent Awareness

**IMPORTANT:** Multiple agents may be working on different phases concurrently. Before creating a new phase:

1. **Scan the last 10 phases** for potential file/domain overlaps
2. **Check git status** for uncommitted changes from other agents
3. **Document dependencies** on other active phases in your plan

If you detect overlap with an active phase, note it in your plan's Context section and specify how the phases should coordinate.

See `06_MULTI_AGENT_COORDINATION.md` for detailed procedures.

## Signals

- The conversation reaches a new direction or architecture decision
- The user says "create a phase plan", "materialize this", "capture this into planning"
- A "we should plan this" moment where structure would help

## References

**Directory:** `references/`

- `01_INTENT.md`
- `02_PRECONDITIONS.md`
- `03_PROCEDURE.md`
- `04_TEMPLATES.md`
- `05_EDGE_CASES.md`
- `06_MULTI_AGENT_COORDINATION.md`
