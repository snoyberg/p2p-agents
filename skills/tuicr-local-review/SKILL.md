---
name: tuicr-local-review
description: Use Michael Snoyman's opt-in local commit-range review and publication workflow. Trigger only when Michael or a project selects tuicr, local candidate commits, or commit-range review.
---

# Local review with tuicr

Michael runs `tuicr` himself and returns review comments to the agent. Do not launch `tuicr`, inspect its sessions, or rely on its agent integration. The useful contract is the commit range being reviewed.

## Universal workflow rules

- Refresh remote refs and branch from current `origin/main` or a verified equivalent before preparing a new candidate.
- Make a coherent local candidate commit. After every candidate or review-fix commit, report the branch name, full commit ID, and exact commit range for `tuicr`.
- Address feedback in new focused commits while review is active. Do not amend, squash, rebase, or otherwise rewrite commits under review unless Michael explicitly asks.
- Preserve unrelated local changes and untracked files.
- Wait for explicit candidate approval; resolved feedback is not approval.
- Do not push, open a pull request, request remote review, merge, or otherwise publish until explicitly authorized.
- Before a pull request exists, explicit candidate approval authorizes finalizing the reviewed local work: squash the candidate and its review-fix commits into one clean commit when there is more than one, rename an `agent/` branch to a descriptive name without that prefix, and report the final branch and commit. Then offer to push and open a pull request, but wait for explicit publication authorization.
- After a pull request exists, preserve published history. Use additive commits for subsequent review rounds; never amend, squash, rebase, force-push, or otherwise replace published commits.
- Do not merge an approved branch directly into the target branch. Let the hosting service merge it according to repository policy.

## One change at a time

Use this flow for one independently reviewed change:

1. Create a feature branch from the refreshed target branch and make one coherent candidate commit.
2. Add review fixes as separate commits and wait for explicit approval.
3. On explicit approval, squash the candidate and fixes into one clean commit without merging it, and rename the branch if needed to reflect its human-reviewed state.
4. Report the finalized branch and commit, and offer to publish it. Do not publish until explicitly authorized.
5. After merge, refresh the target branch and remove the local branch only when it is no longer useful.

## Ordered batch

Use this alternative only when Michael asks to prepare a long ordered batch before reviewing candidates individually:

1. Keep one persistent immutable all-changes branch containing the original ordered candidate stack. It is a queue and reference snapshot, not an integration branch or per-candidate review target.
2. For each review, create a fresh temporary branch from the current target branch and apply only the next original candidate. The temporary branch must not contain later candidates.
3. Put review fixes in separate temporary-branch commits. Leave the all-changes branch unchanged; apply an equivalent fix to a later candidate only while preparing that later candidate.
4. On explicit approval, squash the temporary candidate and fixes into one clean commit without merging it, rename the branch if needed, and offer to publish it. Do not publish until explicitly authorized.
5. Once the hosting service merges it, refresh the target branch, remove the completed temporary branch when no longer useful, and prepare the next original candidate on a fresh branch.
6. Record the last accepted original commit. If a candidate cannot stand on approved history without another unreviewed commit, stop and ask whether to combine or reorder them.
7. Report the all-changes branch, temporary review branch, original candidate commit, rewritten temporary commit, and exact review range after every transition.

If fixes change candidate boundaries or span queued commits, stop and ask Michael how to divide the work.
