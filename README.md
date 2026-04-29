# Connected Thinking

Obsidian vault + Claude Code harness. Built for ADHD brains.

Open it. Start writing. The system stays out of your way.

---

## Why most note systems fail ADHD brains

| What systems assume | ADHD reality |
|---|---|
| You'll remember where you filed it | Out of sight, gone |
| You'll apply a taxonomy consistently | Decision fatigue burns working memory |
| You'll review on a schedule | Time blindness kills voluntary routines |
| You can hold structure in your head | Working memory caps at ~4 items |
| You'll stick with one system | Interest shifts; rigid systems get abandoned |

Result: a graveyard of half-built vaults, retried every few months.

---

## What this fixes

- **Memory is associative, not hierarchical.** Six broad folders. Real structure lives in `[[wikilinks]]`, `#tags`, and Dataview queries. Notes find each other.
- **Working memory is tiny.** Templates pre-decide structure so you only think about content.
- **Spaced retrieval beats willpower.** Spaced Repetition plugin schedules reviews from passages in your own notes.
- **Visual + verbal beats either alone.** Graph view, Canvas, and Bases give spatial encodings of the same notes.

---

## ADHD-specific wins

| Challenge | What handles it |
|---|---|
| Working memory limits | Frontmatter + templates |
| Blank-page paralysis | Pre-built fields |
| Object permanence | Smart Connections (semantic search) |
| Hyperfocus tangents | `0. Notes/` inbox, retrieve by topic later |
| Time blindness | Calendar + daily notes |
| Decision fatigue | 6 folders, not 60 |
| Task switching | One vault for everything |
| Restarting after a gap | Conventional defaults — easy to resume |

---

## Also good for

**Autism** — predictable structure, pattern-friendly graph view, low-stim theme, explicit frontmatter.

**Dyslexia** — semantic search ignores spelling, SF Pro typography, spatial navigation via Canvas and Graph.

Tool, not treatment. Talk to a clinician if you're struggling.

---

## What ships

| Layer | What |
|---|---|
| Folders | `0. Notes` → `5. Experiments` |
| Templates | Subject, Resource, Definition, Book Analysis |
| Theme | Cupertino — calm, low-stim |
| Plugins | Dataview, Templater, Calendar, Smart Connections, Style Settings, Spaced Repetition |
| AI search | Smart Connections — local embeddings, optional Ollama chat |
| AI authoring | Claude Code with 5 Obsidian skills + book-analyst |

Vault ships empty. Notes are yours.

---

## vs other systems

| | This | PARA | Zettelkasten | Notion |
|---|---|---|---|---|
| Built for ADHD | Yes | No | No | No |
| Pre-built templates | Yes | No | No | Yes |
| Local AI search | Yes | No | No | No |
| AI agent for editing | Yes | No | No | Chat only |
| Files on your disk | Yes | Yes | Yes | No |
| Setup time | 10 min | DIY | DIY | Locked-in |

---

## Setup

1. `git clone https://github.com/jackattacs/connected-thinking ~/Documents/connected-thinking`
2. Obsidian → *Open folder as vault* → `connected-thinking/brAIn/`
3. Settings → Community plugins → turn off Restricted mode, then install all six (links below). They auto-enable once installed because the vault config already lists them as enabled.

   - [Dataview](https://obsidian.md/plugins?id=dataview) — SQL-like queries inside notes
   - [Templater](https://obsidian.md/plugins?id=templater-obsidian) — scripted templates
   - [Calendar](https://obsidian.md/plugins?id=calendar) — daily-note navigation
   - [Smart Connections](https://obsidian.md/plugins?id=smart-connections) — local AI semantic search + chat
   - [Style Settings](https://obsidian.md/plugins?id=obsidian-style-settings) — theme customization UI
   - [Spaced Repetition](https://obsidian.md/plugins?id=obsidian-spaced-repetition) — flashcards from your own notes
4. Settings → Templates and Templater → folder = `Templates`
5. Settings → Appearance → Theme → Cupertino
6. *(optional)* `claude .` from the repo root

---

## Daily use

**Folders**

- `0. Notes/` — inbox
- `1. Education/` — subjects, definitions, resources
- `2. Life/` — goals, inspiration, reading
- `3. Ventures/` — work, businesses
- `4. Archives/` — old
- `5. Experiments/` — sandbox

**Self-organizing notes**

Definition and Resource templates contain:

```dataview
list
from [[]] and #definition
```

Link a note once. Parent picks it up forever. No manual indexing.

**AI**

- **Smart Connections** — find notes by meaning when you forgot the title
- **Claude Code** — draft, reorganize, summarize across multiple notes

Both optional.

---

## Customize

Rename folders, edit templates. Nothing breaks if `Templates/` keeps its name.

---

## Gitignored

`.obsidian/plugins/`, `workspace.json`, `.smart-env/`, `.trash/`, `.DS_Store`, per-machine Claude Code state. Configure Smart Connections (Ollama endpoint, model) on first run.

---

## References

Cowan 2001 (working memory). Clark & Chalmers 1998 (extended mind). Ebbinghaus 1885 (forgetting curve). Paivio 1971 (dual coding).

---

## License

MIT.
