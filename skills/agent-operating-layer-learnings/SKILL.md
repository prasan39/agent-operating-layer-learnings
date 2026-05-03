---
name: agent-operating-layer-learnings
description: Apply practical lessons from building a harness-based agent operating layer: thin harness, fat skills, deterministic tools, resolver, memory, heartbeat nudges, artifact-first outputs, trust boundaries, and adoption calibration. Use when designing, reviewing, or improving coworker-style agents, agent harnesses, AI operating layers, or team workflow agents.
---

# Agent Operating Layer Learnings

Use this skill when building or improving an agent that should behave like a useful teammate inside a real business workflow, not just a chatbot.

## Core Architecture

Design the agent as a 7-layer operating stack:

1. **Thin harness**: runs the model loop, manages context, enforces safety, and avoids owning business logic.
2. **Skills**: markdown instructions that carry domain knowledge, workflows, terminology, judgment, and team playbooks.
3. **Tools and MCPs**: deterministic execution for APIs, databases, files, browser automation, and repeatable operations.
4. **Resolver**: routes the user request to the right skills before tools are called.
5. **Memory**: captures what worked, what failed, user corrections, and accumulated team context.
6. **Heartbeat**: wakes on a schedule, checks whether something needs attention, and nudges only on meaningful signal.
7. **Output skills**: turn analysis into usable artifacts such as PowerPoint, Word, Excel, and PDF.

Operating principle: keep orchestration thin, put intelligence in skills, and put execution in deterministic tools.

## Lessons To Apply

### 1. Build the intelligence layer, not just the metrics layer

Do not stop at usage, revenue, tickets, last touch, or health scores. Interpret the data.

For customer, partner, or account questions, answer:

- What changed?
- Why does it matter?
- How does this compare to last quarter or peer accounts?
- What anomaly does not fit the pattern?
- What should the user do next?

Use structured data and, when available, unstructured context such as email, chat, meeting notes, CRM notes, and prior stakeholder behavior.

### 2. Turn team workflows into skill files

Once core plumbing exists, new team workflows should usually become skills, not new platform features.

Good skill candidates:

- Monthly Business Review
- Quarterly Business Review
- renewal prep
- account readiness
- campaign post-mortem
- OKR report-out
- leadership update

Capture what the team cares about, the sections they expect, the metrics they trust, the risks they call out, and the artifact format they need.

### 3. Produce artifacts, not chat bubbles

Prefer outputs users can edit, present, send, or manipulate:

- PowerPoint decks
- Word documents
- Excel workbooks
- PDFs
- review packs
- customer briefs

Use the team's templates, brand style, language, and layout patterns when available. Artifact quality directly affects trust.

### 4. Use heartbeat nudges carefully

A proactive agent should check for important changes without becoming noisy.

Good heartbeat checks:

- renewal inside a risk window and usage trending down
- stalled deal with no recent activity
- unresolved executive escalation
- customer commitment coming due
- industry or competitor news affecting a top account
- stakeholder silence after an important thread

Only nudge when there is a clear signal and a useful next action.

### 5. Teach reasoning patterns

For ambiguous business questions, use reasoning skills instead of only queries.

Apply:

- MECE issue trees
- competing hypotheses
- coverage checks
- "what would have to be true" tests
- disconfirming evidence
- confidence and caveat reporting

The agent should form a point of view, test it, show its work, and explain what would change its mind.

### 6. Split large skills into folders

When a skill gets too large, keep `SKILL.md` concise and move details into references.

Use this pattern:

```text
skill-name/
  SKILL.md
  references/
    glossary.md
    query-patterns.md
    examples.md
    edge-cases.md
```

Load detailed references only when needed.

### 7. Create a memory improvement loop

Capture recurring failures and turn them into improvements.

Log:

- wrong skill routes
- hallucinated metrics
- user corrections
- stale business rules
- missing context
- tool failures
- poor artifacts
- missed approval gates

Then update skills, tools, resolver rules, or memory policies.

### 8. Use browser automation as a bridge

When APIs are unavailable, blocked, or incomplete, use browser automation for UI-only workflows:

- log in
- click through workflows
- scrape reports
- download files
- validate UI flows

Treat browser automation as a bridge, not the ideal long-term integration. Keep it isolated because UI workflows are brittle.

### 9. Use multiple passes for high-stakes work

For routine work, one model pass is fine. For high-stakes analysis, run independent passes and compare agreement.

Use this for:

- leadership summaries
- renewal recommendations
- customer-facing narratives
- strategic decisions
- ambiguous diagnosis

If the passes disagree, present the disagreement as a signal instead of hiding it.

### 10. Gate trust boundaries

Ask for explicit human approval before actions that:

- cannot be undone
- go to customers or external audiences
- reach senior leaders
- affect money, contracts, permissions, policy, or production systems
- use sensitive information in a new context

Routine reversible internal work can proceed autonomously. Irreversible or visible work should be staged for approval.

### 11. Treat adoption as calibration

The technical build may work before the team trusts it.

Adoption requires:

- persona-specific user research
- workflow observation
- reliability over time
- correction loops
- artifact quality
- clear ownership
- repeated successful use in real rituals

Do not rely on demos alone. Earn usage by helping with work people already need to do.

## Default Response Pattern

When asked to design or review an agent operating layer, respond with:

1. The current architecture read.
2. Which of the 7 layers are present or missing.
3. The top 3 risks.
4. Which lesson applies most strongly.
5. The next concrete improvement to make.

## Short Reminder

Keep the harness thin. Put judgment in skills. Put execution in tools. Route before acting. Remember corrections. Nudge only when useful. Produce artifacts. Gate irreversible actions. Calibrate adoption.

