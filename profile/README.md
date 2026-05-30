# Factory<sup>x</sup>

A project ecosystem that builds and improves itself.

The tooling repos improve the product repos, and building the products exposes what the tooling needs next. Research → Build → Scale → Learn. Same loop since Chemical Engineering, different constraints.

---

### headquarters

The nervous system. Everything flows through here — and back into my day job.

- **Research pipeline** — AI tooling moves too fast to track by reading. The pipeline crawls 30+ sources daily, deduplicates against known findings, scores for relevance against active projects, and writes structured briefings on a schedule. The output feeds directly into architecture decisions and audit priorities. I think automated research as a first-class subsystem is going to be table stakes for most development platforms soon.

- **Artifact contracts** — Every artifact between repos (issues, PRs, findings, audits, briefings) conforms to a typed schema. Generators, parsers, validators, round-trip tests. A malformed issue body fails before it's created. This is how five repos stay consistent without a monorepo.

- **MCP** — Repos communicate through Model Context Protocol servers over stdio. `hq-mcp`: 35 tools, 9 Resources. `oyeme-mcp`: operational tools for the product. Typed access to project state — no raw API calls.

- **Governance** — Integration map defines routing, label state machines, cross-repo permissions. `hq_file_issue` reads the routing table, validates the body against the contract, creates the issue with correct labels. Field repos consume governance; they don't define it.

---

### oyeme

[Something people actually use.](https://loganmies.com/blog/oyeme/dinner-table-driven-development/) Real-time interpreter for multilingual families. SvelteKit, Supabase, LiveKit, AssemblyAI, speaker identification. The only traditional product here so far.

### blog

Part of the refinement loop. Every post forces a review of what was built, and the output feeds back into the system. [loganmies.com](https://loganmies.com), static HTML, Cloudflare Pages.

### employment

Self-reflection and discovery. The same research pipeline that improves the product also surfaces what's next.

### .claude

Org-level governance. Skills, enforcement hooks, deny rules — symlinked into the local machine on every checkout.

---

Collect data around every operation. Tune upstream every time that data reveals issues. Discover and consider the latest tools available like it's the job. Collect scar tissue like it's gold. Compare notes. Iterate.

Constraints and tooling change. Engineering doesn't.

The longer versions: [Engineering](https://loganmies.com/blog/factoryx/engineering/) and [Dinner-Table-Driven Development](https://loganmies.com/blog/oyeme/dinner-table-driven-development/).
