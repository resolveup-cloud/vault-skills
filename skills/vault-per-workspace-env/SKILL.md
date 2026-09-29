---
name: vault-per-workspace-env
description: >-
  Set up, review, debug, or validate a Vault Desktop per-workspace environment recipe: the
  on-demand, disposable runtime (cloud sandbox, VM, SSH host, or local container)
  Vault Desktop creates fresh for each workspace. Use to stand up a new recipe end to end,
  fix an `environmentRecipes` entry in `vault.yaml`, scaffold provider lifecycle
  scripts, or resolve an `vault-desktop vm recipe doctor` failure. Use `vault-cli` for
  ordinary worktree and workspace creation with no recipe involved.
---

# Per-Workspace Environments

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
VAULT skills get vault-per-workspace-env
```

Prefer `--json`. Use the selected executable's `--help` for commands or flags the guide does
not cover. If a command reports that Vault Desktop is not running, start it with `VAULT open --json`
and retry. If `skills get` is unknown, explain that updating Vault Desktop restores the guide; use
`--help` for read-only discovery and do not guess unsupported commands.
