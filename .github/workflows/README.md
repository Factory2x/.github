# Reusable org workflows

Org-owned CI/CD flows; every repo's workflow files are thin callers
(`uses: factory2x/.github/.github/workflows/<name>.yml@main` +
`secrets: inherit`). The fleet's CI opinions — self-hosted always, no
hosted minutes, no npm Actions cache on a warm box — live here once
instead of per-repo.

| Flow | Shape | Callers state |
|---|---|---|
| `chat-gates.yml` | hat-parity + hygiene, the stamped context's merge gate | nothing — the script paths are the stamp's convention |
| `web-ci.yml` | npm ci → build → check → optional tests | node version, client-public build env, test command |
| `pages-deploy.yml` | optional build → wrangler pages deploy | build env, the exact deploy line, account id (or secret) |
| `uv-tests.yml` | uv sync → pytest → optional extra suite | sync scope, extra suite |
| `origin-check.yml` | PR body carries the `hq:origin` provenance stamp (agent-conduct §10) | nothing — skips on non-PR events |

Referenced `@main`, deliberately: these are governance, not artifacts —
they move with the org, and a fix here propagates without bump PRs.
Repos whose CI carries bespoke machinery (fitness's automerge chain,
ui's token suite, ui-swift's module gates) keep it repo-local; shared
flows are for shared shapes, and per-repo jobs and triggers compose
around them freely.

Rules that bind every flow in this directory:

- `runs-on: self-hosted`, hardcoded. No runner input exists, so a caller
  cannot flip a job back to hosted (HQ#528).
- This repo is PUBLIC. No secret, token, or private URL is ever written
  here; secrets arrive from callers via `secrets: inherit`.
- **`inherit` misses ORG-level secrets at required-secret validation** —
  the call fails with "Secret X is required, but not provided" before any
  step runs. A caller whose secret lives at the org level maps it
  explicitly (`secrets: {X: ${{ secrets.X }}}`), which evaluates in the
  caller's context where org secrets resolve. Repo-level secrets work
  with `inherit` as-is.
- Gate logic stays one-homed in the calling repo's `scripts/` — a flow
  calls a script and nothing more, so gates run identically by hand.
