---
name: explain-feature
description: Explain features, merge requests, pull requests, tickets, architecture changes, bug fixes, and code snippets to non-technical stakeholders.
argument-hint: "[audience] [Basic|Balanced|Detailed|Executive Summary] [feature, ticket, MR, PR, code, or context]"
---

# Explain Feature

Turn technical work into a clear, detailed, stakeholder-ready explanation. The output should be easy for non-technical people to understand while preserving the real intent, impact, limitations, and risk of the work.

Use the provided arguments and conversation context:

```text
$ARGUMENTS
```

## Core behavior

Generate an explanation automatically from the available context. If details are missing, state reasonable assumptions briefly instead of blocking on questions. Do not invent business impact, timelines, metrics, or customer behavior that is not supported by the context.

Prefer plain language over jargon. Avoid implementation details unless they are needed to explain user impact, risk, compliance, security, or operational behavior.

Format the answer so it can be pasted into Notion, Jira, GitLab, GitHub, Slack, email, release notes, or stakeholder documentation.

## Detect the mode

Before writing, identify the most likely mode from the input:

- Feature mode: new or changed product capability.
- Merge Request mode: merge request, pull request, diff, changed files, commits, review notes, or code changes.
- Ticket mode: Jira/GitLab ticket, issue, user story, acceptance criteria, requirement, bug report, or support request.
- Bug Fix mode: defect, regression, broken behavior, error, incident, hotfix, patch, or root cause.
- Architecture mode: system design, infrastructure, data flow, integration, queue, cache, database, service split, migration, or scalability change.
- Code Snippet mode: pasted code, function, class, endpoint, configuration, SQL, or script.

If multiple modes apply, combine them. For example, an MR that fixes a ticket should use Merge Request mode and include Ticket mode details when useful.

## Detect the audience

Adapt wording to the intended audience. If no audience is provided, use a balanced tone for Product Managers and general business stakeholders.

- Client: focus on value, reliability, what changes for their users, reassurance, and any required action from them. Avoid internal process details.
- Product Manager: focus on user problem, scope, acceptance, user-visible behavior, tradeoffs, dependencies, and release risk.
- Executive: focus on outcome, business impact, risk, operational effect, customer value, and decision relevance. Keep wording concise.
- Marketing: focus on customer benefit, positioning, launch-friendly phrasing, what can be safely claimed, and what should not be overstated.
- QA engineer: focus on expected behavior, unchanged behavior, edge cases, regression areas, and test scenarios.
- Customer support or sales: focus on how to explain the change to customers, common questions, limitations, and escalation triggers.

## Detect complexity level

Support these levels:

- Basic: shorter explanation, simplest language, one analogy if useful, minimal technical terms.
- Balanced: detailed enough for stakeholders, but avoid very long explanations unless the user asks for Detailed. Keep each section short, use one paragraph per section, and only add a glossary if needed.
- Detailed: full explanation with context, assumptions, impact, risks, glossary, and practical example.
- Executive Summary: compact, business-oriented version. Keep the required section headings but make each section brief.

If no complexity is provided, use Balanced: detailed enough for stakeholders, but avoid very long explanations unless the user asks for Detailed.

## Required output sections

Always produce these sections in this order:

### 1. What is this feature?

Explain what was built or changed. For Balanced, use one short paragraph. For Detailed, use one to three paragraphs depending on the complexity of the work.

### 2. Why do we need it?

Explain the business need, customer need, operational need, compliance need, or product reason.

### 3. What problem does it solve?

Describe the pain point in non-technical terms. Make clear what was difficult, risky, slow, confusing, manual, unreliable, or missing before.

### 4. How does it work?

Explain the behavior in simple language. Avoid code-level details unless necessary. Use a practical analogy when it improves understanding.

Example analogy style:

> Think of it like a receptionist checking visitors before allowing entry.

### 5. What changes for the user?

Explain user-visible impact: new screens, flows, messages, permissions, speed, reliability, steps, restrictions, or outcomes.

### 6. What remains unchanged?

Explain what is not affected. Include unchanged user flows, permissions, data, integrations, behavior, pricing, or existing functionality when relevant.

### 7. Risks and edge cases

Explain limitations, uncertainty, dependencies, rollout risks, data risks, permission risks, browser/device concerns, operational considerations, or uncommon cases.

### 8. Real-world example

Use one practical scenario that shows the change in action for the detected audience.

### 9. Non-technical summary

Provide an executive-ready summary suitable for managers. This should be clear enough to paste into a status update.

## Merge Request mode

When the input is a merge request or pull request, add this short block before the required output sections:

### Merge Request Snapshot

- Technical summary: Explain what changed in developer-friendly but still concise terms.
- Non-technical summary: Explain the change without code details.
- Business impact: Explain why the change matters for users, operations, revenue, risk, support, or product goals.
- Risks: Explain review, rollout, testing, dependency, migration, or regression concerns.

Then continue with the required nine sections.

## Ticket mode

When the input is a Jira, GitLab, GitHub, Linear, or support ticket, add this short block before the required output sections:

### Ticket Snapshot

- Requirement summary: Explain what the ticket is asking for.
- User impact: Explain who benefits and how their experience changes.
- Expected outcome: Explain what should be true when the ticket is complete.

Then continue with the required nine sections.

## Technical glossary

If technical terms are unavoidable, add a `Technical glossary` section after the non-technical summary. Only include terms that appear in the explanation or source context.

Use simple definitions like these:

- API: A structured way for one system or app to talk to another.
- Cache: A temporary storage area that helps information load faster.
- Database: The organized place where the application stores important information.
- JWT: A secure digital pass that helps prove who a user is after they log in.
- Queue: A waiting line for background work that does not need to happen immediately.

## Quality rules

- Be accurate, specific, and calm.
- Do not overpromise results that are not in the input.
- Do not expose sensitive implementation details unless the user asks for them.
- Prefer "people using the app" or "users" over "end users" unless the context uses that phrase.
- Prefer "the system checks" over "the backend validates" unless the audience is technical enough.
- Mention assumptions only when they materially affect the explanation.
- If the input includes code, explain what the code accomplishes rather than line-by-line syntax.
- If the input includes a bug fix, explain what was broken, what was fixed, and what users should notice now.
- If the input includes architecture, explain the moving parts using everyday language and business impact.
