---
name: ingest-resource
description: Fetch a URL, extract structured insights, and save to the right knowledge folder. Handles YouTube videos, articles, blog posts, Substack posts, and product pages. Extracts core idea, frameworks, quotes, and flags potential drill candidates. Trigger on "/ingest-resource [URL]", "ingest this", "save this to knowledge", "extract insights from", or when user shares a URL and wants it processed into the knowledge base.
---

# Ingest Resource

```
  /ingest-resource [URL]
        │
        ▼
  detect content type
  ┌──────────┬──────────┬──────────┬──────────┐
  │ YouTube  │ article  │ Substack │  tool /  │
  │  video   │  / blog  │   post   │  product │
  └────┬─────┴────┬─────┴────┬─────┴────┬─────┘
       └──────────┴──────────┘          │
                  │                     │
                  ▼                     ▼
          extract structure          extract
          core idea · frameworks     positioning
          quotes · drill candidate   use cases · pricing
                  │
                  ▼
          route to knowledge/
          ┌──────────────┬─────────────┬──────────────────┐
          │   general/   │    board/   │  new-drills/     │
          │  [slug].md   │ [name].md   │  candidates.md   │
          └──────────────┴─────────────┴──────────────────┘
```

> Verbatim quotes only — no paraphrase. One file per source, always. If there's no useful insight, say so rather than padding.

Fetch a URL, extract what matters, save it to the knowledge base.

## Step 1 — Identify content type

Classify the URL as one of:
- **YouTube video** — extract transcript if available, otherwise use title/description
- **Article or blog post** — fetch and extract full text
- **Substack post** — fetch and extract
- **Tool or product page** — extract positioning, use cases, pricing if relevant
- **Podcast transcript** — extract if available

If the URL is inaccessible or behind a paywall, say so immediately and ask for an alternative (paste of transcript, article text, etc.).

## Step 2 — Extract structured content

```
## [Title]

Source: [URL]
Date: [publication date if available]
Type: [YouTube / Article / Substack / Other]

### Core idea
[One paragraph — the central argument or insight]

### Key frameworks or mental models
- [Framework 1]
- [Framework 2]
- [Framework 3]

### Relevance to current project
[Why this is useful — which project or skill it connects to]

### Quotes worth keeping
- "[exact quote — verbatim only, no paraphrase]"

### Possible drill idea
[If this content suggests a new experiment, describe it in one sentence. Otherwise omit.]
```

## Step 3 — Save to the right folder

| Content type | Save to |
|---|---|
| Operator knowledge, AI workflows, tools, GTM ideas | `knowledge/general/[slug].md` |
| Adviser content (for the board of advisers) | `knowledge/board/[adviser-name].md` — append |
| New drill candidate | `knowledge/new-drills/candidates.md` — append using candidate card format |
| Wellness or personal content | `knowledge/wellness/[slug].md` |

Create the folder if it doesn't exist.

Use a slug derived from the title: lowercase, hyphenated, 4–6 words.

## Step 4 — Confirm

After saving, tell the user:
- Where you saved it
- The core idea in one sentence
- Whether it surfaced a drill candidate (yes/no)
- If yes: suggest running `/research-drills` to score it

---

## Rules

- Never paraphrase quotes — verbatim or omit
- One file per source — never merge multiple URLs into one file
- If there's no useful insight to extract, say so rather than padding the output
