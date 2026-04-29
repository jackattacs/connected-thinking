# Connected Thinking

An opinionated Obsidian vault + Claude Code harness for people who want a single second brain across learning, life, and work — with local AI built in.

Clone the repo, open the vault, and you've skipped the six months most people spend tweaking their Obsidian setup.

---

## Why this exists

Most "Obsidian starter" vaults fall into one of two camps:

- **Pure note-taking systems** (Zettelkasten, LYT, PARA): heavy on theory, light on tooling. You're left to wire up Dataview, Templater, and AI plugins yourself.
- **Single-purpose vaults**: built for journaling, or research, or project management — but not all three.

Connected Thinking is for people whose brain doesn't split cleanly between domains. One vault holds your subjects of study, life goals, and ventures, and the tooling helps you draw connections across them instead of siloing them.

It's also AI-native: Smart Connections gives you semantic search over your notes locally, and the bundled Claude Code harness lets an agent navigate, query, and edit the vault directly — using skills that understand Obsidian's flavor of markdown, Bases, and Canvas.

---

## Who it's for

- You take notes across multiple life domains (learning, personal, work) and want them in one place.
- You want AI assistance on your own notes without uploading them to a cloud service.
- You like keyboard-driven, markdown-based workflows over Notion-style block editors.
- You're comfortable in a terminal and want an editable, version-controlled vault — not a SaaS product.

If you only journal, or only do research, this is overkill.

---

## How it compares

| | Connected Thinking | PARA | Zettelkasten / LYT | Notion |
|---|---|---|---|---|
| **Organization** | Numbered domain folders (Education / Life / Ventures) | Projects / Areas / Resources / Archives | Atomic notes + tag graph | Nested pages + databases |
| **Templates** | Templater + Dataview, frontmatter-driven | Manual | Manual | Native templates |
| **AI search** | Local embeddings (Smart Connections) | None | None | Cloud (Notion AI) |
| **AI authoring** | Claude Code harness with vault-aware skills | None | None | Notion AI (chat only) |
| **Data ownership** | Markdown files on your disk | Markdown files | Markdown files | Cloud-hosted, exportable |
| **Setup time** | 10 min (this repo) | DIY | DIY | None — but locked in |

---

## What you get

- **Vault structure** — numbered top-level folders so they sort predictably (`0. Notes` through `5. Experiments`).
- **Four templates** — Subject, Resource, Definition, and Book Analysis. Each uses YAML frontmatter and embedded Dataview queries so notes self-organize as you tag and link them.
- **Cupertino theme** — pre-bundled, SF Pro fonts, calm muted accents.
- **Six community plugins** wired together: Dataview, Templater, Calendar, Smart Connections, Style Settings, Spaced Repetition.
- **Claude Code harness** — `.claude/`, `.agents/skills/`, and `skills-lock.json` set up with five Obsidian-aware skills (defuddle, json-canvas, obsidian-bases, obsidian-cli, obsidian-markdown) plus a custom book-analyst skill that walks you through writing a book reflection.

What you don't get: notes. The vault ships empty so it's yours to fill.

---

## The AI layer

Two complementary tools:

| Tool | Runs on | What it does |
|---|---|---|
| **Smart Connections** (Obsidian plugin) | Your machine — local embeddings (TaylorAI/bge-micro-v2) and Ollama for chat | Semantic search across your vault. Find the note you forgot you wrote. Optional chat with your own notes as context. |
| **Claude Code** (CLI) | Anthropic API + local file access | An agent that can read, write, and reorganize your vault. The bundled skills teach it Obsidian wikilinks, callouts, properties, and Canvas/Bases formats so output looks native. |

Both are optional. The vault works fine as a plain Obsidian setup if you skip them.

---

## Prerequisites

- [Obsidian](https://obsidian.md/) (desktop)
- Optional: [Claude Code](https://claude.com/claude-code) for the AI harness
- Optional: [Ollama](https://ollama.com/) for Smart Connections local chat

---

## Setup

1. **Clone**

   ```sh
   git clone https://github.com/vokal-jack/connected-thinking ~/Documents/connected-thinking
   ```

2. **Open the vault in Obsidian**

   Obsidian → *Open folder as vault* → select `connected-thinking/brAIn/`.

3. **Install community plugins**

   Settings → Community plugins → turn off Restricted mode. Install these six. They'll auto-enable from the vault config once installed:

   | Plugin | Purpose |
   |---|---|
   | Dataview | SQL-like queries inside notes |
   | Templater | Scripted templates (`<% %>` syntax) |
   | Calendar | Daily-note navigation |
   | Smart Connections | Local AI semantic search + chat |
   | Style Settings | Theme customization UI |
   | Spaced Repetition | Flashcards over your own notes |

4. **Point template plugins at `Templates/`**

   - Settings → Templates → Template folder location: `Templates`
   - Settings → Templater → Template folder location: `Templates`

5. **Theme**

   Cupertino is bundled. Settings → Appearance → Theme → Cupertino.

6. **(Optional) Claude Code**

   Open the repo root with `claude .`. The harness loads `.claude/settings.local.json` and resolves skills via `skills-lock.json` automatically.

---

## Folder convention

| Folder | Use |
|---|---|
| `0. Notes/` | Unsorted / inbox |
| `1. Education/` | Subjects, definitions, learning resources |
| `2. Life/` | Personal goals, inspiration, skills, reading |
| `3. Ventures/` | Business and entrepreneurial tracking |
| `4. Archives/` | Old materials |
| `5. Experiments/` | Sandbox |
| `Templates/` | Templater source files |

Frontmatter conventions for each note type are documented in [`CLAUDE.md`](./CLAUDE.md).

The numbering is intentional: it forces a stable sort order in the file tree without relying on Obsidian's per-folder ordering UI.

---

## How notes self-organize

The Definition and Resource templates ship with a Dataview query like:

```dataview
list
from [[]] and #definition
```

`[[]]` resolves to the current note, so any note that links here and is tagged `#definition` shows up automatically. You write the link once when you create a definition, and the parent subject note picks it up forever after. No manual indexing.

---

## What's gitignored

| Ignored | Why |
|---|---|
| `.obsidian/plugins/` | Plugin code lives in the Obsidian Community Plugins registry — install via the UI, don't vendor it |
| `.obsidian/workspace.json` | Per-machine pane layout |
| `.smart-env/` | Smart Connections embeddings cache; rebuilds locally on first run |
| `.trash/`, `.DS_Store` | OS / Obsidian noise |
| `.claude/settings.json`, `.claude/plans/`, `.claude/projects/` | Per-machine Claude Code state |

No secrets are committed. No `data.json` from any plugin ships in this repo, so you'll configure Smart Connections (model choice, Ollama endpoint, OpenRouter fallback if you use one) yourself.

---

## Customizing

This is a starter, not a framework. Rename the `brAIn/` directory, swap the numbered folders for your own domains, edit the templates — none of it will break the harness as long as you keep the templates folder name in sync with the Templater setting.

The Claude Code skills under `.agents/skills/` are individually swappable; check `skills-lock.json` for the source of each.

---

## License

MIT. Use it, fork it, change everything.
