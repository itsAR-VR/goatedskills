# Procedure

Execute these steps literally, in order.

## Step 0 — Multi-Agent Conflict Check

Before creating any files, check for concurrent work:

1. **List the last 10 phases:**
   ```bash
   ls -dt docs/planning/phase-* | head -10
   ```

2. **For each recent phase**, quickly scan its `plan.md`:
   - Check the Purpose and Subphase Index
   - Identify any files or domains that overlap with your planned work

3. **Check git status:**
   ```bash
   git status --porcelain
   ```
   Note any uncommitted changes that might affect your work.

4. **If overlaps exist:**
   - Add a "Concurrent Phases" section to your plan's Context
   - Specify which phases are working on related areas
   - Note any coordination requirements (e.g., "Must complete after Phase 35")

## Step 1 — Create the phase directory

Create:

- `docs/planning/phase-<N>/`

## Step 2 — Write the root plan

Create and write:

- `docs/planning/phase-<N>/plan.md`

Use the template from `04_TEMPLATES.md` and fill it from the **current conversation**.

### Rules for Subphase Index

- Subtasks MUST be derived from the discussion (no "filler tasks").
- Prefer 2–6 subphases. Use more only if clearly justified by the discussion.
- Each subphase should be independently completable and produce a tangible output.

## Step 3 — Create subphase directories and scaffolds

For each listed letter in the Subphase Index:

Create:

- `docs/planning/phase-<N>/<letter>/`
- `docs/planning/phase-<N>/<letter>/plan.md`

Populate each subphase plan using the subphase template from `04_TEMPLATES.md`.

### Dependency rule

The output of `<N>/a/plan.md` becomes an input to `<N>/b/plan.md`, etc., in alphabetical order.

## Output checklist

Confirm on disk before finishing:

- `docs/planning/phase-<N>/plan.md` exists and is populated
- Each listed subphase directory exists
- Each subphase has a populated plan.md
- Root plan has a Subphase Index matching the created subphase folders
