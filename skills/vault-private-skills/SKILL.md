---
name: vault-private-skills
description: Use when the user wants to find, install, or update skills from their private Vault library in Codex, Claude, or Grok.
---

# Private Vault skills

The skill contents live in the user's authenticated Vault account. This entrypoint contains no private skill packages or credentials.

1. Check that Vault Go is available and authenticated on this machine. If not, direct the user to install it and run `vault-go setup` or `vault-go login`. Never request or print an access token.
2. Check whether `vault-go --help` lists the `skills` command. If it does, run `vault-go skills list` to find available skills and `vault-go skills install --skill <name>` for the chosen skill, or `--all` when the user requests every skill. The default target is `~/.agents/skills`; use `--target claude` or `--target grok` when requested.
3. If the installed Vault Go lacks that command, use the existing MCP tools: `vault_go_skills` to list, `vault_go_skill_read` to inspect, and `vault_go_skill_install` to install selected skills. For Codex and compatible agents use `targets: ["agents"]`; for Claude or Grok select their respective targets. Tell the user if the MCP connection is unavailable and that a Vault Go npm release is pending.
4. Use `vault_go_skill_sync` to update installed skills when the MCP is available. Set `currentProject: true` only when the user wants missing project-linked skills installed as well.
5. Report which skills and targets were installed or updated. If access is denied, explain that the account needs access to the private library; do not switch to a public copy.

Installation places the skill files on the target machine. Anyone with filesystem access there can read them, so install only on a machine the user trusts.
