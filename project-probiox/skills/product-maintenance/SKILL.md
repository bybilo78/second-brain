---
name: product-maintenance
description: Use when maintaining probiox product quality and backlog.
version: 1.0.0
author: probiox
license: Proprietary
metadata:
  hermes:
    tags: [probiox, product, maintenance, backlog, quality]
    related_skills: [test-driven-development, requesting-code-review]
---

# Product Maintenance

## When to Use
Use for recurring probiox product upkeep: triaging defects and requests, reviewing product documentation, preparing maintenance work, or checking release readiness.

## Workflow
1. **Establish context.** Inspect the relevant project files, current product documentation, and existing issue/backlog records. Treat those as the source of truth; do not assume product behavior or roadmap details that are not documented.
2. **Classify the work.** Separate defects, usability improvements, feature requests, documentation gaps, and operational/release concerns. Record the observed evidence and user impact.
3. **Prioritize transparently.** State impact, urgency, scope, dependencies, and uncertainty. Recommend a priority with a short rationale; do not silently change an official roadmap or backlog.
4. **Define the next step.** For implementation work, write a concise problem statement and testable acceptance criteria. Identify affected areas and risks before editing. Use the relevant development/testing skill when code changes are requested.
5. **Make only authorized changes.** Draft proposals freely, but obtain the user's approval before consequential product, roadmap, release, external-service, or user-visible changes. Never publish or deploy without explicit approval.
6. **Verify and record.** Run appropriate checks for any change, report actual results, and update the relevant project documentation or maintenance log only when the project has an established place for it.

## Output
For a triage or maintenance review, summarize:
- finding and evidence;
- user/product impact;
- recommended priority and rationale;
- proposed action and acceptance criteria;
- open questions, dependencies, or risks.

Keep recommendations distinct from confirmed facts. Do not invent incidents, metrics, product behavior, or completion status.