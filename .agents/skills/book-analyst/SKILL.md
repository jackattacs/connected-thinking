---
name: book-analyst
description: Guide Jack through analyzing a book he has read. Conducts a structured conversation to extract what stuck, what he questioned, and how it changed his thinking — then writes a book analysis note in the brAIn vault. Use when Jack mentions finishing a book or asks to analyze one.
---

# Book Analyst Skill

Build a book analysis note for Jack's Reading section. The note is built entirely from Jack's answers — not from summaries, not from Goodreads, not from what a reviewer said. Only what Jack remembers and has retained.

## Vault Path

Notes go to:
`brAIn/2. Life/Reading/[Book Title].md` (relative to the vault root)

Use the Book Analysis Template structure (see below).

---

## Conversation Protocol

One question at a time. Do not move to the next step until Jack has answered. Do not pre-fill answers.

**Step 1 — Recall**
Ask: *"What do you remember about [book title]? Don't look it up — just tell me what comes to mind."*
Listen. Write down every idea he mentions. These are the candidates for "What Stuck."

**Step 2 — Core Idea**
Ask: *"If you had to explain what the author is actually arguing — one core idea — what would you say?"*
This becomes "The Core Idea" section. Jack's words only.

**Step 3 — Pushback**
Ask: *"Was there anything you disagreed with, or that didn't hold up against what you already know?"*
If yes, goes in "What I Disagreed With." If no, leave the section out.

**Step 4 — Connections**
Ask: *"How does this connect to things you already know — aerospace, engineering, Adobe, chemistry, business, your life?"*
Frame these as bold domain + one tight sentence. 2–3 connections minimum.

**Step 5 — 30-Second Summary**
Ask: *"Give me your 30-second version. What would you tell someone who asks if they should read it?"*
This becomes "In My Own Words."

**Step 6 — Quotes**
Ask: *"Any lines that stuck with you? Exact quotes if you remember them — paraphrase if not."*
If none, skip the section.

**Step 7 — Rating**
Ask: *"1 to 10. Would you re-read it?"*

---

## Note Structure

```
---
tags:
  - book-analysis
Author: [Author Name]
Date Read: [YYYY-MM-DD if known, otherwise approximate]
Rating: [X]/10
Status: finished
Summary: [One sentence from Jack's 30-second summary]
---

# [Book Title]

[One-sentence framing — what this book is actually about, in Jack's words]

---

## The Core Idea

[Jack's answer from Step 2]

---

## What Stuck

[Bullet points from Step 1 — only ideas Jack recalled without prompting]

---

## What I Disagreed With

[Jack's answer from Step 3 — omit section if nothing]

---

## Best Quotes

> "[Quote]" — [Author]

[Omit if no quotes remembered]

---

## In My Own Words

> [Jack's 30-second summary from Step 5]

---

## Connections

**[Domain]** — [One tight sentence].

**[Domain]** — [One tight sentence].

---

## Links
[[Reading]]
```

---

## Rules

- Never pre-fill the note with plot summaries or author background Jack didn't mention.
- "What Stuck" contains only ideas Jack recalled in Step 1 — not everything the book covers.
- If Jack says "I don't remember much," that's fine — a short honest note beats a padded one.
- Connections must be personal to Jack: aerospace, Adobe, chemistry, cars, things he's built, his business, his life.
- "In My Own Words" is always Jack's voice — never paraphrase it into cleaner prose.
- After writing the note, show it to Jack for approval before saving.

---

## Example Invocation

> "I just finished The Tipping Point. Let's write it up."

Start with Step 1. Do not summarize the book first. Do not tell Jack what it's about. Ask him what he remembers.
