# Roadmap

This roadmap focuses the project on reusable, safe agent-skill patterns that can help small maintainers ship and review AI-assisted workflows without turning every repository into a custom prompt pile.

## Maintainer Workflow Goals

- Add prompt regression examples so changes can be reviewed consistently.
- Add issue triage guidance for bug reports, provider changes, and prompt-quality regressions.
- Add pull request review guidance for skill instructions, examples, and secret-handling changes.
- Add changelog and release-note templates for skill updates.
- Keep the repository usable without requiring contributors to expose personal API credentials.

## API Credit Use Cases

If API credits are available, they will be used for project maintenance and examples:

- Generate and compare output variants for prompt regression checks.
- Summarize issues and proposed fixes for maintainers.
- Draft changelog entries from merged pull requests.
- Review docs and examples for credential leaks or unsafe usage instructions.
- Produce reproducible examples for contributors without requiring each contributor to carry paid API usage.

## Near-Term Work

- Add a small prompt-regression fixture set.
- Add a documented manual review checklist for skill changes.
- Add example maintainer workflows for issue triage and release prep.
- Add CI checks for formatting, secret scanning, and markdown link health.

