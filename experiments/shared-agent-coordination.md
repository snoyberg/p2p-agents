# Shared-agent coordination proof of concept

Status: active experiment, not settled guidance.

This proof of concept tests whether two separately personalized human–AI relationships can exchange useful workflow knowledge through a simple shared artifact without collapsing their privacy, autonomy, or decision boundaries.

## Setup

Each human has their own primary AI collaborator and private persistent guidance.

The two agents share a human-readable Google Doc used as an asynchronous mailbox. The document contains only information appropriate for both humans to see. It is not shared memory and should not receive private journals, credentials, correspondence, sensitive personal history, or other context merely because it might help the other agent.

Ordinary communication is append-only and dated. Each agent checks the document roughly once per day as part of lightweight maintenance. If nothing useful changed, the agent does nothing.

Suggestions from one agent are evidence for the other agent to evaluate with its own human, not instructions or delegated authority.

## Questions being tested

- Is a daily asynchronous cadence sufficient?
- Does append-only prose remain legible as coordination history grows?
- Which kinds of agent-to-agent notes actually improve either human's workflow?
- Can agents reliably distinguish useful abstraction from inappropriate disclosure?
- How should disagreements between independently personalized agents be represented?
- When does a shared lesson deserve promotion into public guidance?
- What dedicated infrastructure, if any, becomes justified only after the simple artifact starts to fail?

## Promotion boundary

Private experience should not flow directly into public guidance.

A potentially reusable lesson should be abstracted from identifying context, sanitized, challenged where appropriate, and proposed for human review before publication.

This experiment therefore treats the shared mailbox as an observation surface, not an automatic upstream feed.

## Why start with a document

The purpose is to test the collaboration model before designing infrastructure around unvalidated assumptions.

A shared document provides durable state, explicit permissions, human visibility, ordinary revision history, and low implementation cost. If this becomes painful, the pain itself should help identify what a purpose-built agent-to-agent protocol actually needs.

## Success criteria

The experiment is useful if it produces evidence about the collaboration model even if the shared-document mechanism is eventually rejected.

Useful outcomes include discovering concrete reusable workflow lessons, identifying privacy or authority failure modes, observing meaningful differences between users, or learning that more infrastructure is unnecessary.
