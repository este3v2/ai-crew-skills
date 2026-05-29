# AI Crew Skills

Claude Code skills for operators. Built and maintained by [AI Crew](https://aicrew.com).

## Install

```bash
claude plugins marketplace add este3v2/ai-crew-skills
claude plugins install ai-crew-skills@este3v2
```

Restart Claude Code. Skills will appear in your list and auto-trigger based on their descriptions.

## Skills

| Skill | Trigger | What it does |
|---|---|---|
| `/prompt-rewriter` | paste any prompt | Strips compensating complexity — procedural scaffolding, role-play preambles, duct-tape instructions. Rewrites to clean 4-component format. Shows before/after diff + risk items. |
| `/ask-board` | any strategic question | Loops through your board of adviser profiles, answers as each one, synthesizes where they agree/diverge, ends with one recommendation. Requires `knowledge/board/` profiles. |
| `/improve-system` | end of session | 5-question debrief. Classifies feedback, updates knowledge files and skills. Logs the session. |
| `/ingest-resource [URL]` | any URL | Fetches content, extracts core idea + frameworks + quotes, saves to the right `knowledge/` folder. Flags drill candidates. |
| `/research-drills` | when you want new ideas | Checks installed skills first, then searches web. Scores candidates against operator profile. Flags top pick. Never auto-approves. |

## Requirements

`/ask-board`, `/improve-system`, `/ingest-resource`, and `/research-drills` expect a `knowledge/` folder in your project. They work within the [Experiment Drill 26](https://github.com/este3v2/experiment-drill-26) operator OS structure but adapt to any project with a `knowledge/profile.md`.

`/prompt-rewriter` works standalone — no project structure required.

## Part of Experiment Drill 26

These skills are documented as free + paid operator tools in the [Experiment Drill 26 Substack series](https://substack.com).
