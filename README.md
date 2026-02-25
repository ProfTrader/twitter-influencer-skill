# Skills for AI

Cursor agent skills for specialized workflows. Use these skills inside [Cursor](https://cursor.com) to extend the AI with domain-specific behavior and instructions.

## Overview

| Item | Description |
|------|-------------|
| **Purpose** | Provide Cursor-compatible skills (`.cursor/skills/`) that agents can invoke for specific tasks. |
| **Audience** | Cursor users who want tweet drafting, influencer-style copy, or similar workflows. |
| **Requirements** | Cursor IDE. Optional: Twitter/X API and xAI Grok API credentials (user-supplied; see [Configuration](#configuration)). |

## Features

- **Twitter influencer posts** — Draft Twitter/X posts in the style of specified influencers (e.g. Nick Huber [@sweatystartup](https://x.com/sweatystartup)), with hooks, colloquial tone, and correct @mentions. Can learn from your likes and tweets when API credentials are provided.

## Repository structure

```
skills_for_ai/
├── .cursor/
│   └── skills/
│       └── twitter-influencer-skill/
│           ├── SKILL.md           # Skill definition and when to use
│           ├── examples.md        # Example outputs
│           └── references/
│               ├── api-usage.md   # Twitter API & Grok API usage (no secrets)
│               └── influencers.md # Built-in influencer profiles
├── .gitignore
├── CONTRIBUTING.md
├── README.md
└── .env.example                   # Optional env var names (no real credentials)
```

## How it works

1. **Skill discovery** — Cursor loads skills from `.cursor/skills/<skill-name>/`. Each skill has a `SKILL.md` with a YAML frontmatter (`name`, `description`) and instructions.
2. **When to use** — The agent uses the skill when the user asks for tweet drafts, influencer-style copy, or to mention specific handles. The skill can use built-in influencer profiles or user-provided samples.
3. **Optional APIs** — If the user supplies Twitter API and/or Grok API credentials (via environment variables or Cursor settings), the skill can fetch likes/tweets and trending context. **No API keys or secrets are stored in this repository.**

## Installation / setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/ProfTrader/skills_for_ai.git
   cd skills_for_ai
   ```

2. **Use in Cursor**
   - Open the cloned folder (or a project that includes it) in Cursor. Skills under `.cursor/skills/` are picked up automatically when the agent matches the skill’s description.
   - Alternatively, copy the `.cursor/skills/twitter-influencer-skill` folder into your own project’s `.cursor/skills/`.

3. **Optional: API access**
   - See [Configuration](#configuration). Credentials are **never** committed; use local `.env` or Cursor’s secret handling.

## Configuration

This repo does **not** contain any API keys, tokens, or other secrets. If you want the skill to call Twitter API or Grok API:

- Create a `.env` file in your project (or use Cursor’s recommended way to store secrets).
- Use the variable names listed in `.env.example` only as a reference. Set values locally; do not commit `.env`.
- See `.cursor/skills/twitter-influencer-skill/references/api-usage.md` for required endpoints and parameters. Credentials are always supplied by you.

## Usage

- **In Cursor:** Ask for a tweet, Twitter/X post, “in the style of Nick Huber” (or @sweatystartup), or request specific @mentions. The agent will apply the skill and return 1–3 draft tweets under 280 characters.
- **Without APIs:** You can paste sample tweets or describe “whom I’m okay offending vs. not”; the skill will infer style and boundaries from that.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for:

- Commit message format (standardized for GitHub)
- How to add or change a skill
- What not to commit (secrets, keys, tokens)

## License

See repository license file if present; otherwise all rights reserved.
