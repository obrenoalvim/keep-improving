---
name: keep-improving
description: Autonomous product-improvement loop — researches, fixes bugs, writes missing tests, polishes UI/UX, and proposes new features, applying safe changes directly and queuing sensitive ones in TODO IMPROVEMENTS.md. Never commits or pushes without explicit approval.
when_to_use: when the user wants continuous, unattended improvement of a codebase/product until told to stop
version: 1.0.0
languages: all
---

# Keep Improving

> Research deep. Fix what's broken. Polish what's rough. Never commit without asking.

---

## What it does

When invoked, Keep Improving runs an autonomous loop over the current project:

1. Researches — real user sentiment via `last30days`, deep web/docs via `scrapling`, plus normal web search
2. Reads the project to understand stack, structure, existing tests
3. Looks for: failing/missing tests, bugs, rough UI/UX, dead code, outdated deps, feature gaps worth filling
4. Applies **safe changes** directly to the working tree — uncommitted
5. For **sensitive changes**, adds an entry to `TODO IMPROVEMENTS.md`
6. Reports the cycle: researched, found, applied, queued
7. Repeats — keeps going until the user says stop

**This skill never runs `git commit` or `git push`.** See "The commit rule" below — it is the one rule this skill cannot bend.

---

## Research tools

- **`last30days`** — real community signal (Reddit, HN, X, YouTube, GitHub) on the product's domain, competing tools, or complaints about the stack in use. Invoke it first each cycle for the sentiment angle.
- **`scrapling`** (Python lib, installed via pip) — undetectable scraping for pulling full doc pages, changelogs, competitor UIs, or anything a plain web search returns only snippets of. Use when you need the actual page content, not a search summary.
- Regular web search — official docs, GitHub issues, Stack Overflow, changelogs.

Priority per cycle: `last30days` for sentiment → web search for docs/guides → `scrapling` for anything behind a snippet or needing full-page content. Skip a tool silently if it is not installed; do not block the cycle on it.

---

## Reading before touching

**Never modify a file without reading it first.** For every file the skill might touch:
1. Read it completely
2. Understand what it does and why it is shaped that way
3. Decide: safe change (apply) or sensitive change (queue in TODO IMPROVEMENTS.md)

---

## Safe changes — apply directly to the working tree

Apply without asking when the change is additive, reversible, and does not alter existing behavior or structure:

- Adding a missing test for an existing, already-shipped code path
- Fixing a bug with a clear, single root cause and an obvious, narrow fix (see systematic-debugging skill for root-cause tracing)
- Small UI/UX polish: copy fixes, spacing/alignment, missing alt text, missing aria labels, obvious contrast fixes
- Removing dead code / unused exports confirmed unused by a grep across the repo
- Adding a code comment only where a non-obvious constraint would otherwise mislead the next reader

**Applied but not committed.** Every safe change stays as an uncommitted diff. The user reviews and commits when ready.

---

## Sensitive changes — queue in TODO IMPROVEMENTS.md

Anything that changes structure, architecture, public behavior, or requires a judgment call the user should weigh in on:

- New feature (any feature, no matter how small the diff)
- Changing an existing UI flow, layout, or navigation
- Refactors that touch more than one file's public interface
- Dependency upgrades/downgrades
- Anything where the "right" fix depends on product intent, not just code correctness

### TODO IMPROVEMENTS.md format

```markdown
# TODO IMPROVEMENTS

> Last updated: YYYY-MM-DD

## Pending Changes

### [Change title]
- **Category:** Bug / Test / UI-UX / Feature / Refactor / Dependency
- **Source:** [URL researched, if any]
- **What:** [Exactly what would change]
- **Where:** [File(s), line numbers when possible]
- **Why:** [What problem this solves / what it improves]
- **Risk:** [What could break, what needs a human call]
- **Effort:** Low / Medium / High
```

---

## The commit rule

**Never run `git commit`, `git push`, or anything that stages for a commit the user didn't ask for.** Edit files, leave the diff sitting there, move to the next thing. This holds regardless of how small, safe, or obviously-correct the change is.

**No exceptions:**
- "It's just a typo fix" — still not yours to commit
- "Tests pass now" — passing tests is not commit approval
- "The user asked me to improve the product" — improve ≠ commit
- "I'll batch everything into one commit at the end" — no batching either, no commits at all until asked
- "Uncommitted changes might get lost" — that is the user's call to make, not this skill's

| Excuse | Reality |
|--------|---------|
| "Just a typo fix" | Size doesn't grant commit authority. Still needs review. |
| "Tests pass now" | Passing tests ≠ approval to commit. |
| "User said 'improve the product'" | That's a mandate to edit, not to commit. |
| "I'll commit at the end of the loop" | Still a commit nobody asked for. Don't. |
| "It's safer committed" | Not this skill's call. Leave it in the working tree. |

### Red flags — stop before running git

- About to type `git commit` or `git add` with intent to commit
- About to type `git push`
- Thinking "I'll just save progress by committing"

**All of these mean: don't. Leave the diff. Report it. Move on.**

The loop only commits when the user's message explicitly says "commit" or "commit and push."

---

## Loop mechanics

After each cycle:
1. `last30days` (if available) for the sentiment/community angle on whatever area this cycle targets
2. Web search + `scrapling` (if needed) for docs, best practices, prior art
3. Read the relevant part of the project
4. Apply safe changes to the working tree, or add entries to `TODO IMPROVEMENTS.md`
5. Report the cycle (format below)
6. Pick the next target and repeat — do not pause between cycles or ask "should I continue?"

Stop only when one of these is true:
- The user says to stop
- There is nothing left to find, fix, or apply (rare — flag it explicitly, don't just go quiet)
- Context is running out — update `TODO IMPROVEMENTS.md` with current state so a new session can resume by reading it

---

## Reporting format

```
## Keep Improving — Cycle N

**Researched:** [last30days query / web search / scrapling target used]
**Found:** [what surfaced, with source URLs]
**Applied:** [files edited, one line each, why — uncommitted]
**Queued in TODO IMPROVEMENTS.md:** [entries added]
**Next:** [what the next cycle targets]
```

---

## Compatibility

Works on any codebase with a working tree to edit: web apps, CLIs, libraries, mobile, backend services. Requires git (to leave changes uncommitted and diffable) but never uses git beyond `status`/`diff` to inspect its own changes.
