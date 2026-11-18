# TC Kratt

*Internal project in development. A Claude Opus session has run tests against Kratt. The first complete builder–auditor cycle through the harness is still ahead.*

Kratt is a local software-engineering harness for running AI-assisted repository work with explicit permissions, durable records, and independent review. I set the acceptance criteria and decide which actions require approval. **Permission to execute a job and the decision to accept its result are separate records.**

## How a job runs

- **Start from a known repository revision.** A repository-backed attempt works in a separate Git worktree with a recorded base commit. Its changes stay available for review alongside a bounded status and diff snapshot.
- **Set permissions and budgets before execution.** The operator chooses the worker and the job's limits. Kratt checks tool permissions during the run and records sensitive actions that need approval.
- **Keep an execution record.** A local SQLite ledger stores attempts, tool activity, evidence, approvals, and outcomes. Interrupted work remains visible so the operator can reconcile it after a restart.
- **Review an exact result.** An auditor can be assigned to a specific evidence snapshot. The evaluation records the verdict and findings against that snapshot, so a later correction can be traced back to the finding that prompted it.

## What I wanted to evaluate

A test count alone says little about whether a patch satisfies the original task. I designed Kratt to link the acceptance criteria, the worker's output, and the auditor's findings. That is the evidence I want to use when deciding whether to accept the work or send it back for correction.

## Project status

The private Python repository contains the execution ledger, worktree and evidence handling, and approval workflow. The operator dashboard is being extended, and repository bootstrap remains experimental. Kratt is an internal project at TCalvion Tech.

*Steve Jensen · TCalvion Tech OÜ*
