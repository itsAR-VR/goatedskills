---
name: live-env-playwright
description: "Use when asked to check the live app, run QA, verify deploy, or log in and test. Hard constraint: live-only (never localhost); always test against NEXT_PUBLIC_APP_URL using Playwright MCP."
---

# Live Env Playwright (MCP)

Use Playwright **MCP** tools to smoke-test the deployed app.

## Hard constraints

- Never run or suggest local servers (`pnpm dev`, `next dev`, `localhost`, `127.0.0.1`).
- Always operate against `NEXT_PUBLIC_APP_URL`.
- Read creds from env vars only: `SEED_ADMIN_EMAIL`, `SEED_ADMIN_PASSWORD`.
- Never print secrets from .env.local other than the `SEED_ADMIN_EMAIL`, `SEED_ADMIN_PASSWORD` these must be printed when we are logging in.
- Prefer UI login flow (not direct API auth) unless user explicitly requests API-only.
- No destructive actions (no deletes, no DB resets, no seed scripts) unless user explicitly asks.

## Quick checklist (default assertions)

- `/login` renders and accepts credentials.
- `/app` redirects to `/login` when logged out; does **not** redirect when logged in.
- `/app/calls` loads (no redirect back to `/login`).
- Authenticated API health:
  - `GET /api/me` returns `200`.
  - `GET /api/admin/storage` returns `200`.

If your app uses different endpoints, ask the user for the correct paths before loosening assertions.

## Standard workflow (UI login)

1. Verify env vars exist (do not echo values):
   - `NEXT_PUBLIC_APP_URL`, `SEED_ADMIN_EMAIL`, `SEED_ADMIN_PASSWORD`
2. `mcp__playwright__browser_navigate` to `NEXT_PUBLIC_APP_URL`.
3. Navigate to `NEXT_PUBLIC_APP_URL + '/app'` and verify redirect behavior when logged out.
4. Navigate to `NEXT_PUBLIC_APP_URL + '/login'`.
5. Fill:
   - `#email` = `SEED_ADMIN_EMAIL`
   - `#password` = `SEED_ADMIN_PASSWORD`
   - Click “Sign in”
6. Follow user instructions, typically going through all pages and verifying features are working as per the plan.
7. Collect diagnostics:
   - `mcp__playwright__browser_console_messages`
   - `mcp__playwright__browser_network_requests` (summarize failures; strip secrets)

## Artifacts on any failure

Capture and report filenames:
- Full-page screenshot: `mcp__playwright__browser_take_screenshot` (fullPage).
- Accessibility snapshot: `mcp__playwright__browser_snapshot`.
- Console/page errors: `mcp__playwright__browser_console_messages`.
- Network failure summary (status + URL only; no headers/tokens).

If the Playwright MCP saves artifacts into a temp output directory, copy them into the repo under `artifacts/live-env-playwright/` so they’re easy to find.

## Troubleshooting

- If Playwright MCP errors with “Transport closed” / CDP timeouts: restart Codex CLI session to reload MCP, then retry.
- If auth fails: confirm `SEED_ADMIN_EMAIL`/`SEED_ADMIN_PASSWORD` match an existing Supabase Auth user and that email/password auth is enabled.
