# Learnings: Agent Operating Layer

Source: Tech-tonic Chronicles #24, "7 Layers, 11 Lessons: Inside the Agent Operating Layer"

## Core Architecture

A harness-based agent is not a chatbot or a monolithic AI app. It is an operating layer made of small parts that each do one job well.

The practical stack:

1. Thin harness: runs the model loop, manages context, enforces safety, and stays out of the way.
2. Skills: markdown files that carry domain knowledge, workflows, terminology, judgment, and team-specific playbooks.
3. Tools and MCPs: deterministic execution layers for APIs, databases, files, browser automation, and other repeatable operations.
4. Resolver: routes the user request to the right skills before tools are called.
5. Memory: captures what worked, what failed, user corrections, and accumulated team context.
6. Heartbeat: wakes on a schedule, checks whether something needs attention, and nudges only when signal crosses threshold.
7. Output skills: turn analysis into usable artifacts such as PowerPoint, Word, Excel, and PDF.

The operating principle: keep the harness thin, push intelligence into skills, push execution into deterministic tools.

## Lessons

### 1. The intelligence layer matters more than the metrics dump

Connecting data is the easy part. Encoding how a team interprets that data is the real work.

A useful agent should not only answer, "What are the metrics?" It should answer:

- What changed?
- Why does it matter?
- How does this compare to last quarter or peer accounts?
- What anomaly does not fit the pattern?
- What should we do next?

Judgment often lives outside databases: in emails, chats, meeting notes, stakeholder behavior, and prior team context. Building this layer requires stakeholder interviews, workflow observation, and encoding domain judgment into skills.

### 2. Skills let the operating layer grow horizontally

Once core plumbing exists, new team workflows should usually become skill files, not new platform features.

Examples:

- Monthly Business Review skill
- Renewal-prep skill
- Account-readiness skill
- Campaign post-mortem skill
- OKR report-out skill

The team can own the workflow by editing plain English instructions. This makes the system community-extensible without central engineering becoming the bottleneck.

### 3. Output should be artifacts, not chat bubbles

Users usually want something they can edit, present, send, or manipulate.

Useful outputs include:

- PowerPoint decks
- Word documents
- Excel workbooks
- PDFs
- Review packs
- Customer briefs

Artifact quality changes trust. A generic AI-looking deck gets discounted. An on-brand artifact that follows the team's templates and language gets taken seriously.

### 4. The heartbeat makes the agent proactive

A coworker does not wait to be asked every time. The agent should periodically check for important changes and nudge only when needed.

Good heartbeat checks include:

- renewal within 60 days and usage trending down
- stalled deal with no recent activity
- executive escalation still open
- customer commitment coming due
- industry or competitor news affecting a top account
- stakeholder silence after an important thread

The hard part is not scheduling. The hard part is calibration: threshold, frequency, relevance, and noise control.

### 5. Teach the agent how to think, not just how to query

Better results came from adding reasoning skills, not only better models.

Useful reasoning patterns:

- MECE issue trees
- hypothesis-driven investigation
- coverage checks
- "what would have to be true" tests
- disconfirming evidence
- confidence and caveat reporting

A strong agent does not just show a dashboard. It forms a point of view, tests it, shows its work, and says what would change its mind.

### 6. When a skill grows, make it a folder

A skill may start as one `SKILL.md`, but it should become a folder when it accumulates too much knowledge.

Good pattern:

```text
skill-name/
  SKILL.md
  references/
    glossary.md
    query-patterns.md
    examples.md
    edge-cases.md
```

Keep the main skill concise. Move detailed examples, glossaries, playbooks, templates, and edge cases into references that are loaded only when needed.

### 7. Memory turns the agent into a living system

The agent should learn from repeated failure patterns.

Capture:

- wrong skill routes
- hallucinated metrics
- user corrections
- stale business rules
- missing context
- tool failures
- poor artifacts
- approval mistakes

Then close the loop by updating skills, tools, resolver rules, or memory policies. Without this loop, the agent remains a snapshot of day-one knowledge.

### 8. Browser automation bridges missing APIs

Many internal systems do not have usable APIs. Some APIs are blocked, incomplete, or slower than the UI.

Playwright-style browser automation can bridge the gap:

- log in
- click through workflows
- scrape reports
- download files
- validate UI flows

Treat this as a bridge, not the ideal long-term integration. UI automation is brittle and should be isolated in dedicated skills or scripts.

### 9. Use multiple model passes for high-stakes work

For routine work, one model pass is fine. For high-stakes outputs, disagreement is useful signal.

Use independent passes for:

- leadership summaries
- renewal recommendations
- customer-facing narratives
- strategic decisions
- ambiguous analysis

Compare where the passes agree and diverge. If they disagree, show the disagreement instead of pretending certainty.

### 10. Trust boundaries decide when the agent stops

A coworker knows when to ask before acting. The agent should too.

Gate actions that:

- cannot be undone
- go to customers or external audiences
- reach senior leaders
- affect money, contracts, permissions, policy, or production systems
- use sensitive information in a new context

Routine, reversible internal work can flow autonomously. Irreversible or visible actions should be staged for human approval.

### 11. Adoption is the longest mile

The technology may work before the team trusts it.

Adoption requires:

- user research by persona
- workflow observation
- reliability over time
- correction loops
- artifact quality
- clear ownership
- repeated successful use in real rituals

People do not switch from trusted manual workflows because a demo was impressive. They switch when the agent reliably helps with work they already need to do.

## Short Version For Agents

When building an agent operating layer:

- Keep orchestration thin.
- Put domain judgment in skills.
- Use deterministic tools for execution.
- Route before acting.
- Remember corrections.
- Nudge only on meaningful signal.
- Produce artifacts, not just answers.
- Use browser automation when APIs are missing.
- Use multiple passes when stakes are high.
- Ask before irreversible or visible actions.
- Treat adoption as an ongoing calibration loop.

## Share Note

People used to say nobody reads long articles anymore. Turns out agents do.

If you want Codex, Claude Code, or your favorite agent to ingest the learnings from my Agent Operating Layer build, point it at this Markdown file and let it do the reading.
