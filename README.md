# Vault private skills

This repository contains one small entrypoint skill. It does not contain private skill packages, account data, or credentials. The private skills stay in the authenticated Vault library.

## Install

Set up Vault Go on the machine where the agent runs:

```sh
npm install -g vault-go@latest
vault-go setup
```

Sign in to the Vault account that has access to the private skills. Then install the entrypoint in the shared agent skills directory:

```sh
npx --yes skills add https://github.com/resolveup-cloud/vault-skills --skill vault-private-skills --global --agent universal -y
```

Restart the agent and ask it to use `vault-private-skills` to list and install the skills you choose. The agent downloads each selected package through the authenticated Vault Go MCP connection. Vault Go checks package integrity and will not overwrite a skill that it did not install.

The person installing a private skill can read its installed files. Give access only to accounts and machines you trust. Installing this entrypoint does not grant access to the Vault account.

## Local check

Before publishing, run `npx --yes skills add . --list` to check that the installer discovers the entrypoint.
