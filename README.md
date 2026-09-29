# Vault private skills

This repository contains one small entrypoint skill. It does not contain private skill packages, account data, or credentials. The private skills stay in the authenticated Vault library.

## Install private skills

Set up Vault Go on the machine where the agent runs:

```sh
npm install -g vault-go@latest
vault-go setup
```

Sign in to the Vault account that has access to the private skills. Once the `vault-go` npm release includes the `skills` command, run:

```sh
vault-go skills list
vault-go skills install --all
```

The second command installs the real private packages in `~/.agents/skills`. Use `--skill <name>` instead of `--all` to select one skill. As of September 29, 2026, the code is on Vault Go's `main` branch but npm still serves `0.30.0`, which does not include this command. The public entrypoint below works with the existing Vault Go MCP tools while the npm release is pending.

## Optional agent entrypoint

Install the public entrypoint when you want the agent to guide selection and updates:

```sh
npx --yes skills add https://github.com/resolveup-cloud/vault-skills --skill vault-private-skills --global --agent universal -y
```

Restart the agent and ask it to use `vault-private-skills` to list and install the skills you choose. Vault Go checks package integrity and preserves existing skills that it did not install.

The person installing a private skill can read its installed files. Give access only to accounts and machines you trust. Installing this entrypoint does not grant access to the Vault account.

## Local check

Before publishing, run `npx --yes skills add . --list` to check that the installer discovers the entrypoint.
