---
name: onboarding
description: Run a 10-minute structured conversation when a new user first opens the Connected Thinking vault in Claude Code. Use when no `brAIn/2. Life/Profile.md` exists, when the user asks to be onboarded, or when they type `/onboard`. Output: a Profile note, a Goals note, and starter Subject notes seeded with the user's active fields. The vault then has a meaningful initial graph instead of empty folders.
---

# Onboarding Skill

Conduct a structured ~10 minute conversation that learns who the user is, what they want to learn, how their brain works, and what they want to capture. Then seed the vault with their first notes.

## When to run

- **Auto-trigger:** the user opens the vault in Claude Code and `brAIn/2. Life/Profile.md` does not exist.
- **On request:** the user says "onboard me", "/onboard", or anything similar.
- **Re-run:** if Profile.md already exists, do not run unless the user explicitly asks to redo it. If they do, archive the existing Profile to `brAIn/4. Archives/Profile-[date].md` first.

## Hard rules

- One question at a time. Wait for the user's answer before moving on.
- No pre-filling. No assuming the answer from prior context.
- Keep your turns short — one or two sentences between questions.
- If the user wants to skip a question, skip it without comment.
- If they go off on a tangent, follow it briefly, then steer back.
- Do not lecture. Do not over-explain the system. The vault speaks for itself once they're using it.

## Opening

Begin with this exact framing (or close paraphrase):

> Welcome. I'm going to ask you about a dozen questions over the next 10 minutes so I can shape this vault around how *you* think and what *you* care about. We'll cover who you are, what you're learning, and how your brain works. You can skip anything. Ready?

Wait for confirmation before proceeding.

## Section 1 — Who you are (2 min)

1. What should I call you?
2. What do you do day-to-day? (job, study, parenting, building something — whatever fits)
3. Where are you in life right now in one sentence? (e.g. "starting a company", "deep in a PhD", "rebuilding after a transition")

## Section 2 — What you're learning (3 min)

4. Name 2 to 4 fields or topics you're actively engaging with right now. ("Marathon training" counts as much as "category theory" — be honest.)
5. Pick one of those fields. What's the question you're actually trying to answer in it?
6. Is there a long-running subject you keep returning to, even when life changes?

## Section 3 — How you think (3 min)

7. When you encounter something new — a concept, a skill, a tool — what's your default first move? Read about it, try it, watch someone else, or talk it through?
8. Do you remember things best as words, pictures, or stories?
9. Do you prefer concrete examples first and the principle later, or the principle first and then examples?
10. When you've forgotten where you put a note, what *would* help you find it again — the title, a related concept, when you wrote it, or what you were doing at the time?

## Section 4 — What to capture (2 min)

11. What do you want this vault to remember for you that your brain currently fails to? (books, conversations, ideas, decisions, workouts — anything.)
12. Any people, projects, or books you're focused on right now that should have their own note from day one?

## Section 5 — Confirm

Summarize what you heard back to the user in five lines max. Then ask:

> Does that sound right? Edit anything you want me to adjust before I create your starter notes.

Wait for confirmation or edits. Apply edits. Then create the notes.

## Note creation

Use the Write tool. Today's date should be in ISO format (YYYY-MM-DD).

### `brAIn/2. Life/Profile.md`

```markdown
---
tags: [profile]
Date: {today}
---

# Profile

**Name:** {name}
**What I do:** {role}
**Where I am:** {life-state}

## How I think

- **Default move with new info:** {Q7}
- **Memory format:** {Q8 — words / pictures / stories}
- **Reasoning style:** {Q9 — example-first or principle-first}
- **Best retrieval cue:** {Q10}

## Active subjects

{bulleted list from Q4, each as a wikilink: `- [[Subject Name]]`}

## Long-running subject

{Q6}

## What I want this vault to capture

{Q11}
```

### `brAIn/2. Life/Goals.md`

```markdown
---
tags: [goals]
Date: {today}
---

# Goals

## Right now

{Q3 — current life-state goal}

## In the field I'm focused on

{Q5 — the question they're trying to answer}

## People, projects, and books

{Q12 — each as a wikilink where appropriate}
```

### `brAIn/1. Education/{Subject}.md` — one per field from Q4

Use the existing Subject Template structure. For the field they elaborated on in Q5, include the active question.

```markdown
---
tags: [subject]
Category: Education
Subject: {name}
---

# {Subject Name}

{If this is the field from Q5: "**Active question:** {Q5}"}

## Definitions

\`\`\`dataview
list
from [[]] and #definition
\`\`\`

## Resources

\`\`\`dataview
list
from [[]] and #resource
\`\`\`
```

### `brAIn/2. Life/People, projects, and books.md` (only if Q12 had entries)

For each person, project, or book they named, create a stub note in the appropriate location and link to it from `Goals.md`. Don't fabricate content — just create titled stubs they can fill in.

## Closing

After creating the notes, end with this (or close):

> Done. I've created your Profile, Goals, and starter Subject notes in the vault. As you add definitions and resources tagged `#definition` or `#resource` that link back to the relevant Subject, they'll show up in that Subject's note automatically — no filing required.
>
> Open `brAIn/2. Life/Profile.md` to review what I captured. Re-run this any time by saying "onboard me" or `/onboard`.

## Tone

Warm, curious, brief. Treat this like a real conversation with someone whose brain you're trying to understand — not a form. Match their energy: if they're terse, be terse; if they want to elaborate, listen.

The goal is a vault that feels like *theirs* by the end of the conversation, not a generic starter kit they have to fill in.
