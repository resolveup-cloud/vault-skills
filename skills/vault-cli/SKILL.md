---
name: vault-cli
description: >-
  Operate Vault-managed worktrees, folder contexts, terminals, repos, automations, artifacts,
  skill sharing, worktree comments, and Vault Desktop's embedded browser through the `vault-desktop` CLI. Use
  when the user says "$vault-cli", "Vault Desktop worktree", "child worktree", "spawn codex/claude in a
  worktree", "read/wait/send Vault Desktop terminal", "handoff" / "handover" / "give this to another
  agent", "Vault Desktop browser", "vault-desktop artifacts", or "share skills". Prefer it over raw git
  worktree, ad hoc PTYs, or Computer Use when Vault Desktop state is involved. Use Computer Use only
  for external windows or desktop UI that needs OS-level control, and Playwright or CDP for
  external pages.
---

# Vault Desktop CLI

This discovery stub loads the version-matched guide from the Vault Desktop executable used for this session.

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
VAULT skills get vault-cli
```

Prefer `--json`. Use the selected executable's `--help` for commands or flags the guide does
not cover. If a command reports that Vault Desktop is not running, start it with `VAULT open --json`
and retry. If `skills get` is unknown, explain that updating Vault Desktop restores the guide; use
`--help` for read-only discovery and do not guess unsupported commands.
