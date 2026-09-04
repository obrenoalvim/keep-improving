# Keep Improving

[🇧🇷 Leia em Português](README.pt.md)

A Claude Code skill for continuous product improvement. Point it at a project and it stays on it: fixes bugs, writes missing tests, polishes UI and UX, and drafts features worth building.

---

## What it does

Each cycle: researches the product's domain, reads the codebase, finds what's broken or missing, applies what it safely can, and queues the rest for review.

**Safe changes go in right away, uncommitted:** a missing test for shipped code, a bug with a clear single cause, small UI/UX polish, missing alt text or aria labels, confirmed dead code.

**Sensitive changes go into `TODO IMPROVEMENTS.md`** with the category, source, exact files, reasoning, and risk. New features, layout changes, refactors that cross file boundaries, dependency bumps: all queued, none applied automatically.

The skill stops when you ask, or when there's genuinely nothing left to improve. If context runs out mid-cycle, it updates `TODO IMPROVEMENTS.md` so a new session can resume from there.

---

## The one rule that matters

This skill never runs `git commit` or `git push`. It edits files and leaves the diff sitting in your working tree. You review, you decide what ships, you run the commit yourself, no matter how small or obviously correct a change looks.

---

## Research tools

- **[last30days](https://github.com/mvanhorn/last30days-skill)** for the sentiment angle: what people actually say on Reddit, Hacker News, X, and GitHub about the product's domain or the stack in use.
- **[web](https://github.com/obrenoalvim/unblock)** for docs, changelogs, and best-practice references: a 13-tool fallback chain that keeps trying when a search or scrape gets blocked, rate-limited, or comes back empty.
- **[Scrapling](https://github.com/D4Vinci/Scrapling)** for full page content when a search snippet isn't enough: docs, changelogs, competitor products.

Installing keep-improving as a plugin auto-installs `last30days`. Without `last30days`, `web`, or `scrapling` installed, the skill still works and skips straight to a plain web search for that part.

---

## Use it

**No install needed:**
> "Read https://github.com/obrenoalvim/keep-improving and follow the Keep Improving skill."

**As a plugin (available in all sessions):**
```
/plugin marketplace add obrenoalvim/keep-improving
/plugin install keep-improving@keep-improving
```

Then invoke it: "Run Keep Improving on this project."

**Copy the skill file:**
Copy `skills/keep-improving/SKILL.md` into your skills directory and invoke through your skill system.

---

## Works with

Any codebase with a working tree to edit: web apps, CLIs, libraries, mobile, backend services. Needs git to leave changes uncommitted and diffable.
