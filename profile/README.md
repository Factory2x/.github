# Factory X

A project ecosystem that builds and improves itself. The tooling repo improves the product repo, and building the product exposes what the tooling needs next.

Research → Build → Scale → Learn. Same loop since Chemical Engineering, different constraints.

---

## What's Inside

**headquarters** is the nervous system. A research pipeline crawls 30+ AI and infrastructure sources daily, scores and deduplicates findings against active projects, and writes structured intel into a governance layer. Artifact contracts enforce typed schemas on every issue, PR, and audit finding across the org — generators, parsers, validators. A FastMCP server (35 tools) gives agents typed access to all of it. Everything flows through here.

This is also where the patterns I bring back into my day job come from. The research pipeline is the standout: curated source tables, model-tiered processing (Sonnet for collection, Opus for synthesis), observability everywhere, daily briefings. It's how I stay current and how the system stays honest.

**oyeme** is [something people actually use](https://loganmies.com/blog/oyeme/dinner-table-driven-development/). Real-time interpreter for multilingual families — SvelteKit, Supabase, LiveKit, AssemblyAI, speaker identification. The only traditional product here so far. Building it is what exposes what the tooling needs next.

**blog** is sneaky. Looks like content — it's actually part of the refinement loop. Every post forces a review and explanation of what was built, and the output feeds back into the system. [loganmies.com](https://loganmies.com), static HTML, Cloudflare Pages.

**employment** is self-reflection and discovery, sitting here. The same research pipeline that improves the product also surfaces what's next.

**.claude** is org-level governance. Skills, enforcement hooks, deny rules — symlinked into the local machine on every checkout.

## The Loop

Collect data around every operation. Tune upstream every time that data reveals issues. Discover and consider the latest tools available like it's the job. Collect scar tissue like it's gold. Compare notes. Iterate.

Constraints and tooling change. Engineering doesn't.

---

The longer versions: [Engineering](https://loganmies.com/blog/factoryx/engineering/) and [Dinner-Table-Driven Development](https://loganmies.com/blog/oyeme/dinner-table-driven-development/).
