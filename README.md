# Connected Thinking

An opinionated Obsidian vault + Claude Code harness for a single second brain across learning, life, and work — with local AI built in.

Clone, open, and skip the six months most people spend tweaking their setup.

---

## Is this for you?

Most Obsidian starters are either heavy on theory and light on tooling (Zettelkasten, LYT, PARA), or built around a single use case (journaling, research). This one's for people whose brain doesn't split cleanly between domains, who want one vault for everything, and who want AI assistance on their own notes without uploading anything to a SaaS.

You'll get the most out of it if you:

- Take notes across multiple life domains and want to draw connections between them
- Prefer markdown files on your disk over cloud-locked block editors
- Want local AI search, and optionally a Claude Code agent that can edit the vault directly
- Are comfortable in a terminal

If you only journal, or only research, this is overkill.

---

## What's inside

| Layer | What ships |
|---|---|
| **Vault structure** | Six numbered top-level folders (`0. Notes` → `5. Experiments`) that sort predictably, plus a `Templates/` folder |
| **Templates** | Subject, Resource, Definition, Book Analysis — frontmatter-driven, with embedded Dataview queries so notes self-organize as you tag and link them |
| **Theme** | Cupertino, pre-bundled — SF Pro fonts, calm muted accents, ribbon hidden |
| **Plugins** | Six community plugins pre-enabled in the config: Dataview, Templater, Calendar, Smart Connections, Style Settings, Spaced Repetition |
| **Local AI search** | Smart Connections — local embeddings (TaylorAI/bge-micro-v2), optional Ollama chat over your notes |
| **AI authoring** | Claude Code harness with five Obsidian-aware skills (defuddle, json-canvas, obsidian-bases, obsidian-cli, obsidian-markdown) plus a custom book-analyst skill |

What you **don't** get: notes. The vault ships empty.

---

## How it compares

| | Connected Thinking | PARA | Zettelkasten / LYT | Notion |
|---|---|---|---|---|
| **Organization** | Numbered domain folders | Projects / Areas / Resources / Archives | Atomic notes + tag graph | Nested pages + databases |
| **Templates** | Templater + Dataview, frontmatter-driven | Manual | Manual | Native templates |
| **AI search** | Local embeddings | None | None | Cloud (Notion AI) |
| **AI authoring** | Claude Code with vault-aware skills | None | None | Notion AI (chat only) |
| **Data ownership** | Markdown on your disk | Markdown | Markdown | Cloud-hosted |
| **Setup time** | 10 min | DIY | DIY | None — but locked in |

---

## Why it works

The vault isn't designed around a productivity philosophy. It's designed around how memory actually works.

### The brain doesn't store information in folders

Long-term memory is associative. You don't retrieve a fact by remembering its location — you retrieve it by following links from related concepts (*spreading activation* through semantic networks). A folder hierarchy fights that. Every note has exactly one home, and you have to remember where you put it.

This vault prioritizes links and tags over nesting. The numbered folders are a coarse domain split, not a taxonomy. The real structure emerges through `[[wikilinks]]`, `#tags`, and Dataview queries — closer to how associative recall actually works.

### Cognitive offloading

Working memory holds about four items at once (Cowan, 2001). Anything past that is gone unless it's externalized. The *extended mind* thesis (Clark & Chalmers, 1998) argues that external tools function as genuine extensions of cognition, not just storage. A well-designed vault is a literal extension of your working memory.

The templates are deliberately minimal: frontmatter, a Dataview query, blank space. They remove the *decision* of how to structure a note so working memory goes to the content, not the container.

### Spaced retrieval

The Spaced Repetition plugin turns marked passages in your own notes into flashcards scheduled along the Ebbinghaus forgetting curve. You don't maintain a separate deck — you review your own writing on the schedule that produces durable memory.

### Dual coding

Paivio's dual coding theory: information encoded both verbally and visually has more retrieval pathways than either alone. Obsidian's graph view, Canvas, and Bases give you visual encodings of the same notes you wrote linearly. Same idea, two encodings, more hooks for recall.

---

## Built for neurodivergent thinking

External scaffolding helps any brain, but it's load-bearing for brains with executive function differences. The choices here are shaped by what helps in practice.

### ADHD

| Challenge | How the vault helps |
|---|---|
| Working memory limits | Frontmatter and templates externalize structure so you don't hold it in your head |
| Choice paralysis on a blank page | Templates pre-decide the fields, removing the "what does this note need" friction |
| Object permanence — out of sight, out of mind | Smart Connections finds the note you forgot existed via semantic similarity, not exact recall |
| Hyperfocus tangents getting lost | Capture into `0. Notes/` without thinking, retrieve later by topic instead of by location |
| Time blindness | Calendar plugin + daily notes give time a visual anchor |
| Decision fatigue on filing | Six numbered domain folders, not sixty arbitrary ones |
| Task switching cost | Single vault means no app/context switch between learning, life, and work |

### Autism

| Strength or preference | How the vault helps |
|---|---|
| Systemizing and pattern recognition | Graph view and Dataview surface relationships you can see at a glance |
| Predictability and consistent structure | Templates produce identical-shaped notes; folder convention is fixed |
| Deep focus on special interests | Domain folders contain rabbit holes without polluting other areas |
| Sensory regulation | Cupertino is muted, ribbon hidden; no notifications, no social feed, no algorithm |
| Literal interpretation | Frontmatter fields are explicit and named — no guessing at intent |

### Dyslexia

| Challenge | How the vault helps |
|---|---|
| Difficulty retrieving by exact spelling | Smart Connections searches by meaning — type roughly what you remember |
| Visual fatigue with dense text | SF Pro typography + Cupertino spacing; Style Settings exposes font-size and line-height controls |
| Sequential reading load | Graph view and Canvas let you navigate spatially instead of through long lists |

Neurodivergence isn't a deficit to be patched. This vault doesn't try to make any brain work like a neurotypical one — it removes the parts of conventional note-taking that punish those brains for being themselves. It's a tool, not a treatment. If you're struggling, talk to a clinician.

---

## Setup

### Prerequisites

- [Obsidian](https://obsidian.md/) (desktop)
- Optional: [Claude Code](https://claude.com/claude-code) for the AI harness
- Optional: [Ollama](https://ollama.com/) for Smart Connections local chat

### Steps

1. **Clone**

   ```sh
   git clone https://github.com/vokal-jack/connected-thinking ~/Documents/connected-thinking
   ```

2. **Open the vault**

   Obsidian → *Open folder as vault* → `connected-thinking/brAIn/`.

3. **Install community plugins**

   Settings → Community plugins → turn off Restricted mode. Install all six. They auto-enable from the vault config:

   - Dataview
   - Templater
   - Calendar
   - Smart Connections
   - Style Settings
   - Spaced Repetition

4. **Wire up the templates folder**

   - Settings → Templates → Template folder location: `Templates`
   - Settings → Templater → Template folder location: `Templates`

5. **Activate the theme**

   Settings → Appearance → Theme → Cupertino. (Already bundled.)

6. **(Optional) Claude Code**

   `cd ~/Documents/connected-thinking && claude .` — the harness loads `.claude/settings.local.json` and resolves skills via `skills-lock.json` automatically.

---

## Daily use

### The folder model

| Folder | Use |
|---|---|
| `0. Notes/` | Unsorted / inbox |
| `1. Education/` | Subjects, definitions, learning resources |
| `2. Life/` | Personal goals, inspiration, skills, reading |
| `3. Ventures/` | Business and entrepreneurial tracking |
| `4. Archives/` | Old materials |
| `5. Experiments/` | Sandbox |
| `Templates/` | Templater source files |

Numbering forces a stable sort order without depending on Obsidian's per-folder ordering UI. Frontmatter conventions for each note type are documented in [`CLAUDE.md`](./CLAUDE.md).

### How notes self-organize

The Definition and Resource templates ship with a Dataview query like:

```dataview
list
from [[]] and #definition
```

`[[]]` resolves to the current note, so any note that links here and is tagged `#definition` shows up automatically. Link a definition once when you create it; the parent subject note picks it up forever after. No manual indexing.

### Working with the AI layer

| Tool | When you'd reach for it |
|---|---|
| **Smart Connections** (in Obsidian) | "Find the note I wrote about this topic" — even when you can't remember the title or exact words |
| **Claude Code** (terminal) | "Write a new definition note from this article" / "Reorganize my reading list" / "Summarize what I learned about X across these five notes" |

Both are optional. The vault works fine as a plain Obsidian setup if you skip them.

---

## Customizing

This is a starter, not a framework. Rename `brAIn/`, swap the numbered folders for your own domains, edit the templates — nothing breaks as long as the templates folder name stays in sync with the Templater setting.

The Claude Code skills under `.agents/skills/` are individually swappable; check `skills-lock.json` for each one's source.

---

## What's gitignored

| Ignored | Why |
|---|---|
| `.obsidian/plugins/` | Plugin code lives in Obsidian's Community Plugins registry — install via the UI, don't vendor it |
| `.obsidian/workspace.json` | Per-machine pane layout |
| `.smart-env/` | Smart Connections embeddings cache; rebuilds on first run |
| `.trash/`, `.DS_Store` | OS / Obsidian noise |
| `.claude/settings.json`, `.claude/plans/`, `.claude/projects/` | Per-machine Claude Code state |

No secrets are committed. No plugin `data.json` ships in this repo, so you'll configure Smart Connections (model, Ollama endpoint, optional OpenRouter fallback) yourself on first run.

---

## License

MIT. Use it, fork it, change everything.
