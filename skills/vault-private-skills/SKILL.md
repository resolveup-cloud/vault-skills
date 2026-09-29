---
name: vault-private-skills
description: Use when the user wants to find, install, or update skills from their private Vault library in Codex, Claude, or Grok.
---

# Private Vault skills

The skill contents live in the user's authenticated Vault account. This entrypoint contains no private skill packages or credentials.

1. Check that the `vault-go` MCP tools are available. If they are missing, direct the user to run `vault-go setup` and sign in on this machine, then restart the agent. Never request or print an access token.
2. Use `vault_go_skills` to find available skills. Use `vault_go_skill_read` only when the user needs to inspect a particular skill before installation.
3. Install the selected skill with `vault_go_skill_install`. For Codex and other agents reading `~/.agents/skills`, set `targets: ["agents"]`; use `"claude"` or `"grok"` only when requested.
4. For updates, use `vault_go_skill_sync`. Set `currentProject: true` only when the user wants missing project-linked skills installed as well.
5. Report which skills and targets were installed or updated. If access is denied, explain that the account needs access to the private library; do not switch to a public copy.

Installation places the skill files on the target machine. Anyone with filesystem access there can read them, so install only on a machine the user trusts.
