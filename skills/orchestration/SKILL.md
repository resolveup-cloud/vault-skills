---
name: orchestration
description: >-
  Coordinate supervised Vault Desktop workers: threaded messages, blocking ask/reply,
  task dispatch, worker_done/escalation waits, task DAGs, decision gates,
  coordinator loops, and decomposing work across agents. Use `vault-cli` for full
  ownership handoffs — "hand off", "handoff", "handover", "give this to another
  agent", "another worktree" — unless asked to supervise, monitor, or coordinate
  a DAG, and for terminal control, lightweight terminal prompts, shell commands,
  Vault Desktop worktree management, and reading or waiting on terminals. Use Computer
  Use for external browser windows, webviews, Vault Desktop app UI, or desktop UI outside
  Vault Desktop's embedded browser only when the task requires OS/window-level control
  such as focus, menus, dialogs, coordinates, or screenshots. Use `vault-cli` for
  Vault Desktop's embedded pages and a page-automation tool such as Playwright or CDP for
  external pages.
---

# Vault Desktop Orchestration

This file is a discovery stub, not the usage guide. The full, version-matched Vault Desktop
orchestration reference is served by the `vault-desktop` binary itself — kept out of this file on
purpose so it can never drift from the binary that will actually run your commands.

Engage Vault Desktop orchestration whenever you need structured multi-agent coordination: threaded
messages, blocking ask/reply flows, task dispatch, worker_done/escalation waits, task DAGs,
decision gates, coordinator loops, or decomposing work across agents. Use the vault-cli skill
instead for full ownership handoffs ("hand off", "handoff", "handover", "give this to
another agent", "another worktree") when the user did not ask to supervise, monitor, wait
for results, or coordinate a DAG — and for ordinary terminal control, shell commands,
worktree management, and the built-in browser. Coordination requires real Vault Desktop runtime
state; never substitute a non-Vault subagent tool.

## Resolve the CLI for this session

Choose the executable once and reuse it for every later command:

- If the `VAULT_CLI_COMMAND` environment variable is set, use its value. Vault Desktop exports this
  for managed WSL sessions.
- Otherwise, in a dev checkout whose session exposes `VAULT_DEV_REPO_ROOT`, use `vault-desktop-dev`.
- Otherwise, on Linux outside a Vault-managed terminal, use `vault-ide`. That is the registered
  Linux command; `vault-desktop` is normally not on `PATH` there.
- Otherwise, use `vault-desktop`.

Never run a bare `vault` command: it usually resolves to HashiCorp Vault's CLI, not to
Vault Desktop.

Below, `VAULT` is a placeholder for the executable you resolved. Substitute it before
running anything; do not create a shell variable or run `VAULT` literally. This works the
same way in POSIX shells, PowerShell, and cmd.exe.

If the selected executable cannot run, report its exact error and stop. Do not fall through
to another executable, which could silently target a different Vault Desktop build.

## Load the version-matched guide before running Vault Desktop commands

```text
VAULT skills get orchestration
```

That prints the compact, version-matched guide for the exact binary that will handle your
next commands. It covers the normal local coordinator loop. For a conditional action gate
such as remote placement, uncertain release recovery, or expanded DAG work, load only the
reference that gate names with
`VAULT skills get orchestration --reference references/<file>.md`
(`--references` lists the names). If that binary rejects `--reference`, run
`VAULT skills get orchestration --full` and read the named bundled reference before acting.

Prefer `--json`. Use the selected executable's `--help` for commands or flags the guide does
not cover. If a command reports that Vault Desktop is not running, start it with `VAULT open --json`
and retry. If `skills get` is unknown, explain that updating Vault Desktop restores the guide; use
`--help` for read-only discovery and do not guess unsupported commands.
