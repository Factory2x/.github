# Factory X

An engineering ecosystem built around one conviction: the best feedback loops run through people who care about the outcome.

Factory X is five repositories that share a governance layer, a research pipeline, and a single product at the center. The product is a real-time interpreter my family uses every day. Everything else exists to make that product better, faster, and more honest about what it does.

---

## The Product

**Óyeme** is a real-time translation app for multilingual families. My father-in-law speaks Spanish. I speak English. We've been in the same family for years. Óyeme sits between us — live transcription, real-time translation, speaker identification — so the conversation moves at the speed of the relationship, not the speed of someone's vocabulary.

The interesting part isn't the stack. It's the development process.

An idea my father-in-law dictates into his phone in Colombian coastal Spanish can become a merged pull request without me writing a single line of code. A database trigger fires an intake routine that reads the codebase, checks for duplicates, refines the raw idea into a spec, and opens a structured GitHub issue. A build routine picks it up, implements the change, verifies the build, and opens a PR with a preview deploy. My wife reviews it. I merge from my phone.

Sandra — my wife — outpaces me on submissions. The dinner table is the standup.

## The Ecosystem

| Repo | What it does |
|---|---|
| **oyeme** | The interpreter. SvelteKit, Supabase, LiveKit for WebRTC, AssemblyAI and Deepgram for transcription, OpenAI for translation, ECAPA-TDNN for speaker identification. Runs its own operational MCP server (24 tools). |
| **headquarters** | Governance hub. Typed artifact contracts — schemas for issues, PRs, findings, audits — with generators, parsers, and validators. Integration map. Label state machine. FastMCP server (35 tools). Not deployable; it's the source of standards. |
| **blog** | [loganmies.com](https://loganmies.com). Static HTML, no build step. Auto-deploys to Cloudflare Pages. Engineering notes and project doctrine. |
| **employment** | Job search as a system. Daily crawling across 11 ATS sources, model-scored matching, resume-as-code in Notion, opportunity tracking as GitHub Issues with contract-enforced status machines. |
| **.claude** | Org-level Claude Code configuration. Skills, enforcement hooks, deny rules. Symlinked into the local machine on every checkout. |

## How It Works

The repos don't just coexist — they enforce each other. `headquarters` defines the artifact contracts. Every issue, PR, and audit finding across the org conforms to typed schemas with validation. The daily research pipeline scans AI-engineering sources, scores findings against active projects, and writes structured intel into a governance database. Audits run against every repo on a schedule.

This isn't a monorepo and it isn't microservices. It's a governed ecosystem where the contracts are the architecture.

## Three Principles

**Friction belongs to the dev, not the user.**
If a family member's submission needs a tooling change to flow cleanly, that's a P0. The person at the dinner table should never know the pipeline exists.

**Pipelines, not wrappers.**
Don't build a thin shell over someone else's opinionated AI. Build a pipeline whose opinions are yours. Every routine in this ecosystem — intake, build, research, audit — is a pipeline with explicit contracts at each stage.

**Capability is logged, not claimed.**
PRs, audit findings, research briefings — the ledger is the reputation. If the system did something useful, there's an artifact that proves it.

---

The longer version: [Dinner-Table-Driven Development](https://loganmies.com/blog/oyeme-dinner-table-driven-development/).
