---
name: twitter-influencer-skill
description: Writes Twitter/X posts in the style of specified influencers (e.g. Nick Huber @sweatystartup–style social engineering), with controversial takes, hooks, colloquial/grammar quirks, and correct @mentions. Uses Twitter API and Grok API to learn from the user's likes and tweets (whom to offend/not, posting style). Use when the user asks for tweet drafts, Twitter posts, influencer-style copy, Nick Huber style, social-engineering style, or to mention specific handles.
---

# Twitter influencer posts

## When to use

Apply this skill when the user asks for: a tweet, Twitter/X post, "in the style of X", Nick Huber style, @sweatystartup style, social-engineering style, or to mention @handles.

## Style source

- **Built-in influencer (e.g. Nick Huber)** → Read [references/influencers.md](references/influencers.md) and apply that profile. For social-engineering profiles, also apply the **seven style rules** below.
- **User provides sample tweets** → Follow "User-provided style" below; still apply the seven style rules if the user requested controversial/hook/colloquial style.

## Seven style rules (social-engineering / Nick Huber–style)

When using Nick Huber (@sweatystartup) or similar social-engineering style:

1. **Controversial take**: Base the tweet on a controversial take from the trending section or a sensitive topic.
2. **Profanity**: Use of profane language is allowed when it fits the voice.
3. **Political extremes**: Political extremes can be included where appropriate.
4. **Hook**: Every tweet must have a clear hook (opening that grabs attention).
5. **Grammar and colloquial**: Include intentional grammatical mistakes and colloquial writing (not polished corporate tone).
6. **Niche relevance**: Information must be fully relevant to the niche the user provides.
7. **Offend / do not offend**: Learn from the user whom they are willing to offend and whom they are not, by inferring from their posting style and—when available—from their likes and tweets via Twitter API (see [references/api-usage.md](references/api-usage.md)).

## Learning from the user

- **Prefer**: Fetch the user's recent likes and tweets via Twitter API. Infer boundaries (whom they support vs. criticize), tone, and grammar/colloquial patterns. Use Grok API (or user-provided trends) for trending/sensitive topics when needed. Full details: [references/api-usage.md](references/api-usage.md).
- **Fallback**: If APIs are not available, ask the user to paste a few sample tweets and likes, or describe "whom I'm okay offending vs. not", and infer from that.

**Workflow before drafting (social-engineering style):**

1. Obtain the account to write for (user's handle or ID).
2. If available, fetch recent likes and recent tweets via Twitter API; otherwise ask for sample likes/tweets or a description of boundaries.
3. Infer: whom the user tends to support vs. criticize, tone (profanity level, political range), grammatical/colloquial patterns.
4. Use Grok (or user-provided trend list) if needed for trending/sensitive topics.
5. Apply the seven style rules and generate drafts.

## User-provided style (no built-in profile)

1. From sample tweets (or API-fetched tweets), note: length, tone, sentence length, numbers/lists, hook vs CTA, punctuation, profanity level, political range.
2. Summarize 3–5 style traits and "offend vs. not offend" boundaries.
3. Draft using those traits and the seven style rules where applicable; keep under 280 characters and reserve space for @mentions.

## @mentions

- Use `@handle` (no space). Each character counts toward the 280 limit.
- Placement: opening (e.g. "@handle …"), inline, or end—whatever fits the line and reads naturally.
- For multiple mentions, account for total handle length; suggest trimming copy if needed.

## Output

- Provide 1–3 draft tweets, each under 280 characters, with mentions already placed.
- Note which influencer profile (e.g. Nick Huber @sweatystartup) and which rules were applied.

## References

- **Built-in profiles and style traits**: [references/influencers.md](references/influencers.md)
- **Twitter API and Grok API usage**: [references/api-usage.md](references/api-usage.md)
- **Examples**: [examples.md](examples.md)
