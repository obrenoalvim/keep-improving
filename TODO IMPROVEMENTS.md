# TODO IMPROVEMENTS

> Last updated: 2026-09-12

## Pending Changes

### Dedup guidance for TODO IMPROVEMENTS.md entries
- **Category:** Refactor
- **What:** Add an explicit instruction to check existing `TODO IMPROVEMENTS.md` entries before appending a new one for a sensitive change, and skip/update instead of duplicating when the same file/issue is already queued.
- **Where:** `skills/keep-improving/SKILL.md`, "Sensitive changes — queue in TODO IMPROVEMENTS.md" section (around line 64-91)
- **Why:** The loop is designed to run many cycles unattended ("keeps going until the user says stop"). Nothing currently tells it to check for an existing entry before queuing a new one, so a long-running session could rediscover the same gap across cycles and append duplicate entries, bloating the file the user has to review.
- **Risk:** Behavior change to the skill's queuing logic — needs the maintainer to decide the exact matching rule (by file path? by title similarity?) rather than being guessed.
- **Effort:** Low

### Guidance for conflicting target-project instructions
- **Category:** Feature
- **What:** Add a note that when the target project has its own CLAUDE.md/AGENTS.md/CONTRIBUTING rules that conflict with keep-improving's safe/sensitive classification (e.g., a project rule "never touch generated files" or "always add tests"), the project's own rules take precedence.
- **Where:** `skills/keep-improving/SKILL.md`, near "Safe changes — apply directly to the working tree" (around line 50)
- **Why:** The skill currently classifies safe vs. sensitive purely on its own criteria with no mention of deferring to project-local conventions, which could cause it to "safely" apply a change a given project explicitly disallows.
- **Risk:** Adds a new precedence rule to core skill behavior — worth the maintainer's judgment call on wording and priority order.
- **Effort:** Low
