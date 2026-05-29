---
name: research-drills
description: Search the web for new experiment and drill candidates, score them against the operator profile and current skills inventory, and flag the top pick. Checks existing skills before going to the web — many top drills are already installed and just need packaging. Accepts manual ideas via --feed flag. Trigger on "/research-drills", "find new drill ideas", "what should I build next", "research new experiments", or "what's worth packaging next".
---

# Research Drills

```
  /research-drills
        │
        ▼
  read knowledge/ context
  (profile · skills-inventory · existing candidates)
        │
        ▼
  check installed skills FIRST ←── best drills often already exist
        │
        ├── skill fits criteria? ──→ surface as candidate (no build needed)
        │
        ▼
  5 web searches
  (general · AI operators · Reddit · X · Substack)
        │
        ▼
  score each candidate  0──────────────────────10
                        │  buildable in 1 session  │ 0-2
                        │  free + paid packagable  │ 0-2
                        │  useful to YOU today     │ 0-3
                        │  standalone Substack post│ 0-3
        │
        ▼
  ★ flag top pick with reasoning
        │
        ▼
  append to knowledge/new-drills/candidates.md
        │
        ▼
  ask for approval → never auto-move to approved/
```

> The rule: check `knowledge/skills-inventory.md` before going to the web. Several 10/10 drills already exist as installed skills and just need packaging.

Find and score new experiment candidates. Check what's already installed before searching the web.

## Step 1 — Load context

Read `knowledge/profile.md` and `CLAUDE.md`.
Read `knowledge/skills-inventory.md` — check installed skills FIRST. Several top drills already exist as installed skills and just need packaging.
Read `knowledge/new-drills/candidates.md` to avoid re-surfacing what's already staged.
Read `knowledge/new-drills/revival-candidates.md` to avoid re-surfacing catalogued half-builds.

## Step 2 — Handle manual feed (if --feed flag used)

If the user ran `/research-drills --feed "[idea]"`:
1. Write a candidate card for the idea immediately (see card format below)
2. Score it against the four criteria
3. Add it to the candidates list before running web searches
4. Label it `[Manual feed]` in the Source field

## Step 3 — Run web searches

**Search 1 — General:**
`"Claude Code projects operators can build" 2025 2026`

**Search 2 — AI operators focused:**
`"AI tools for non-technical operators" "build in public" site:substack.com OR site:youtube.com`

**Search 3 — Reddit:**
`site:reddit.com "I built" AI tool operators productivity 2025`

**Search 4 — X / Twitter:**
`site:x.com "built with Claude" OR "Claude Code project" operators tool 2025 2026`

**Search 5 — Substack:**
`site:substack.com "Claude Code" OR "AI operator" project tutorial build 2025`

Collect the 2–3 most promising results per search.
Ignore: developer tutorials, anything requiring deep technical skill, anything already in P1–P5 or in candidates/revival files.

## Step 4 — Score each candidate

For each of the 5–8 strongest candidates, write a card:

```
## [Candidate Name]
Source: [URL or "Manual feed" or "Existing skill: [name]"]
Platform found: [Reddit / Substack / X / YouTube / General / Installed skill / Manual]
What it is: [One sentence]
Why it fits operators: [Why a non-technical operator would use this today]
Packageability: [How it becomes a free + paid deliverable]
Effort: [Low / Medium / High — one Claude Code session = Low]

Scores:
- Buildable in one Claude Code session: [0–2]
- Packageable as free + paid deliverable: [0–2]
- Useful to the operator today (not hypothetical): [0–3]
- Documentable in a standalone post: [0–3]
Total: [X/10]
```

## Step 5 — Flag the top pick

```
## ★ Top pick: [Name]
Score: [X/10]
Platform: [where found]
Why this one: [2–3 sentences — be specific about why this fits the current ICP
and what makes the before/after demo compelling]
Suggested next action: [specific — "Start a new session with: [exact prompt]"]
```

## Step 6 — Save output

Append to `knowledge/new-drills/candidates.md`:

```
---
## Research run: [DATE]
Searches: General · AI operators · Reddit · X · Substack
Manual feeds: [count or "none"]
Sources checked first: skills-inventory.md · revival-candidates.md
Candidates surfaced: [count]
Top pick: [name]
---
[candidate cards]
```

Do NOT overwrite previous runs. Always append.

## Step 7 — Ask for approval

After presenting the top pick, ask:
> "Do you want to move [top pick] to `knowledge/new-drills/approved/` and start planning the build?"

Only move on explicit confirmation. Never auto-approve.

---

## Scoring criteria (what makes a good drill)

- Buildable in one Claude Code session — not a multi-week project
- Packageable as free + paid deliverable for operators
- Useful TODAY — not a hypothetical problem
- Documentable in a post that stands alone

---

## Rules

- Never surface tools requiring paid API keys with no free tier as the MVP
- Never suggest projects that only work for one industry
- Never suggest a project already in the current build queue
- Check installed skills BEFORE going to the web — the best drill might already be installed
