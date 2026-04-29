# Connected Thinking

A plug-and-play Obsidian + Claude Code workflow. Clone, open the vault, and you're running the same setup as me.

## What's inside

- `brAIn/` — Obsidian vault. Numbered-folder organization (`0. Notes`, `1. Education`, `2. Life`, `3. Ventures`, `4. Archives`, `5. Experiments`), Templater templates, Cupertino theme, and the community-plugin allow-list.
- `.claude/`, `.agents/`, `skills-lock.json`, `CLAUDE.md` — Claude Code harness preconfigured with the skills I use against this vault (defuddle, json-canvas, obsidian-bases, obsidian-cli, obsidian-markdown).

## Prerequisites

- [Obsidian](https://obsidian.md/) (desktop)
- Optional: [Claude Code](https://claude.com/claude-code) if you want the AI harness
- Optional: [Ollama](https://ollama.com/) for Smart Connections local chat

## Setup

1. **Clone the repo**

   ```sh
   git clone <this-repo-url> ~/Documents/connected-thinking
   ```

2. **Open the vault in Obsidian**

   Obsidian → "Open folder as vault" → select `connected-thinking/brAIn/`.

3. **Install community plugins**

   Settings → Community plugins → turn off Restricted mode. Install these six (the vault config already has them in the enabled list, so they'll switch on automatically once installed):

   | Plugin | Purpose |
   |---|---|
   | Dataview | SQL-like queries inside notes |
   | Templater | Scripted templates (`<% %>` syntax) |
   | Calendar | Daily-note navigation |
   | Smart Connections | Local AI semantic search + Ollama chat |
   | Style Settings | Theme customization UI |
   | Spaced Repetition | Flashcard / SRS system |

4. **Point template plugins at the `Templates/` folder**

   - Settings → Templates → Template folder location: `Templates`
   - Settings → Templater → Template folder location: `Templates`

5. **Theme**

   Cupertino is already bundled in `.obsidian/themes/`. Settings → Appearance → Theme → Cupertino.

## Folder convention

| Folder | Use |
|---|---|
| `0. Notes/` | Unsorted / general notes |
| `1. Education/` | Subjects, definitions, learning resources |
| `2. Life/` | Personal goals, inspiration, skills |
| `3. Ventures/` | Business and entrepreneurial tracking |
| `4. Archives/` | Old materials |
| `5. Experiments/` | Sandbox |
| `Templates/` | Templater source files |

Note frontmatter conventions are documented in `CLAUDE.md`.

## Claude Code (optional)

Open the repo root in Claude Code. The harness loads `.claude/settings.local.json` and the skills listed in `skills-lock.json` automatically. The skills give Claude direct support for editing Obsidian-flavored markdown, Bases, Canvas, and using the Obsidian CLI.

## What's gitignored

- `.obsidian/plugins/` — install plugins via Obsidian's Community Plugins UI; their code and per-machine `data.json` settings stay out of git.
- `.obsidian/workspace.json` — per-machine pane layout.
- `.smart-env/` — Smart Connections embeddings cache (rebuilds locally).
- `.trash/`, `.DS_Store`, etc.
