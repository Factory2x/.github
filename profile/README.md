# Factory<sup>x</sup>

A project ecosystem that builds and improves itself.

The tooling repos improve the product repos, and building the products exposes what the tooling needs next.

```
┌──────────────┐
│   Research   │◀──────────╮
└──────┬───────┘           │
       │                 Learn
┌──────▼───────┐           │
│    Build     │◀──────────┤
└──────┬───────┘           │
       │                 Learn
┌──────▼───────┐           │
│    Scale     │───────────╯
└──────────────┘
```

Some writing on the principles here:

[loganmies.com/blog/factoryx/engineering/](https://loganmies.com/blog/factoryx/engineering/)

---

### [`headquarters/`](https://github.com/factory2x/headquarters)

The nervous system. Everything flows through here.

Research pipeline, artifact contracts, MCP servers, governance layer.

<details>
<summary>More details</summary>
<br>

**Research pipeline**

Crawls 30+ sources daily, deduplicates, scores against active projects, writes structured briefings. I think automated research as a first-class subsystem is going to be table stakes for most development platforms soon.

**Artifact contracts**

Typed schemas for every artifact between repos. Generators, parsers, validators, round-trip tests. Five repos stay consistent without a monorepo.

**MCP**

`hq-mcp`: 35 tools, 9 Resources. Typed access to project state over stdio.

**Governance**

Integration map, label state machines, cross-repo routing. Field repos consume governance; they don't define it.

</details>

---

### [`oyeme/`](https://github.com/factory2x/oyeme)

[Something people actually use.](https://loganmies.com/blog/oyeme/dinner-table-driven-development/) Real-time interpreter for multilingual families.
The only traditional product here so far — building it is what exposes what the tooling needs next.

<details>
<summary>More details</summary>
<br>

```
mic → VAD → STT → translate → TTS
              ↕
         speaker ID
        (pgvector)
```

**Pipeline**

Provider-abstracted audio: VAD in-browser, STT (AssemblyAI/Deepgram), translation (OpenAI), TTS with slow-speed "Learn" playback. Echo suppression and speculative translation in the orchestrator.

**Speaker ID**

ECAPA-TDNN embeddings (192-dim) stored in pgvector, cosine similarity matching. Custom inference server on Hetzner.

**Stack**

SvelteKit 2, Supabase (18 tables, RLS, Auth), LiveKit WebRTC rooms. `oyeme-mcp`: 24 tools across core, data, and infra.

</details>

---

### [`blog/`](https://github.com/factory2x/blog)

Part of the refinement loop. Every post forces a review of what was built, and the output feeds back into the system.
[loganmies.com](https://loganmies.com).

<details>
<summary>More details</summary>
<br>

```
Notion Site Mirror DB → hq-mcp export → Python render → static HTML
                                           ↳ Playwright → OG cards
```

**Pipeline**

Pages live in a Site Mirror DB. `hq-mcp` exports render-input JSON, a Python pipeline renders static HTML + Playwright-generated OG cards. No framework, no build step, EN/ES bilingual.

**Content**

Factory<sup>x</sup> engineering series (build, repeat, research, scale), Óyeme doctrine, airport connection plans, legal hub, pipeline showcase.

**Showcase**

`/src/` is an interactive Notion-style source table of every published page. Resizable columns, filterable by status/type/language.

</details>

---

### [`employment/`](https://github.com/factory2x/employment)

Self-reflection and discovery.
The same research pipeline that improves the product also surfaces what's next.

<details>
<summary>More details</summary>
<br>

**Find**

Crawls 35 sources daily (Greenhouse ATS, Ashby ATS, EU aggregators, remote boards, HN Who is Hiring). Sonnet-scored against a 45-skill candidate profile with evidence chains and per-variant weights.

**Resume**

Notion is the source of truth. Five pages in the Site Mirror DB, three role-shape variants (AI Infra, SRE, Product), PDF render from live Notion blocks via weasyprint.

**Tracking**

Opportunities as GitHub Issues with contract-enforced status machines. EU-focused: Dublin, Amsterdam, London.

</details>

---

### [`.claude/`](https://github.com/factory2x/.claude)

Org-level governance.
Symlinked into `~/.claude/` on every machine via bootstrap script.

<details>
<summary>More details</summary>
<br>

**Skills**

10+ reusable slash commands: spec writing and review, epic decomposition and execution, voice analysis (14-profile corpus), org-wide triage, blog drafting into Notion.

**Hooks**

Two PreToolUse enforcers: one blocks raw `gh issue` calls (forces writes through `hq-mcp`), one prevents field sessions from modifying org config.

**Promotion**

Field repos can shadow with local skills. Promotion path: local override → PR to `.claude` → headquarters merges.

</details>
