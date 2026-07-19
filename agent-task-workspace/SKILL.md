---
name: agent-task-workspace
description: Create, maintain, or review task-local records for AI-agent work. Use when a task or ticket should preserve its purpose, rationale, investigation, decisions, changes, evidence, outcome, or links to related commits, whether the work is short or spans many sessions.
---

# Agent Task Workspace

Use this skill to give documented AI-agent work a durable, task-local record without mixing plans, investigation notes, scripts, reports, or outcomes into the source tree. A task workspace explains not only what changed, but why it changed and how the result was reached.

Follow applicable project instructions first. If the project already has a task location, file naming scheme, retention policy, or index convention, preserve it.

## Decide When to Create a Workspace

Create a task workspace whenever a task should leave durable context for a future person or agent. It is appropriate for a ticket completed in one session as well as for a long-running investigation, audit, migration, or recurring workflow.

Do not treat short duration as a reason to omit a workspace. If the project wants every AI-assisted ticket or change documented, create one workspace per ticket. Use a ticket-oriented name when one exists, such as `.agent/tasks/projectkey-1234-improve-search/`.

For an informal question or a change the project explicitly does not need to retain, a workspace may be unnecessary. Let the project's documentation policy decide, not an assumption that the work was too small.

## Create a Task-Local Record

Use the project's established workspace root. The recommended layout is `.agent/tasks/<task-name>/`, with a lowercase kebab-case folder name.

Choose only the files the task genuinely needs:

- `brief.md` or `plan.md` for the original purpose, scope, constraints, expected outcome, and ticket reference;
- `status.md`, `handover.md`, or an established equivalent for current state, verification, decisions, open questions, and next step;
- `findings.md` for durable investigation results, alternatives considered, and approaches rejected with their reasons;
- `outcome.md`, or a final outcome section in the status file, for the change summary, rationale, verification result, limitations, and relevant ticket or commit IDs;
- `scripts/` for task-specific reusable automation; and
- `reports/`, `runs/`, or `cache/` only when those artifacts are useful to retain, can be understood or refreshed later, and have an explicit Git-retention decision.

Do not force every task to contain every file. A short completed ticket might need only a brief and an outcome. A larger task can add findings, scripts, reports, and a continuing handover as needed.

## Preserve the Change Narrative

Record enough context that a future agent can connect a ticket or Git commit to the reasoning behind it:

- what problem, request, or expected behavior started the work;
- what mattered, constraints that shaped the solution, and what did not matter;
- investigation findings, alternatives considered, and approaches rejected or deferred, with their reasons;
- what changed in the project and why that approach was selected;
- relevant ticket IDs, commit IDs, pull requests, reports, or external evidence when available; and
- the outcome: verification performed, known limitations, unresolved questions, and the next step if the work is not complete.

Keep stable task intent and final decisions separate from changing progress notes. Do not make a future agent reconstruct the rationale from raw logs, chat history, or commit messages alone.

## Keep Artifacts Task-Local and Safe

- Keep task-specific scripts, reports, samples, and logs inside the task folder instead of a global `.agent/scripts/` or `.agent/reports/` catch-all.
- Prefer concise summaries over raw bulk output. Store a path or reproducible procedure for large captures rather than committing them by default.
- Do not store secrets, credentials, personal data, or machine-specific private paths unless the project expressly permits a safe, non-sensitive reference.
- Do not move application source code, production documentation, or unrelated work into the task workspace.
- Preserve historical report snapshots only when comparison over time is useful; otherwise regenerate volatile output when current state matters.

## Decide Git Retention for Generated Artifacts

Before creating or retaining a task-local `cache/`, `runs/`, generated report, build product, downloaded input, or intermediate artifact as repository content, inspect the project's existing Git and ignore rules.

- Track durable, human-readable task records and evidence only when they provide continuing value to the project.
- Treat downloaded caches, reproducible intermediate data, transient run output, and build products as a separate decision. They often do not belong in version control merely because they helped complete the task.
- If project policy does not clearly say whether an artifact should be tracked, excluded, or kept only temporarily outside the repository, ask the developer or user before creating it as persistent repository content.
- Do not add generated artifacts to Git, change `.gitignore`, or create task-specific ignore rules without that decision.
- When artifacts are excluded but useful during the task, document their purpose, source or generation procedure, and refresh path in the task record instead of committing the artifacts themselves.

## Maintain the Record

1. Re-read the task record before resuming or reviewing related work.
2. Update the record when a decision, approach, change, or verification result materially affects future understanding.
3. Keep prior evidence intact unless it is clearly superseded; state what replaced it and why.
4. On completion, leave a concise outcome that links the task's purpose, rationale, changes, verification, and relevant commits or tickets.
5. When investigating an old commit or ticket, search task workspaces by its identifier before relying on commit messages alone.

## Review Checklist

- The task workspace follows the project's documentation policy, regardless of whether the work was short or long-running.
- The folder name and location follow project conventions and include the relevant ticket ID when available.
- The record explains the purpose, constraints, rationale, changes, and outcome.
- Considered and rejected approaches are retained when they help prevent repeated work or incorrect reversions.
- Relevant tickets, commits, pull requests, evidence, and verification results are recorded where available.
- Scripts, reports, runs, and caches stay with the task they support.
- Retained derived artifacts include provenance or a refresh path.
- Generated artifacts have an explicit decision to track, exclude, or keep outside the repository.
- No secret, oversized capture, or unrelated source material entered the workspace.
- A future agent can understand past work without relying on chat history or commit messages alone.
