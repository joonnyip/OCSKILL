# Contributing to Self-Improving Agent

Thank you for your interest in contributing! This project is a single-file HTML app — contributions are straightforward.

## How to Contribute

### Reporting Bugs

Open an issue with:
- Browser name and version
- Steps to reproduce
- Expected vs actual behavior
- Console errors (open DevTools → Console)

### Suggesting Features

Open an issue tagged `enhancement` with:
- What problem it solves
- Proposed behavior
- Any relevant examples

### Pull Requests

1. Fork the repository
2. Create a branch: `git checkout -b feature/your-feature-name`
3. Make your changes to `index.html`
4. Test in at least two browsers (Chrome + Firefox or Safari)
5. Verify all existing features still work:
   - [ ] Learning capture + Claude analysis
   - [ ] Mirofish toggle + graph builds correctly
   - [ ] Skill pattern extraction
   - [ ] Multi-agent run completes
   - [ ] API key modal saves and loads correctly
6. Submit a pull request with a clear description

## Code Style

- The app is intentionally a single HTML file — keep it that way
- Use `'use strict'` JavaScript
- Escape all user-generated content with `escapeHtml()` before inserting into DOM
- Keep CSS variables consistent with the existing `:root` definitions
- Function names: `camelCase`; CSS classes: `kebab-case`
- Comments in the `/* ── Section ─ */` style for major sections

## Security

- Never log or transmit API keys
- Always use `escapeHtml()` for any user input rendered in the DOM
- Do not add external script dependencies without discussion

## Questions

Open an issue or start a Discussion on GitHub.

---

*Created by Joon Nyip (Koh)*
