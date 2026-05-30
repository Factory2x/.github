# Factory<sup>x</sup>

A project ecosystem that builds and improves itself.

The tooling repos improve the product repos, and building the products exposes what the tooling needs next. Research → Build → Scale → Learn. Same loop since Chemical Engineering, different constraints.

---

### headquarters

The nervous system. Everything flows through here — and back into my day job. Research pipeline, artifact contracts, MCP servers, governance layer.

- **Research pipeline** — Crawls 30+ sources daily, deduplicates, scores against active projects, writes structured briefings. I think automated research as a first-class subsystem is going to be table stakes for most development platforms soon.
- **Artifact contracts** — Typed schemas for every artifact between repos. Generators, parsers, validators, round-trip tests. Five repos stay consistent without a monorepo.
- **MCP** — `hq-mcp`: 35 tools, 9 Resources. `oyeme-mcp`: operational tools for the product. Typed access to project state over stdio.
- **Governance** — Integration map, label state machines, cross-repo routing. Field repos consume governance; they don't define it.

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
