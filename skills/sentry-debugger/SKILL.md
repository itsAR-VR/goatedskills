---
name: sentry-debugger
description: 'Triage and fix production errors using Sentry. Use when you need to pull live Sentry issues/events/stack traces, correlate them to code in the repo, and ship + verify fixes. Triggers include: Sentry issue, Sentry logs, event id, stack trace, @sentry/nextjs, captureException, startSpan, instrumentation-client, sentry.server.config, or sentry.edge.config.'
---

# Sentry Debugger

## Overview

Pull current Sentry issues and sample events, map stack traces to code, implement fixes with tests, and verify that errors stop regressing.

## Setup

- Set `SENTRY_AUTH_TOKEN` (required) to a Sentry API token with access to the target org/project (typically needs read access to issues/events).
- Set `SENTRY_ORG` and `SENTRY_PROJECT` (recommended) to default slugs.
- Optional: set `SENTRY_BASE_URL` (defaults to `https://sentry.io`) for self-hosted Sentry.

Example:

```bash
export SENTRY_AUTH_TOKEN="..."
export SENTRY_ORG="my-org"
export SENTRY_PROJECT="my-project"
export SENTRY_BASE_URL="https://sentry.io"  # optional
```

## Workflow

1. Pull the top issues from Sentry (by frequency or recency).
2. Inspect a sample event for one issue (exception value + stack trace + tags).
3. Locate the most relevant in-app frames in the repo, reproduce if possible, and fix.
4. Add a targeted regression test (or a small repro harness) and run the suite.
5. Deploy and verify in Sentry (new events stop, issue doesn’t regress).
6. If the fix benefits from better observability, add Sentry instrumentation (exceptions, spans, logs).

## Quick Start

List issues (defaults from env):

```bash
python3 scripts/sentry.py issues --limit 20
```

List only unresolved issues:

```bash
python3 scripts/sentry.py issues --query "is:unresolved" --limit 20
```

Inspect the latest event for an issue:

```bash
python3 scripts/sentry.py event-latest --issue-id 1234567890 --frames 16
```

Generate a Markdown report (useful for automations):

```bash
python3 scripts/sentry.py report --limit 15 > sentry-report.md
```

## Scripts

All scripts live in `scripts/`.

- `scripts/sentry.py issues`
- `scripts/sentry.py issue`
- `scripts/sentry.py event-latest`
- `scripts/sentry.py report`

Run `python3 scripts/sentry.py --help` for all options.

## References

- Read `references/nextjs-sentry.md` when instrumenting a Next.js app with `@sentry/nextjs` (exceptions, spans, logs, and init file locations).
