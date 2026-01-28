---
name: karpathy-guidelines
description: Apply Andrej Karpathy-inspired coding principles to reduce LLM mistakes. Use when starting complex tasks, before writing code, or when you notice over-engineering tendencies.
---

# Karpathy Coding Guidelines

Four principles to reduce common LLM coding mistakes, derived from observations about systematic pitfalls.

## 1. Think Before Coding

**Problem:** Wrong assumptions, hidden confusion, silent interpretation choices.

**Fix:**
- State assumptions explicitly before coding
- When multiple interpretations exist, present them—don't choose silently
- If something is confusing, stop and ask rather than guessing
- Push back if a simpler approach exists

**Self-check:** "Am I hiding any uncertainty?"

## 2. Simplicity First

**Problem:** Overcomplication, speculative features, premature abstraction.

**Fix:**
- Write minimum code that solves exactly what was requested
- No unrequested features, even "obviously helpful" ones
- No unnecessary abstractions or configurability
- No error handling for scenarios that can't happen

**Self-check:** "Would a senior engineer say this is overcomplicated?"

## 3. Surgical Changes

**Problem:** Scope creep, orthogonal modifications, "while I'm here" improvements.

**Fix:**
- Touch only what's necessary for the stated task
- Match existing code style exactly
- Don't refactor unrelated code or improve formatting elsewhere
- Only remove imports/variables YOUR changes made obsolete
- Leave pre-existing issues alone unless explicitly asked

**Self-check:** "Is every change directly required by the task?"

## 4. Goal-Driven Execution

**Problem:** Vague success criteria, unclear when "done", wasted iteration.

**Fix:**
- Transform requests into verifiable success criteria before starting
- Define what "working" looks like in testable terms
- Create verification steps you can execute
- Loop until criteria are met, not until it "feels done"

**Self-check:** "Can I verify success without asking the user?"

## When to Apply

- **Always:** Complex multi-file changes, unfamiliar codebases, ambiguous requests
- **Lighter touch:** Trivial tasks with obvious implementations
- **Critical:** When you notice yourself adding "helpful" extras

## Red Flags (Stop and Reconsider)

- Adding features not explicitly requested
- Creating abstractions "for future flexibility"
- Refactoring adjacent code "while you're there"
- Guessing at unclear requirements instead of asking
- Writing error handling for impossible scenarios
