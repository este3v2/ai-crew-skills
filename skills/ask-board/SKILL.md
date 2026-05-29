---
name: ask-board
description: Answer any strategic question by looping through your personal board of advisers. Each adviser responds in their own voice using their frameworks. Then synthesizes where they agree and diverge, ending with one recommended action. Requires adviser profiles in knowledge/board/. Trigger on "/ask-board [question]", "ask my board", "what would my advisers say about", or any strategic decision question when board context is available.
---

# Ask Board

Loop through your personal board of advisers, answer as each one, synthesize, and recommend.

## Step 1 — Load context

Read `knowledge/profile.md` and all files in `knowledge/board/`.

If `knowledge/board/` is empty or doesn't exist:
> "No board members ingested yet. Run `/ingest-resource [URL]` with content from each adviser to build their profiles first."

Stop there — do not continue without profiles.

## Step 2 — Answer as each adviser

For each file in `knowledge/board/`, write a response in that adviser's voice:
- Use their known frameworks and mental models (from their profile)
- Use their language and tone
- Apply their contrarian takes where relevant
- 3–5 sentences max — punchy, not verbose

Format each response as:
```
### [Adviser Name]
[their response]
```

## Step 3 — Synthesize

After all individual responses, write:

```
## Synthesis

**Where they agree:** [what all or most advisers converge on]
**Where they diverge:** [the key tension or disagreement]
**What the divergence reveals:** [the assumption you need to pressure-test]
```

## Step 4 — Recommend

End with:

```
## One action

[One clear recommendation, 2–3 sentences.
Grounded in the user's specific constraints from knowledge/profile.md.]
```

---

## Variants

`/ask-board [question]` — full board, all advisers
`/ask-board --adviser [name] [question]` — single adviser only
`/ask-board --devil [question]` — board argues against your current plan
`/ask-board --decision [question]` — forced binary choice, no "it depends"
