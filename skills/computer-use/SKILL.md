---
name: computer-use
description: >-
  OS/window-level inspection and input in visible local app windows through `vault-desktop computer`:
  native apps, external browser windows (Chrome, Edge, Safari), and app webviews. Not for
  Vault Desktop's embedded browser (use `vault-cli`) or page-only automation (use Playwright or CDP).
---

# Computer Use

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
VAULT skills get computer-use
```

Prefer `--json`. Use the selected executable's `--help` for commands or flags the guide does
not cover. If a command reports that Vault Desktop is not running, start it with `VAULT open --json`
and retry. If `skills get` is unknown, explain that updating Vault Desktop restores the guide; use
`--help` for read-only discovery and do not guess unsupported commands.
