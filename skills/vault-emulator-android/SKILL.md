---
name: vault-emulator-android
description: >-
  Android device and emulator control from inside Vault Desktop over adb, with the live
  device view in Vault Desktop's emulator pane. Use when driving an adb-connected emulator
  or phone on Windows, Linux, or macOS: booting AVDs, taps, swipes, typing,
  hardware buttons, rotation, app install and launch, runtime permissions, the
  accessibility tree, and logcat. For an iOS simulator use the iOS emulator
  skill; build the APK with Gradle first.
license: Apache-2.0
---

# Vault Desktop Emulator (Android)

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
VAULT skills get vault-emulator-android
```

Prefer `--json`. Use the selected executable's `--help` for commands or flags the guide does
not cover. If a command reports that Vault Desktop is not running, start it with `VAULT open --json`
and retry. If `skills get` is unknown, explain that updating Vault Desktop restores the guide; use
`--help` for read-only discovery and do not guess unsupported commands.
