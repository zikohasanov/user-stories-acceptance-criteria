# User Stories & Acceptance Criteria

> Self-initiated portfolio exercise using a fictional pickup-ordering product. It contains no real client requirements or employment claims.

Stories are vertical slices tied to explicit outcomes and testable behavior. They cover menu discovery, cart configuration, submission, staff decision, status lookup, and exception handling. [Stories and acceptance criteria](stories.md) includes Given/When/Then scenarios, priorities, traceability, and a concise ready/done agreement.

## Prioritization rationale

Must stories make a safe, usable request-and-decision loop possible. Secure status lookup and staff state controls belong in the first release because a customer-facing order reference alone is not enough to protect data or coordinate fulfilment. Pilot metrics are Should because they support learning but do not block a small operational trial.

## Refinement prompts

Before implementation, confirm the review timeout, notification channel, legal notice wording, tax calculation, contact-data retention, and staff permissions. These are decisions for stakeholders, not facts hidden inside the story text.
