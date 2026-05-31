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

Some writing on the principles and patterns here:

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

[Something people actually use.](https://loganmies.com/blog/oyeme/dinner-table-driven-development/) 

Real-time translation and learning service for multilingual families.

Speaker diarization, family-scoped glossaries, locale-adaptive prompt registers, speculative translation, slow-speed TTS for language acquisition.

<details>
<summary>More details</summary>
<br>

```
┌─────────────────────────────┐
│             mic             │
└──────────────┬──────────────┘
               ▼
┌─────────────────────────────┐
│             VAD             │
│  (voice activity detection) │
└──────────────┬──────────────┘
         ┌─────┴─────┐
         ▼           ▼
┌─────────────┐ ┌──────────────┐
│     STT     │ │  speaker ID  │
│ (speech-to- │ │  (pgvector)  │
│    text)    │ └──────┬───────┘
└──────┬──────┘        │
       │               │
       ▼               ▼
┌─────────────────────────────┐
│          translate          │
└──────────────┬──────────────┘
               ▼
┌─────────────────────────────┐
│             TTS             │
│      (text-to-speech)       │
└─────────────────────────────┘
```

**Pipeline**

Provider-abstracted audio: VAD in-browser, speech-to-text, translation, text-to-speech with slow-speed playback for language acquisition. Echo suppression and speculative translation in the orchestrator.

**Diarization** (local mode)

ECAPA-TDNN embeddings in pgvector, cosine similarity matching. 

In local mode — multiple speakers sharing one device — identifies who is speaking to resolve translation direction. 

Overrides LLM language detection when the speaker's native language is known.

**Stack**

SvelteKit 2, Supabase, LiveKit WebRTC rooms. Operational MCP server: 24 tools across core, data, and infra.

</details>

---

### [`blog/`](https://github.com/factory2x/blog)

Part of the refinement loop. Built out of necessity — we needed somewhere to review and edit as a family.

[loganmies.com](https://loganmies.com).

<details>
<summary>More details</summary>
<br>

```
┌─────────────────────────────┐
│          Notion DB          │
│      (Site Mirror DB)       │
└──────────────┬──────────────┘
               ▼
┌─────────────────────────────┐
│           export            │
│    (hq-mcp render input)    │
└──────────────┬──────────────┘
         ┌─────┴─────┐
         ▼           ▼
┌─────────────┐ ┌──────────────┐
│   Python    │ │  Playwright  │
│   render    │ │  (OG cards)  │
└──────┬──────┘ └──────┬───────┘
       │               │
       ▼               ▼
┌─────────────────────────────┐
│         static HTML         │
│     (Cloudflare Pages)      │
└─────────────────────────────┘
```

**Pipeline**

Pages live in a Notion database. 

A Python pipeline exports, renders static HTML, and generates OG cards via Playwright.

</details>

---

### [`employment/`](https://github.com/factory2x/employment)

Self-reflection, discovery, opportunity tracking.

---

### [`.claude/`](https://github.com/factory2x/.claude)

Shared dotfiles for Claude Code — skills, hooks, and rules symlinked into `~/.claude/` on each machine. Being [folded into headquarters](https://github.com/factory2x/headquarters/issues/287).
