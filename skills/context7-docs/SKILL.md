---
name: context7-docs
description: Use Context7 MCP to fetch up-to-date documentation (and code examples) whenever questions involve platform/library usage or documentation (e.g., Supabase, Vercel, Next.js).
source: local
---

# Context7 Docs First

This skill keeps platform/library answers grounded in current documentation by using the Context7 MCP tools before responding.

## When to Use

Use this skill when any of the following are true:
- The user mentions documentation (docs, “according to docs”, “what does the docs say”, “verify in docs”, etc.).
- The user is using or integrating a platform/library where API details change (e.g., Supabase, Vercel/Next.js, Stripe, Cloudflare, AWS SDKs).
- The user asks for “latest”, “current”, “recommended”, “supported”, or version-sensitive behavior.

## Workflow (Do This First)

1. **Identify the primary platform/library** involved (and version, if mentioned).
2. **Resolve the Context7 library ID**:
   - Call `mcp__context7__resolve-library-id` with `libraryName` set to the platform/library (examples: `supabase`, `next.js`, `vercel`).
   - Prefer official docs sources and the closest match to the user’s intent.
3. **Query the docs for the specific task**:
   - Call `mcp__context7__query-docs` using the resolved `libraryId`.
   - Make the query concrete: include the feature name, exact API/method names, error messages, versions, and constraints.
4. **Answer using the retrieved docs**:
   - Provide the implementation steps or code based on the docs results.
   - If docs are ambiguous or incomplete, say what is unclear and ask a targeted follow-up question.

## Guardrails

- **Always resolve before query** (unless the user already provided a valid `libraryId` like `/org/project`).
- **Stay within tool limits**: max 3 Context7 calls per user question.
- If there are **multiple platforms**, pick the one that is most load-bearing, or ask the user which one to prioritize.
- If Context7 has **no relevant coverage**, say so and ask for:
  - the exact doc page/link, or
  - the relevant snippet, or
  - the exact product/version (so you can try a better `libraryName`).

## Common Starting Points (Library Names)

- Supabase: `supabase`, `supabase-js`, `postgres`
- Vercel/Next.js: `next.js`, `vercel`
- Auth: `next-auth`, `auth.js`
- DB/ORM: `prisma`, `drizzle`, `sequelize`

## Trigger Examples

- “What does the Supabase docs recommend for RLS on multi-tenant tables?”
- “Can you check the latest Next.js middleware docs for redirects?”
- “How do I set environment variables on Vercel?”
- “Is this API still supported in the current version?”

