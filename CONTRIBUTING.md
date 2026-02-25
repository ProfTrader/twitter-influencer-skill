# Contributing to Skills for AI

Thanks for considering contributing. This document covers commit standards, how to add or change skills, and how we handle sensitive information.

## Commit message format (standardized for GitHub)

We use **Conventional Commits** so history and release tooling stay consistent.

### Format

```
<type>(<scope>): <short description>

[optional body]

[optional footer(s)]
```

- **type** (required): One of:
  - `feat` — New skill or new user-facing behavior
  - `fix` — Bug fix in a skill or docs
  - `docs` — Documentation only (README, CONTRIBUTING, skill text)
  - `refactor` — Code or skill structure change, no behavior change
  - `chore` — Tooling, .gitignore, repo config

- **scope** (optional): e.g. `twitter-influencer-skill`, `readme`, `contributing`.

- **short description**: Imperative, lowercase start, no period. Max ~72 chars for the subject line.

### Examples

```text
feat(twitter-influencer-skill): add support for thread drafts
docs(readme): add installation and configuration section
fix(twitter-influencer-skill): correct character count in examples
chore: update .gitignore for env files
```

### Rules

- One logical change per commit.
- Keep the subject line clear and scannable in `git log` and on GitHub.
- Add a body when you need to explain *why* or reference an issue (e.g. `Refs #2`).

---

## How to add or change a skill

1. **New skill**
   - Create a folder under `.cursor/skills/<skill-name>/`.
   - Add `SKILL.md` with YAML frontmatter: `name`, `description`, and full instructions.
   - Optionally add `examples.md` and `references/` for long reference material.
   - Update the root `README.md` with a short description and link.

2. **Change an existing skill**
   - Edit the relevant files under `.cursor/skills/<skill-name>/`.
   - Keep examples and references in sync with `SKILL.md`.
   - Prefer `docs(...)` or `feat(...)` / `fix(...)` commits as appropriate.

3. **Pull requests**
   - Use a short, descriptive branch name (e.g. `docs/contributing`, `feat/thread-drafts`).
   - Follow the commit format above; squash only if requested by maintainers.

---

## Sensitive information — do not commit

**This repository must never contain:**

- API keys, bearer tokens, or OAuth secrets (Twitter/X, xAI Grok, etc.)
- Passwords or session tokens
- Private keys (`.pem` or similar)
- Any `.env` or `.env.local` files that hold real credentials
- User IDs, handles, or other PII that could identify a real account (use placeholders like `@handle`, `USER_ID` in docs)

**Safe to commit:**

- `.env.example` with **variable names only** and empty or placeholder values (e.g. `TWITTER_BEARER_TOKEN=`, `XAI_API_KEY=`)
- Documentation that describes *where* to get credentials and *what* to set, without actual values
- Example tweets or copy that are clearly generic or anonymized

**If you accidentally commit secrets:**

- Rotate or revoke the exposed credentials immediately.
- Do not force-push to “remove” the secret from history; it will still be in clones and caches. Prefer revoking and documenting the incident.

The project `.gitignore` already excludes `.env`, `.env.local`, and `*.pem`. Keep it updated if new secret-bearing patterns are introduced.
