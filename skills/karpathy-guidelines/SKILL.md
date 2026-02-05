---
name: karpathy-guidelines
description: Karpathy-inspired behavioral guardrails to reduce common LLM coding mistakes (wrong assumptions, overengineering, drive-by edits, missing verification loops).
source: forrestchang/andrej-karpathy-skills
license: MIT
---

# Karpathy-Inspired Coding Guardrails

Apply these principles whenever this skill is invoked.

## 1) Think Before Coding

Don’t assume. Don’t hide confusion. Surface tradeoffs.

- State assumptions explicitly; if uncertain, ask.
- If multiple interpretations exist, present them — don’t pick silently.
- If a simpler approach exists, say so; push back when warranted.
- If something is unclear, stop; name what’s confusing and ask.

## 2) Simplicity First

Minimum code that solves the problem. Nothing speculative.

- No features beyond what was asked.
- No abstractions for single-use code.
- No “flexibility” or “configurability” that wasn’t requested.
- No error handling for impossible scenarios.
- If 200 lines could be 50, rewrite it.

Ask: “Would a senior engineer say this is overcomplicated?” If yes, simplify.

## 3) Surgical Changes

Touch only what you must. Clean up only your own mess.

When editing existing code:
- Don’t “improve” adjacent code, comments, or formatting.
- Don’t refactor things that aren’t broken.
- Match existing style, even if you’d do it differently.
- If you notice unrelated dead code, mention it — don’t delete it.

When your changes create orphans:
- Remove imports/variables/functions that your changes made unused.
- Don’t remove pre-existing dead code unless asked.

Test: Every changed line should trace directly to the user’s request.

## 4) Goal-Driven Execution

Define success criteria. Loop until verified.

- “Add validation” → write tests for invalid inputs, then make them pass.
- “Fix the bug” → write a test that reproduces it, then make it pass.
- “Refactor X” → ensure tests pass before and after.

For multi-step tasks, create a brief plan with verifiable checks using the $phase-plan $phase-gaps $phase-implement $phase-review family of skills:

1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]

