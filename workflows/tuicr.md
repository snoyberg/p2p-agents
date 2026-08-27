# Local review with tuicr

This is an optional workflow for agents working with Michael Snoyman.

Use it when Michael says he is reviewing with `tuicr`, asks for a local commit-range review workflow, or a repository explicitly opts into this process. Do not assume every task should use `tuicr`.

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

After Michael explicitly approves the candidate, automatically finalize the reviewed local work before offering publication:

- squash the candidate and its review-fix commits into one clean commit when there is more than one;
- rename an `agent/` branch to a descriptive name without that prefix;
- report the finalized branch and commit;
- offer to push the branch and open a pull request.

Approval authorizes this local finalization because it completes the review workflow and makes the branch's name reflect its human-reviewed state. It does not authorize publication: wait for Michael to explicitly authorize the push and pull request.

## After a pull request exists

Once the branch has been published as an active pull request, treat its existing commit history as immutable review context.

Do not amend, squash, rebase, force-push, or otherwise replace commits on the active PR unless Michael explicitly directs that exceptional action.

Address subsequent review feedback with new focused commits.

Remote reviewers may have inline comments, diff anchors, cached views, links, or a mental model tied to the existing commit SHAs and patch history. Rewriting published history can invalidate that context, make comments difficult to reconcile, and force reviewers to re-evaluate code they already reviewed.

A squash merge performed by GitHub at the end of review is different: it may produce a clean single commit on the target branch without destroying the review history of the PR while the review is active.

## Keep the workflow proportional

This document describes the ordinary one-candidate-at-a-time workflow.

Do not invent elaborate branch stacks, immutable queues, or multi-branch review machinery for a simple task. If a large batch of independently reviewable changes needs a more complicated queueing workflow, agree on that structure explicitly or follow repository-local guidance.
