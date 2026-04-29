# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a personal Obsidian knowledge management system organized into three separate vaults:

- **Education/** — Academic learning, subject notes, definitions, and resources
- **Life/** — Personal goals, inspiration, notes, and skill development
- **Ventures/** — Business and entrepreneurial tracking

## Vault Structure Pattern

All three vaults follow the same numbered-folder convention:
- `0. Notes/` — General/unsorted notes
- `1. [Primary Category]/` — Main organizational category (Subjects, Businesses, etc.)
- `2. [Secondary Category]/` — Secondary category (Resources, Companies, etc.)
- `3. Definitions/` — Definition entries (Education only)
- `4. Archives/` — Archived materials
- `Templates/` — Templater templates for note creation

## Note Frontmatter

Notes use YAML frontmatter. Common fields vary by note type:

**Notes Template:** `Date`, `Subject`

**Definition Template:** `tags`, `Subject`, `Section`

**Resource Template:** `tags`, `Category`, `Subject`, `Section`, `Date`

**Subject Template:** `tags`, `Category`, `Subject`

## Plugins in Use

- **Dataview** — SQL-like queries embedded in notes (Education and Life vaults). Queries use `from [[]] and #tag` syntax to pull related notes.
- **Templater** — Scripted templates in `Templates/` folders; use `<% %>` syntax.
- **Smart Connections** — AI semantic search powered by local embeddings (TaylorAI/bge-micro-v2 via Transformers) and Ollama for chat. Embeddings are cached in `.smart-env/`.
- **Calendar** — Daily note navigation.
- **Style Settings** — Theme customization.
- **Highlighter** — Text highlighting (Life and Ventures vaults).

## Dataview Query Pattern

Definition and Resource templates use backlink-scoped queries:
```dataview
list
from [[]] and #definition
```
This pulls all notes tagged `#definition` that also link back to the current note.

## AI/Smart Connections Config

Each vault's `.smart-env/smart_env.json` configures:
- Embedding model: `TaylorAI/bge-micro-v2` (local, via Transformers)
- Chat model: Ollama (local)
- Cloud fallback: OpenRouter
- Min block size for embeddings: 200 characters
- Excludes: Untitled files

Processed embeddings are stored in `.smart-env/multi/` as `.ajson` files — do not edit these manually.
