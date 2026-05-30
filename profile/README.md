# Factory X

A project ecosystem that builds and improves itself. The tooling repos improve the product repos, and building the products exposes what the tooling needs next.

Research → Build → Scale → Learn. Same loop since Chemical Engineering, different constraints.

---

## What's Inside

**headquarters** is the nervous system. A research pipeline crawls 30+ AI and infrastructure sources daily, scores and deduplicates findings against active projects, and writes structured intel into a governance layer. Artifact contracts enforce typed schemas on every issue, PR, and audit finding across the org — generators, parsers, validators. A FastMCP server (35 tools) gives agents typed access to all of it. Everything flows through here.

This is also where the patterns I bring back into my day job come from.

**oyeme** is [something people actually use](https://loganmies.com/blog/oyeme/dinner-table-driven-development/). Real-time interpreter for multilingual families — SvelteKit, Supabase, LiveKit, AssemblyAI, speaker identification. The only traditional product here so far. Building it is what exposes what the tooling needs next.

**blog** is sneaky. Looks like content — it's actually part of the refinement loop. Every post forces a review and explanation of what was built, and the output feeds back into the system. [loganmies.com](https://loganmies.com), static HTML, Cloudflare Pages.

**employment** is self-reflection and discovery, sitting here. The same research pipeline that improves the product also surfaces what's next.

**.claude** is org-level governance. Skills, enforcement hooks, deny rules — symlinked into the local machine on every checkout.

## Architecture

**Contracts.** Every artifact that flows between repos — issues, PRs, findings, audits, briefings — conforms to a typed schema with required sections, allowed values, and validation. The contracts ship as a Python package with generators, parsers, and round-trip tests. A malformed issue body fails validation before it's created. This is how five repos stay consistent without a monorepo.

**MCP.** Repos communicate through Model Context Protocol servers over stdio. `hq-mcp` exposes 35 tools (research pipeline reads/writes, editorial surface, GitHub operations, contract validation) and 9 Resources (the contracts themselves, queryable at runtime). `oyeme-mcp` exposes operational tools for the product. Agents get typed access to project state — no raw API calls, no screen-scraping.

**Governance.** An integration map defines issue routing, label state machines, and cross-repo permissions. Labels follow a state machine (`ready` → `in-progress` → `in-review` → `merged`) enforced by automation. When `hq_file_issue` is called, it reads the routing table, resolves the target repo, validates the body against the contract, and creates the issue with the correct labels. Field repos consume governance; they don't define it.

**Research pipeline.** The thing I couldn't do manually anymore. AI tooling moves too fast to track by reading — so the pipeline crawls 30+ sources daily (release feeds, changelogs, engineering blogs, docs updates), deduplicates against known findings, scores for relevance against active projects, and writes structured briefings. It runs autonomously on a schedule. The output feeds directly into architecture decisions and audit priorities across the ecosystem. I think this pattern — automated research as a first-class subsystem, not a side habit — is going to be table stakes for most development platforms soon.

## The Loop

Collect data around every operation. Tune upstream every time that data reveals issues. Discover and consider the latest tools available like it's the job. Collect scar tissue like it's gold. Compare notes. Iterate.

Constraints and tooling change. Engineering doesn't.

---

The longer versions: [Engineering](https://loganmies.com/blog/factoryx/engineering/) and [Dinner-Table-Driven Development](https://loganmies.com/blog/oyeme/dinner-table-driven-development/).
