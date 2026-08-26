# Local review with tuicr

This is a local-review workflow for agents working with Michael Snoyman.

Use it when Michael's active personal instructions make `tuicr` the default, when Michael says he is reviewing with `tuicr`, when he asks for a local commit-range review workflow, or when a repository explicitly opts into this process. Do not assume every user or every environment should use `tuicr`; Michael's current Codex-specific guidance opts into it by default unless he or the repository intentionally selects another workflow.

The purpose is to keep agent-generated work easy to inspect locally while preserving useful review history.

## Human-driven review

Michael normally runs `tuicr` himself and returns review comments to the agent.

Do not launch `tuicr`, inspect its sessions, or rely on its agent integration unless Michael explicitly asks for that. The useful contract is the commit range being reviewed, not control of the review UI.

After creating a candidate or review-fix commit, report the branch name, commit SHA, and exact commit range that Michael can review.

## Candidate and feedback cycle

Start with one coherent candidate commit for the unit of work being reviewed.

While that candidate is under local review:

- address feedback with new focused commits;
- do not amend or squash away the distinction between the original candidate and its review fixes;
- preserve unrelated local changes and untracked files;
- do not infer approval merely because all currently known comments have been addressed.

Wait for explicit approval of the candidate.

## Before a pull request exists

Local review history is provisional.

After Michael explicitly approves the candidate, history may be cleaned up when he asks for it. For example, the candidate and its review-fix commits may be squashed into one clean commit before publication.

Do not rewrite reviewed local history merely because a cleaner commit would look nicer. Approval and authorization to rewrite are separate decisions.

## After a pull request exists

Once the branch has been published as an active pull request, treat its existing commit history as immutable review context.

Do not amend, squash, rebase, force-push, or otherwise replace commits on the active PR unless Michael explicitly directs that exceptional action.

Address subsequent review feedback with new focused commits.

Remote reviewers may have inline comments, diff anchors, cached views, links, or a mental model tied to the existing commit SHAs and patch history. Rewriting published history can invalidate that context, make comments difficult to reconcile, and force reviewers to re-evaluate code they already reviewed.

A squash merge performed by GitHub at the end of review is different: it may produce a clean single commit on the target branch without destroying the review history of the PR while the review is active.

## Keep the workflow proportional

This document describes the ordinary one-candidate-at-a-time workflow.

Do not invent elaborate branch stacks, immutable queues, or multi-branch review machinery for a simple task. If a large batch of independently reviewable changes needs a more complicated queueing workflow, agree on that structure explicitly or follow repository-local guidance.
