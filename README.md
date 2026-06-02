# Explain Non Tech

`explain-non-tech` is a Claude Code plugin that helps developers explain technical work to non-technical stakeholders.

It turns features, merge requests, pull requests, tickets, architecture changes, bug fixes, and code snippets into clear documentation for Product Managers, clients, executives, marketing, managers, sales, QA, and customer support.

## What it provides

- A Claude Code skill: `explain-feature`
- A slash command file: `commands/explain-feature.md`
- Audience-aware explanations for clients, Product Managers, executives, marketing, QA, support, sales, and managers
- Complexity levels: Basic, Detailed, and Executive Summary
- Merge Request and Ticket modes
- Plain-language analogies
- Technical glossary support for terms like JWT, cache, API, queue, and database
- Copy-ready output for Notion, Jira, GitLab, GitHub, Slack, and email

## Installation

Clone or copy this plugin directory, then load it locally with Claude Code:

```bash
claude --plugin-dir .
```

If you are launching Claude Code from a parent directory:

```bash
claude --plugin-dir ./explain-non-tech
```

Validate the plugin before publishing or sharing:

```bash
claude plugin validate . --strict
```

## Usage

Claude Code namespaces plugin skills by plugin name. In plugin mode, invoke the skill as:

```text
/explain-non-tech:explain-feature audience=Product Manager complexity=Detailed
```

Then paste a feature description, MR, PR, ticket, architecture note, bug fix, or code snippet.

This repository also includes `commands/explain-feature.md` for teams that copy the command into a standalone `.claude/commands/` setup, where it can be invoked as:

```text
/explain-feature audience=Client complexity=Basic
```

## Examples

Feature explanation:

```text
/explain-non-tech:explain-feature audience=Marketing complexity=Basic
We added cookie consent preferences with separate analytics and marketing toggles.
```

Merge Request explanation:

```text
/explain-non-tech:explain-feature audience=Product Manager complexity=Detailed
MR: Add passwordless login flow using one-time email links. Changed auth controller, email template, and login page.
```

Ticket explanation:

```text
/explain-non-tech:explain-feature audience=QA complexity=Detailed
Jira ABC-123: Users should be able to export filtered orders as CSV from the orders dashboard.
```

See the example files:

- `examples/feature-example.md`
- `examples/bugfix-example.md`
- `examples/mr-example.md`

## Screenshots

Place screenshots here when publishing:

- `docs/screenshots/plugin-list.png` - Plugin visible in Claude Code
- `docs/screenshots/explain-feature-command.png` - Command invocation example
- `docs/screenshots/notion-output.png` - Example explanation pasted into Notion

## Plugin structure

```text
explain-non-tech/
|-- .claude-plugin/
|   `-- plugin.json
|-- skills/
|   `-- explain-feature/
|       `-- SKILL.md
|-- commands/
|   `-- explain-feature.md
|-- README.md
`-- examples/
    |-- feature-example.md
    |-- bugfix-example.md
    `-- mr-example.md
```

## Output format

The skill always generates:

1. What is this feature?
2. Why do we need it?
3. What problem does it solve?
4. How does it work?
5. What changes for the user?
6. What remains unchanged?
7. Risks and edge cases
8. Real-world example
9. Non-technical summary

Merge Request mode also adds a technical summary, non-technical summary, business impact, and risks.

Ticket mode also adds a requirement summary, user impact, and expected outcome.

## Future roadmap

- Notion-specific output templates
- Release note mode
- Customer support macro mode
- Sales enablement mode
- Localization presets for multilingual stakeholder updates
- Optional repository-aware examples generated from real diffs
- Screenshot and diagram prompt templates
