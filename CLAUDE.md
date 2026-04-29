# CLAUDE.md

Guidance for Claude Code when working in this repository.

## First-run onboarding (do this before anything else)

If `brAIn/2. Life/Profile.md` does not exist when this session opens, the user has not been onboarded. Launch the **onboarding** skill (in `.agents/skills/onboarding/`) before responding to anything else, unless the user has explicitly told you to skip onboarding or to do something else first.

The onboarding skill conducts a ~10 minute structured conversation that learns who the user is, what they're learning, how they think, and what they want to capture. It then writes the user's Profile, Goals, and starter Subject notes into the vault. After it runs, the vault has a meaningful initial graph instead of empty folders.

If Profile.md exists, do not re-run onboarding unless the user explicitly asks.

## Repository overview

This is a single Obsidian vault (`brAIn/`) plus a Claude Code harness, packaged as a plug-and-play starter for ADHD and neurodivergent thinkers.

## Vault structure

`brAIn/` is one Obsidian vault. Top-level folders:

- `0. Notes/` — General / unsorted / inbox
- `1. Education/` — Subjects, definitions, learning resources
- `2. Life/` — Personal goals, inspiration, skills, reading, the user's Profile
- `3. Ventures/` — Business and entrepreneurial tracking
- `4. Archives/` — Old / superseded materials
- `5. Experiments/` — Sandbox
- `Templates/` — Templater source files

Numbering is intentional — it forces a stable sort order in the file tree.

## Note frontmatter

YAML frontmatter, varies by note type:

| Template | Fields |
|---|---|
| Notes | `Date`, `Subject` |
| Definition | `tags`, `Subject`, `Section` |
| Resource | `tags`, `Category`, `Subject`, `Section`, `Date` |
| Subject | `tags`, `Category`, `Subject` |
| Profile (created by onboarding) | `tags: [profile]`, `Date` |
| Goals (created by onboarding) | `tags: [goals]`, `Date` |

## Plugins

| Plugin | Purpose |
|---|---|
| Dataview | SQL-like queries embedded in notes — uses `from [[]] and #tag` syntax to pull related notes |
| Templater | Scripted templates in `Templates/`; uses `<% %>` syntax |
| Calendar | Daily-note navigation |
| Smart Connections | Local AI semantic search via embeddings (TaylorAI/bge-micro-v2 through Transformers); optional Ollama for chat. Embeddings cache in `.smart-env/` |
| Style Settings | Theme customization UI |
| Spaced Repetition | Flashcard / SRS over passages in any note |

## Dataview pattern

Definition, Resource, and Subject notes use backlink-scoped queries:

```dataview
list
from [[]] and #definition
```

`[[]]` resolves to the current note. The query says: list every note that links to this one and is tagged `#definition`. Notes self-organize through this — write a link once and the parent note picks it up forever.

## Smart Connections config

`.smart-env/smart_env.json` (per-user, gitignored):

- Embedding model: `TaylorAI/bge-micro-v2` (local, via Transformers)
- Chat model: Ollama (local) by default
- Cloud fallback: OpenRouter (optional)
- Min block size for embeddings: 200 characters

Embeddings live in `.smart-env/multi/` as `.ajson` files. Do not edit manually.

## Skills

Skills under `.agents/skills/`:

| Skill | Source | Purpose |
|---|---|---|
| onboarding | local | First-run conversation; seeds Profile, Goals, Subject notes |
| book-analyst | local | Walks the user through reflecting on a book; writes a book analysis note |
| defuddle | github (kepano/obsidian-skills) | Strip clutter from web pages and import as clean markdown |
| json-canvas | github (kepano) | Create and edit `.canvas` files |
| obsidian-bases | github (kepano) | Create and edit `.base` files |
| obsidian-cli | github (kepano) | Drive Obsidian via its CLI |
| obsidian-markdown | github (kepano) | Write Obsidian-flavored markdown (wikilinks, callouts, embeds, properties) |
