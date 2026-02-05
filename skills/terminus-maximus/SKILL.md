---
name: terminus-maximus
description: Relentless end-to-end execution loop for coding tasks. Always resume the latest docs/planning/phase-N (highest N unless user specifies) and keep working until the phase is complete or truly blocked. On every turn, update phase docs with progress and run a RED TEAM pass (phase-gaps) to surface next steps, assumptions, and targeted user questions. Use when the user says "Terminus Maximus", "Ralph Loop", "never stop", "keep going", "continue", or wants full completion with explicit blocker handling and phase-plan/gaps/implement/review discipline.
---

# Instructions

Read all references in `references/` before using this skill.

## Companion Skills (Mandatory)

Always apply these skills as **subroutines** of $terminus-maximus. They exist to improve the Terminus Maximus loop (clarity, correctness, verification) and should not replace it. Default output format remains Terminus Maximus (templates + phase doc updates) unless the user explicitly asks for a different format.

1. $karpathy-guidelines — Apply at the start of every turn to keep changes minimal, assumptions explicit, and verification tight.
2. $recursive-reasoning-operator — Use its PLAN/LOCATE/EXTRACT/SOLVE/VERIFY/SYNTHESIZE workflow whenever you are making claims or decisions grounded in docs/planning, references, or other provided materials. Then synthesize back into the Terminus Maximus progress updates + user response skeleton.
3. $context7-docs — If documentation is mentioned or platform/library behavior is version-sensitive, pull the relevant docs via Context7 MCP (resolve then query) before answering. Funnel findings back into Terminus Maximus updates; stay within Context7 call limits.
4. $skill-creator — If the task involves creating or updating any skill (including this one), follow its creation/update and validation steps.

## Multi-Agent Awareness

**IMPORTANT:** Multiple agents may be working on different phases concurrently. Every turn:

1. Run `git status` and note unexpected changes
2. Scan the last 10 phases for overlaps with files you will touch
3. Document any coordination conflicts in the active subphase Output

See `07_MULTI_AGENT_COORDINATION.md` for procedures.

## Signals

- The user says "Terminus Maximus" / "Ralph Loop" / "never stop" / "keep going"
- The user wants you to finish the task fully, not partially
- The work is tracked via `docs/planning/phase-N/`

## References

**Directory:** `references/`

- `01_INTENT.md`
- `02_PRECONDITIONS.md`
- `03_RULES.md`
- `04_PROCEDURE.md`
- `05_TEMPLATES.md`
- `06_EDGE_CASES.md`
- `07_MULTI_AGENT_COORDINATION.md`
