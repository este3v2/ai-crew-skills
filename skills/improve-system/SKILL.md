---
name: improve-system
description: End-of-session debrief that captures what worked and what didn't, then updates knowledge files and skills so the next session starts smarter. Asks 5 structured questions, classifies feedback, makes targeted file edits, and logs the session. Trigger on "/improve-system", "end of session", "update my system", "capture what we learned", or when the user asks to wrap up a session.
---

# Improve System

```
  /improve-system
        │
        ▼
  5 debrief questions
  (what worked · what didn't · what Claude got wrong)
        │
        ▼
  classify each answer
  ┌─────────────────┬──────────────┬──────────────┬───────────┐
  │ profile update  │ skill update │ CLAUDE.md    │ no action │
  └────────┬────────┴──────┬───────┴──────┬───────┴───────────┘
           │               │              │
           ▼               ▼              ▼
    knowledge/       skills/*.md      CLAUDE.md
    profile.md
           │               │              │
           └───────────────┴──────────────┘
                           │
                           ▼
                  knowledge/improve-log.md
                  (append session entry)
```

> Run this after every session that produced significant output. The system compounds — each session makes the next one faster.

Capture session feedback and update the operator OS so it compounds over time.

## Step 1 — Debrief

Ask the user these 5 questions. Ask them all at once:

```
Quick debrief — answer these:

1. What output from this session was better than expected?
2. What output was weaker than expected or needed rework?
3. Was there anything Claude got wrong about your context, preferences, or goals?
4. Any prompt or approach that worked surprisingly well?
5. Anything you had to repeat or re-explain that Claude should just know?
```

Wait for answers before proceeding.

## Step 2 — Classify each piece of feedback

For each answer, classify as one of:

- **Profile update** — Claude misunderstood something about the user → update `knowledge/profile.md`
- **Skill update** — a skill produced weak output → update the relevant file in `skills/`
- **CLAUDE.md update** — a systemic rule needs to change → update `CLAUDE.md`
- **No action** — useful to note, nothing to change in files

Show the classification before making any changes.

## Step 3 — Make the changes

For each item requiring a file update:
1. State what you're changing and why (one sentence)
2. Make the edit
3. Confirm the change

Never make changes without stating them first.

## Step 4 — Log the session

Append to `knowledge/improve-log.md`:

```
---
Date: [TODAY]
Session: [brief description of what was worked on]
Changes made:
- [file]: [what changed and why]
No-action items:
- [anything noted but not acted on]
---
```

Create `knowledge/improve-log.md` if it doesn't exist.

---

## Rules

- Never delete content from knowledge files — only add or refine
- If feedback contradicts an existing rule in CLAUDE.md, flag the conflict and ask which takes precedence before changing anything
- Keep changes minimal — one targeted edit per piece of feedback, not a rewrite
