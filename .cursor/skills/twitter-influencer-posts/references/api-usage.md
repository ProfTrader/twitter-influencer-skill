# Twitter API and Grok API usage

This skill uses Twitter API and Grok API to learn from the user's likes and tweets (whom to offend/not, posting style) and to get trending/sensitive topics when drafting in social-engineering style.

**User must supply:** API credentials and the target user ID (or handle; resolve handle → ID first).

---

## Twitter API (X)

**Base:** https://api.twitter.com/2/

**Auth:** OAuth 1.0a user context or OAuth 2.0. User must supply credentials (e.g. bearer token or OAuth keys).

**Resolve handle → user ID:**

- `GET /2/users/by/username/:username` — returns `data.id` for the user.

**Liked tweets (what the user endorses):**

- **Endpoint:** `GET /2/users/:id/liked_tweets`
- **Query params:** `max_results` (5–100), `pagination_token`
- **Use for:** Infer what the user endorses, tone preferences, and whom they are less likely to want to offend.
- **Rate limits:** e.g. 75 requests per 15 min; check project-level monthly caps.

**User's tweets (posting style and boundaries):**

- **Endpoint:** `GET /2/users/:id/tweets`
- **Query params:** `max_results` (5–100), `pagination_token`, `exclude` (e.g. retweets)
- **Use for:** Infer posting style, topics, whom they attack vs. support, profanity level, political range.
- **Rate limits:** Check current X Developer docs.

---

## Grok API (xAI)

**Use for:** Real-time or trend-aware context when the skill needs **trending topics** or **sensitive/controversial topics** (style rule 1: controversial take from trending/sensitive topic).

**Base URL:** https://api.x.ai/v1 (confirm in current xAI docs)  
**Models:** e.g. `grok-2`, `grok-3` — check xAI for current model names.

**User must supply:** API key if they want the agent to call Grok for trends/sensitive-topic context. Otherwise use user-provided trend list or manual topic input.

---

## Workflow summary

1. **Resolve handle → ID** (if user gave a handle): `GET /2/users/by/username/:username`.
2. **Fetch recent likes:** `GET /2/users/:id/liked_tweets` (e.g. 20–50 tweets).
3. **Fetch recent tweets:** `GET /2/users/:id/tweets` (e.g. 20–50 tweets).
4. **Infer:** Whom the user supports vs. criticizes, tone, profanity level, political range, grammatical/colloquial patterns → "offend vs. not offend" boundaries and style.
5. **Optional:** Call Grok (or use user-provided list) for current trending/sensitive topics.
6. **Draft** applying the seven style rules and the chosen influencer profile.
