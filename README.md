# AI Crew Skills

Claude Code skills for operators. Built by [AI Crew](https://aicrew.com) — packaged from real client sessions, not hypothetical workflows.

## Install

```bash
claude plugins marketplace add este3v2/ai-crew-skills
claude plugins install ai-crew-skills@este3v2
```

Restart Claude Code. Skills auto-trigger from their descriptions, or invoke directly (e.g. `/prompt-rewriter`).

---

## How the skills fit together

```
  FEED IN                   SKILLS                        KNOWLEDGE BASE
  ───────                   ──────                        ──────────────

  article / video
  podcast / page   ──────→  /ingest-resource  ──────────→  knowledge/
  adviser content           fetch · extract                general/
                            save to right folder           board/
                                                           new-drills/
                                                                │
                                          ┌─────────────────────┘
                                          │
              ┌───────────────────────────┼──────────────────┐
              │                           │                  │
              ▼                           ▼                  ▼
       /ask-board               /research-drills      /improve-system
       load profiles            check installed       5q debrief
       answer as each           skills first          update knowledge/
       adviser                  then search web       update skills/
       synthesize               score · flag          log session
              │                           │                  ▲
              ▼                           ▼                  │
       [decision clarity]      [next drill candidate]        │
                                          │                  │
                                          └──→  BUILD  ──────┘
                                               session

  ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─

  STANDALONE — works anywhere, no knowledge/ needed

  [any bloated prompt]
          │
          ▼
  /prompt-rewriter
  classify → strip scaffolding → rewrite to 4-component format
          │
          ▼
  [clean prompt + before/after diff + risk items]
```

---

## Skills

### `/prompt-rewriter`
Strips compensating complexity from any system prompt. Classifies every line (outcome / constraint / scaffolding / duct-tape), rewrites to a clean 4-section format, shows before/after diff and risk items.

**Standalone — no project structure required.**

```
/prompt-rewriter

[paste your prompt]
```

---

### `/ask-board`
Answers any strategic question by looping through your board of adviser profiles. Each adviser responds in their own voice using their frameworks. Synthesizes where they agree and diverge. Ends with one recommended action.

**Requires `knowledge/board/` profiles.** Build them with `/ingest-resource`.

```
/ask-board Should I prioritize growing the audience or converting existing leads this quarter?
```

---

### `/ingest-resource [URL]`
Fetches any URL, extracts core idea + frameworks + quotes, saves to the right `knowledge/` folder. Flags drill candidates automatically.

```
/ingest-resource https://example.com/article
```

---

### `/research-drills`
Finds new experiment candidates. Checks your installed skills inventory first (best drills are often already installed and just need packaging), then searches the web. Scores each candidate. Flags the top pick. Never auto-approves.

```
/research-drills
/research-drills --feed "my own idea to score"
```

---

### `/improve-system`
End-of-session debrief. Asks 5 structured questions, classifies what to update, edits the right files, logs the session. Run this after any session that produced significant output.

```
/improve-system
```

---

## Project structure expected

`/ask-board`, `/improve-system`, `/ingest-resource`, and `/research-drills` work within a project that has:

```
knowledge/
  profile.md          ← who the operator is, goals, constraints
  board/              ← adviser profiles (built via /ingest-resource)
  general/            ← ingested articles and resources
  new-drills/
    candidates.md     ← staged drill ideas
    approved/         ← approved, ready to plan
skills/               ← skill files (updated by /improve-system)
CLAUDE.md             ← project brain file
```

`/prompt-rewriter` works standalone with no structure required.

---

## Part of Experiment Drill 26

These skills are documented as free + paid operator tools in the [Experiment Drill 26 Substack series](https://substack.com). Each skill has a free prompt version and a paid implementation guide for client delivery.
