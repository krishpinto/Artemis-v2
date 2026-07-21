# Artemis Roadmap — v1.x incremental track

Status: accepted 2026-07-19. This is the execution plan. `architecture.md` is the
long-term map; this roadmap ships its first vertical slice without a rewrite.

Goal: a product whose usefulness is provable by real users — issues from
strangers, a 60-second demo, people who vouch for it. Not download counts.

## Phase 1 — The contract (weeks 1–3)
- `artemis init`: scan repo evidence (package.json, prisma/drizzle config,
  `.env.example`) and propose an `artemis.yml`.
- `artemis up` deploys from the committed `artemis.yml` instead of the
  interactive picker. Existing K8s runtime and TUI stay.
- GitHub Actions CI, ~10 tests on scanner + config parsing, tagged release
  with changelog.

## Phase 2 — Trust (weeks 4–6)
- Protocol-level readiness: Postgres accepts a connection, Redis answers PING,
  MinIO health endpoint responds. "Ready" means usable, not "pod exists".
- Diagnostics that explain failures ("port 5432 already owned by another
  process"), not just report them.
- `artemis env`: print or write the exact connection env vars.

## Phase 3 — The differentiator (weeks 7–10)
- Read-only MCP server against existing code: `get_status`, `get_endpoints`,
  `read_logs`, `diagnose`.
- Pitch: "the local dev stack your coding agent can see."

## Phase 4 — Distribution (weeks 8–16, overlaps)
- README rewritten around one 60-second demo GIF: `npx artemis-cli init &&
  artemis up` in a real Next.js + Prisma repo.
- Launch: Show HN, r/node, r/kubernetes, dev.to write-up, LinkedIn.
- 5 known users (Ethan, classmates, Infinity Pool colleagues) asked to use it
  and file issues.
- Success metric: 10 issues from strangers + 3 people who would vouch for it.

## Non-goals for this track
- No monorepo restructure, no control API daemon, no Compose provider, no
  policy/audit engine, no dashboard rewrite. Those live in `architecture.md`
  and are earned by adoption, not built on spec.
- Budget: 2–3 hrs/week. Any phase that stops fitting gets cut, not crammed.
