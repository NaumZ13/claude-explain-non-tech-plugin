# Explain Non Tech

`explain-non-tech` is a Claude Code plugin that helps developers explain technical work to non-technical stakeholders.

It turns features, merge requests, pull requests, tickets, architecture changes, bug fixes, and code snippets into clear documentation for Product Managers, clients, executives, marketing, managers, sales, QA, and customer support.

## Why this plugin exists

Developers constantly need to explain technical work to stakeholders.

Claude can already explain code, but the format often changes from conversation to conversation. This plugin provides a repeatable structure that generates stakeholder-ready explanations for features, merge requests, tickets, architecture changes, and bug fixes.

## What it provides

- A Claude Code skill: `explain-feature`
- A slash command file: `commands/explain-feature.md`
- Audience-aware explanations for clients, Product Managers, executives, marketing, QA, support, sales, and managers
- Complexity levels: Basic, Balanced, Detailed, and Executive Summary
- Merge Request and Ticket modes
- Plain-language analogies
- Technical glossary support for terms like JWT, cache, API, queue, and database
- Copy-ready output for Notion, Jira, GitLab, GitHub, Slack, and email

## Installation

### Local skill installation

Clone this repository, then copy the skill into your Claude Code skills directory.

macOS/Linux:

```bash
mkdir -p ~/.claude/skills
cp -R skills/explain-feature ~/.claude/skills/
```

Windows PowerShell:

```powershell
New-Item -ItemType Directory -Force -Path "$HOME\.claude\skills"
Copy-Item -Recurse -Force ".\skills\explain-feature" "$HOME\.claude\skills\"
```

Windows Command Prompt:

```cmd
mkdir %USERPROFILE%\.claude\skills
xcopy /E /I skills\explain-feature %USERPROFILE%\.claude\skills\explain-feature
```

Restart Claude Code after copying the skill.

### Plugin validation

This repository is structured as a Claude Code plugin. Before publishing or sharing it as a plugin, validate the manifest with your installed Claude Code CLI:

```bash
claude plugin validate . --strict
```

## Usage

After local skill installation, ask Claude Code to use the `explain-feature` skill:

```text
Use the explain-feature skill to explain this for non-technical stakeholders.
```

Then paste a feature description, MR, PR, ticket, architecture note, bug fix, or code snippet.

You can also specify audience and complexity:

```text
Use the explain-feature skill. audience=Client complexity=Basic
```

When installed as a namespaced plugin, invoke it as:

```text
/explain-non-tech:explain-feature complexity=Detailed
```

This repository also includes `commands/explain-feature.md` for teams that copy the command into a standalone `.claude/commands/` setup:

```text
/explain-feature complexity=Basic
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

## Example output

### 1. What is this feature?

This feature allows the product to detect when a visitor rejects cookies and automatically turn off personalization that depends on consent.

### 2. Why do we need it?

It helps the business respect privacy choices while still keeping the website usable for visitors who do not accept optional cookies.

### 3. What problem does it solve?

Without this, the site might continue using personalization behavior after a visitor has declined cookies, which could create compliance and trust concerns.

### 4. How does it work?

When a visitor makes a cookie choice, the system checks that preference before enabling personalization. Think of it like checking a guest list before giving someone access to a private room.

### 5. What changes for the user?

Visitors who reject optional cookies still see the website, but personalization features that rely on those cookies are disabled.

### 6. What remains unchanged?

Required website functionality stays available, and visitors who accept cookies can still receive the personalized experience.

### 7. Risks and edge cases

Legal or compliance teams should confirm the exact consent requirements for each region. QA should test both accepted and rejected cookie states.

### 8. Real-world example

A visitor declines marketing cookies. The site remembers that choice and avoids showing personalization that depends on those cookies.

### 9. Non-technical summary

This change helps the product respect cookie consent choices while keeping the website experience stable and understandable.

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

If no complexity is provided, the skill uses `Balanced` by default. Balanced keeps each section short, uses one paragraph per section, and only adds a glossary when technical terms are needed.

## Privacy

This plugin does not collect, transmit, store, or process user data outside of the local Claude Code session. It only provides prompt instructions and examples for explaining technical work.

## License

MIT License. See `LICENSE` for details.
