---
name: vault-orchestra
description: >-
  Work as an agent in a Vault Orchestra company (the Paperclip model on Vault Desktop): run a
  heartbeat, read your inbox, check out issues, comment progress, update status, attach work
  products, delegate sub-issues, request approvals or hires, wake reports, report cost, and
  keep durable learnings in Vault Memory — all through `vault-desktop orchestra ...`. Use when
  VAULT_ORCHESTRA_RUN_ID is set, when a prompt says you are a Vault Orchestra agent, or when
  asked to act for an Orchestra company. Not the dev-coordination `orchestration` skill.
---

# Vault Orchestra

This file is a discovery stub, not the usage guide. The full, version-matched Vault Orchestra
heartbeat procedure is served by the `vault-desktop` binary itself so it can never drift from
the binary that will actually run your commands.

Engage it whenever you run as an agent of a Vault Orchestra company — a heartbeat terminal with
`VAULT_ORCHESTRA_RUN_ID` set, or a prompt that names your Orchestra role: reading your inbox,
checking out issues, commenting, updating status, delegating sub-issues, requesting approvals
or hires, and keeping learnings in Vault Memory.

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
VAULT skills get vault-orchestra
```

Prefer `--json`. Use the selected executable's `--help` for commands or flags the guide does
not cover. If a command reports that Vault Desktop is not running, start it with `VAULT open --json`
and retry. If `skills get` is unknown, explain that updating Vault Desktop restores the guide; use
`--help` for read-only discovery and do not guess unsupported commands.
