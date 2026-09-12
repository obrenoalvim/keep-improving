# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

## [1.1.0] - 2026-09-04
### Added
- `web` skill (13-tool fallback chain) to the research tools, used for docs/reference lookups between `last30days` sentiment and `scrapling` full-page fetches.

## [1.0.0] - 2026-08-09
### Added
- Initial `keep-improving` skill: autonomous product-improvement loop with research via `last30days` and `scrapling`, safe changes applied to the working tree, sensitive changes queued in `TODO IMPROVEMENTS.md`, and the no-commit/no-push rule.
- Restructured as a proper plugin package: `.claude-plugin` manifest and marketplace entry, GitHub issue/PR templates, MIT license, CONTRIBUTING guide, `SKILL.md` nested under `skills/keep-improving/`, and bilingual README.
