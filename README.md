<p align="center">
  <img src="agent-task-workspace/assets/agent-task-workspace_circular.png" alt="Agent Task Workspace" width="140">
</p>

<h1 align="center">Agent Task Workspace Skill</h1>

<p align="center">
  <img alt="AI Agents - Skill" src="https://img.shields.io/badge/AI--Agents-Skill-EF9035?style=flat">
  <a href="LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/License-MIT-blue?style=flat"></a>
  <a href="https://www.linkedin.com/in/wolfgang-muhsal-12408194/"><img alt="LinkedIn" src="https://img.shields.io/badge/Contact-LinkedIn-95a5a6.svg?style=flat"></a>
</p>

Agent Task Workspace is an agent skill for Codex and other AI coding assistants. It creates and maintains durable, task-local records for tickets and other documented work: purpose, rationale, investigation findings, decisions, changes, outcomes, scripts, reports, and reproducible evidence.

It is useful for individual tickets completed in one session as well as for long-running tickets, audits, migrations, and recurring analyses. A future agent can connect a ticket number or Git commit to the context behind a change instead of inferring everything from commit messages alone.

## Installing Agent Task Workspace

Install the skill with `npx`:

```bash
npx skills add https://github.com/Gucky/AgentTaskWorkspace --skill agent-task-workspace
```

To install it globally for Codex:

```bash
npx skills add https://github.com/Gucky/AgentTaskWorkspace --skill agent-task-workspace --agent codex --global
```

For a specific agent:

```bash
npx skills add https://github.com/Gucky/AgentTaskWorkspace --skill agent-task-workspace --agent claude-code
```

For all supported agents:

```bash
npx skills add https://github.com/Gucky/AgentTaskWorkspace --skill agent-task-workspace --agent '*'
```

## Using Agent Task Workspace

In Codex, trigger the skill directly:

```text
$agent-task-workspace
```

Or ask naturally:

```text
Use Agent Task Workspace to document this ticket, including its rationale, investigated alternatives, final change, verification, and related commit IDs.
```

The skill helps agents to:

- document the purpose, rationale, decisions, changes, and outcome of short or long-running tasks;
- connect ticket IDs and Git commits to their underlying investigation and implementation context;
- keep scripts, reports, caches, and run records with the task they support;
- ask whether generated task artifacts should be tracked, excluded, or kept temporary; and
- retain enough provenance for future agents to refresh evidence safely.

## Scope and Safety

The skill keeps task artifacts outside the source tree and adapts to existing repository rules. A project may choose to document every AI-assisted ticket, including small ones. Before creating or retaining caches, run output, downloaded inputs, build products, or other generated artifacts as repository content, the skill checks the project's ignore rules and asks whether they should be tracked, excluded, or kept temporary. It does not store secrets or oversized captures, and does not replace project documentation with operational notes.

## Requirements

- Node.js for `npx` installation
- An AI coding assistant that supports agent skills

## License

Agent Task Workspace was created by [Wolfgang Muhsal](https://github.com/Gucky). It is available under the [MIT License](LICENSE).
