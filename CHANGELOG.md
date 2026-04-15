# Changelog

All notable changes to Self-Improving Agent are documented here.

Format: [MAJOR.MINOR.PATCH] — Date — Description

---

## [3.0.0] — 2025 — Initial Open Source Release

**Created by Joon Nyip (Koh)**

### New Features
- **🐟 Mirofish Enable** — Force-directed SVG knowledge graph. Claude finds semantic connections between learnings; nodes self-organize via physics simulation.
- **⚡ Skill Patterns** — Claude extracts reusable `When [X] → Do [Y] → Verify [Z]` templates from your learnings. Manual pattern creation also supported.
- **🤖 Claw Multi-Agent Improvement** — Four specialized agents (Error Detector, Skill Extractor, Pattern Builder, Optimizer) run in parallel via `Promise.all`. Coordinator agent synthesizes outputs into a prioritized plan.

### Core (inspired by pskoett/self-improving-agent)
- Learning capture with type classification: skill, error, correction, note
- Claude analysis per capture: severity, pattern, recommendation, tags
- Auto-extraction of patterns every 3 captures
- Activity feed with 12-item history
- Sidebar stats: learnings, patterns, errors

### Security & Quality Fixes
- **BUG-01** Fixed: Added `anthropic-version` header to all API calls
- **BUG-02** Fixed: API key modal with sessionStorage — enables standalone browser use
- **BUG-03** Fixed: XSS protection via `escapeHtml()` on all user-generated content
- **BUG-05** Fixed: `setInterval` stored and cleared on `beforeunload`
- **BUG-08** Fixed: Multi-agent coordinator card resets to hidden on re-run
- **BUG-09** Fixed: Pattern IDs use `String()` comparison — no float precision issues
- **BUG-11** Fixed: API response collects all text blocks, not just `content[0]`
- **STYLE-01** Fixed: `capturelearning` renamed to `captureLearning` (camelCase)
- Added `anthropic-dangerous-direct-browser-access: true` header for direct browser API access

### Developer Experience
- Single HTML file, zero build step, zero npm dependencies
- `'use strict'` mode throughout
- Structured state object `S` with clear ownership
- Cleanup on `beforeunload` (clearInterval, cancelAnimationFrame)
- Fixed Mirofish canvas uses internal 800×460 coordinate system — stable regardless of tab visibility

---

## Inspired By

- [self-improving-agent v3.0.13](https://clawhub.ai/pskoett/self-improving-agent) by [@pskoett](https://github.com/pskoett) — MIT-0 License
