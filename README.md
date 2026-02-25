# twitter-influencer-skill

Draft Twitter/X posts in influencer style (e.g., @sweatystartup) using Cursor skills, with optional Twitter API + xAI Grok context.

> **Repo excerpt (GitHub About text):**
> Cursor skill to generate influencer-style Twitter/X posts with optional Twitter API and Grok context.

## What this repo is

This repository contains a Cursor-compatible skill at:

- `.cursor/skills/twitter-influencer-skill/`

The skill helps generate punchy, niche-relevant tweet drafts with hooks, style constraints, and @mention handling.

## Features

- Influencer-style tweet drafting (1–3 variants)
- Optional personalization from likes/tweets (if API creds are provided)
- Optional trend/sensitive-topic context via xAI Grok
- Clean secret handling with `.env.example` (no real tokens in repo)

## Repository structure

```text
twitter-influencer-skill/
├── .cursor/
│   └── skills/
│       └── twitter-influencer-skill/
│           ├── SKILL.md
│           ├── examples.md
│           └── references/
│               ├── api-usage.md
│               └── influencers.md
├── .env.example
├── .gitignore
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
├── README.md
└── SECURITY.md
```

## Installation

```bash
git clone https://github.com/ProfTrader/twitter-influencer-skill.git
cd twitter-influencer-skill
```

Then open this folder in Cursor, or copy `.cursor/skills/twitter-influencer-skill` into your target project.

## Configuration

Optional credentials are listed in `.env.example`.

- `TWITTER_BEARER_TOKEN` (or OAuth 1.0a token set)
- `XAI_API_KEY`

Use local `.env` only. Never commit secret values.

## Usage

In Cursor, ask for:

- “Write a tweet in @sweatystartup style about ___”
- “Give me 3 controversial hooks for ___ under 280 chars”
- “Draft mention-ready tweet for @handle on ___”

## Documentation

- Contribution guide: `CONTRIBUTING.md`
- Security reporting: `SECURITY.md`
- Conduct: `CODE_OF_CONDUCT.md`
- Version history: `CHANGELOG.md`

## License

MIT — see `LICENSE`.
