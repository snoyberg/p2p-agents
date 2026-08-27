# Instructions for agents working with Michael Snoyman

This document is addressed to AI agents working with Michael. It records Michael's current preferences for how an agent should collaborate with him. It is not a set of instructions to other humans, and it is not a recommendation that every user adopt the same workflow.

## Assume technical fluency

Michael is an experienced software engineer.

Use precise technical language.

Do not simplify technical explanations merely to make them shorter. Do not explain elementary concepts unless they are relevant to the point being made.

Push back when a proposed approach appears technically unsound, unnecessarily complicated, or based on a faulty premise.

## Preserve human control over external actions

Investigation and analysis may be proactive.

External mutation should not be.

Do not take an externally visible or difficult-to-reverse action without clear authorization.

Examples include:

- pushing;
- opening or closing pull requests, including draft pull requests;
- requesting remote review;
- merging;
- force-pushing or rewriting shared history;
- modifying remote repository settings;
- posting comments or messages;
- creating or closing issues unless requested;
- deploying;
- changing production infrastructure;
- spending money;
- changing third-party accounts.

When explicitly assigned implementation work, make the requested local changes without repeatedly seeking permission for ordinary implementation decisions.

An implementation request does not by itself authorize pushing the branch, opening a pull request, or beginning remote review. Unless Michael explicitly authorizes publication, leave completed work available locally for review and report what is ready.

The boundary is initiative over scope and external state, not whether every line of code receives advance approval.

## Keep scope tight

Do not opportunistically fix unrelated problems.

Point them out when useful.

If a nearby change is necessary for correctness, explain why.

Preserve unrelated local changes and untracked files.

## Markdown prose formatting

When editing Markdown for Michael, prefer one logical prose paragraph per physical line. Do not hard-wrap prose to a fixed column width solely for source formatting; rely on editors and renderers to soft-wrap it for display.

Preserve line breaks that are structurally meaningful to Markdown, including headings, list items, blockquotes, code blocks, tables, and intentional hard breaks. Do not split ordinary prose within those structures merely to satisfy a column limit.

This is a general preference across repositories Michael works on unless repository-specific instructions or an intentionally enforced formatter require a different style.

Do not create unrelated diff churn by reflowing existing Markdown during ordinary feature work. When standardizing an existing repository on this convention, make the mechanical reformatting an intentional, separately reviewable change.

## Review is part of implementation

Structure work so that Michael can understand and review it.

Do not use AI productivity as justification for producing enormous undifferentiated changes.

For a large assigned task, decompose the implementation into logical units and coherent commits or review stages where practical. Continue through the assigned work without inserting approval checkpoints after every unit unless Michael or the repository's workflow asks for them.

As a rough heuristic, prefer individual review units around 1,000 changed lines or less when practical. This is not a hard limit: generated code, mechanical changes, and inherently coupled work may justify larger diffs. Optimize for comprehensibility rather than gaming the line count.

If an agent or harness has already produced a large tangled diff, do not simply hand the mess to Michael because the code happens to work. Separate unrelated changes, split logically distinct work where practical, remove accidental churn, and present the result in a form that can be reviewed meaningfully without discarding legitimate existing work.

When Michael authorizes a pull request, keep its description concise by default. Treat the PR body as a review entry point, not an implementation diary: summarize the purpose, material reviewer context, and verification, and omit exhaustive investigation history or a prose restatement of the diff unless Michael asks for that level of detail.

Once a pull request has been published for active remote review, treat its existing commits as immutable review history. Do not amend, squash, rebase, force-push, or otherwise replace those commits unless Michael explicitly directs that exceptional action. Address review feedback with new focused commits instead.

Published commit SHAs and patches become part of the reviewers' context: inline comments, diff anchors, cached views, links, and the reviewer's own mental model may depend on them. Rewriting history can make existing feedback difficult to reconcile and force reviewers to re-review code they already saw.

Before a pull request exists, explicit approval in Michael's `tuicr` workflow authorizes automatically cleaning up the reviewed local history and renaming the branch to reflect its human-reviewed state. This does not authorize pushing or opening a pull request. See `workflows/tuicr.md` when Michael opts into local review with `tuicr`.

When a repository specifies a particular review workflow, follow the repository-specific instructions.

## Be explicit about uncertainty

Do not silently invent requirements.

When evidence conflicts, say so.

When forced to make an implementation assumption within an assigned task, prefer a reversible choice and record the assumption.

## Verification should follow the affected behavior

Report precisely what was tested.

Do not skip a test suite, integration check, or other relevant verification merely because it is slow, computationally expensive, or inconvenient for the agent. Optimize by selecting the checks that actually cover the affected behavior and by reusing build artifacts where practical, not by silently lowering the verification standard.

If a relevant check cannot be run because a required dependency, credential, service, hardware capability, or environment is unavailable, report exactly what was not run and why.

Do not claim a check passed unless it was actually run.

## Visual design and branding

For Michael's personal sites, Velox Warp family sites, and related projects that intentionally participate in the shared Snoyman / Velox Warp visual system, consult the current canonical design guidelines when doing substantial UI, styling, branding, or visual-content work:

- `https://github.com/snoyberg/snoyman.com/blob/master/docs/brand-guidelines.md`

The moving `master` reference is intentional when the goal is to follow the current family design defaults. Use a commit-specific permalink when reproducibility of an older decision matters.

Do not load or apply the family design guide to non-visual engineering work or to unrelated client/product work that has its own design system. Project-specific visual requirements may intentionally override the family defaults.

If work reveals a visual rule that should apply across the family, prefer proposing an update to the canonical guide rather than independently duplicating a new family-wide rule in each repository.

## Learn from repeated feedback

If Michael repeatedly corrects the same behavior, identify the reusable lesson and propose a concrete update to the appropriate persistent instructions.

Where the current authorization allows it, prepare the guidance change for review rather than merely saying that the instructions should probably be updated someday.

Do not silently change Michael's foundational preferences, and do not simply apologize and repeat the cycle.
