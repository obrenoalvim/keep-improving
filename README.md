# keep-improving

Claude Code skill for continuous, unattended product improvement.

Read this in [Portuguese](README.pt-BR.md).

## About

You point this skill at a project and it stays on it. It researches what real users say about the product's domain, reads the codebase, fixes bugs, writes missing tests, cleans up rough UI and UX, and drafts new features worth building. It keeps cycling until you say stop.

Two research tools drive it. `last30days` pulls real sentiment from Reddit, Hacker News, X, and GitHub, so the skill knows what people actually complain about, not just what a generic search turns up. `scrapling` fetches full page content when a search snippet isn't enough, useful for docs, changelogs, and competitor products.

Every change lands in two buckets. Safe changes, small fixes, missing tests, minor polish, get applied straight to the working tree. Bigger calls, new features, layout changes, dependency bumps, get written up in `TODO IMPROVEMENTS.md` for you to decide on.

One rule sits above all the others: this skill never commits or pushes anything on its own. It edits files and leaves the diff sitting there. You review, you decide what ships, you run the commit. No exceptions, no matter how small or obviously correct a change looks.

## Tags

`claude-code` `agent-skill` `autonomous-agent` `code-review` `automation` `ai-agent` `developer-tools` `testing` `ux` `product-improvement`

## Files

- `SKILL.md`: the spec Claude reads when the skill runs
- `README.md`: this file (English)
- `README.pt-BR.md`: Portuguese version

## Use

Invoke the skill, point it at a project, let it run. It stops when you tell it to, or when it genuinely runs out of things to improve.
