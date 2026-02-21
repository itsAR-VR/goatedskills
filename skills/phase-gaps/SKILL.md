---
name: phase-gaps
description: RED TEAM the newest docs/planning/phase-N plan to find gaps/weak spots, refine the plan docs on disk, and surface below-84.7% confidence items as user questions.
---

# Instructions

Read all references in `references/` before using this skill.

## Original User Request Preservation

Preserve the exact prompt that started this phase and use it as the anchor for all RED TEAM judgments.

Before editing root plans:
1. Open `docs/planning/phase-<N>/plan.md`.
2. Keep the existing verbatim original request block at the top untouched.
3. If the block is missing, add it as the first section after the plan title using:
`## Original User Request (verbatim)` followed by the exact user text that initiated `/phase-plan`.
4. If the exact text is not available, pause and request it before patching the plan.

## Multi-Agent Awareness

**IMPORTANT:** Multiple agents may be working on different phases concurrently. RED TEAM analysis must account for:

1. **Cross-phase conflicts** — Files the plan touches may have been modified by other active phases
2. **Dependency races** — The plan may depend on work from another phase that isn't complete
3. **Stale assumptions** — Code referenced in the plan may have changed since planning

When RED TEAM reviewing, always:
- Scan the last 10 phases for file/domain overlaps
- Check git status for uncommitted changes from other agents
- Add coordination gaps to the RED TEAM findings if overlaps detected

See `08_MULTI_AGENT_COORDINATION.md` for detailed procedures.

## Signals

- The user says: "red team the plan", "find gaps", "weak spots", "stress test", "pre-mortem", "refine the newest phase plan", "audit the phase plan".
- A `docs/planning/phase-<N>/plan.md` exists and needs tightening before execution.
- The plan references repo code/paths and you must verify assumptions against repo reality.

## References

**Directory:** `references/`

- `01_INTENT.md`
- `02_PRECONDITIONS.md`
- `03_RULES.md`
- `04_PROCEDURE.md`
- `05_TEMPLATES.md`
- `06_RED_TEAM_CHECKLIST.md`
- `07_EDGE_CASES.md`
- `08_MULTI_AGENT_COORDINATION.md`
