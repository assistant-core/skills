# Assistant Core skills

An [Agent Skill](https://agentskills.io) that teaches AI apps to manage your [Assistant Core](https://assistantcore.com) assistants through the Assistant Core MCP server: write and edit system prompts, set voice greetings and models, add knowledge, turn tools on or off, and improve answers from end-user feedback.

The MCP server gives the AI app the tools; the skill tells it how Assistant Core uses what it sets. For example, the platform adds format rules for each channel (voice, web widget, messaging) on its own, so a good system prompt leaves them out.

## Install

### Claude Code

One plugin installs both the MCP server and the skill:

```bash
claude plugin marketplace add assistant-core/skills
claude plugin install assistant-core@assistant-core
```

Then run `/mcp`, select the `assistant-core` server and choose **Authenticate**.

### Codex, Cursor, VS Code, Gemini CLI and other coding tools

1. Connect the MCP server: see [Coding tools](https://docs.assistantcore.com/en/assistant-core-mcp/coding-tools).
2. Install the skill:

   ```bash
   npx skills add assistant-core/skills
   ```

### Claude (web and desktop)

1. Connect the MCP server: see [Claude](https://docs.assistantcore.com/en/assistant-core-mcp/claude).
2. Download [assistant-core.zip](https://github.com/assistant-core/skills/releases/latest/download/assistant-core.zip).
3. In **Settings → Capabilities**, turn on code execution, then under **Skills** choose **Upload skill** and pick the zip.

## Use

Ask in your own words, for example:

- "Set up my assistant for the speaker at our spa front desk."
- "Look at last week's negative feedback and suggest fixes."
- "Check my assistant's setup and tell me what to improve."

Changes apply to your end users immediately. The skill has the AI app propose changes before making them, show you each prompt diff, and offer to undo a change.

## Contents

```
.claude-plugin/              Claude Code marketplace and plugin manifests
.mcp.json                    Assistant Core MCP server, for the plugin
skills/assistant-core/
  SKILL.md                   the skill
  references/system-prompt.md  how to write an assistant's system prompt
```

## Release

Bump `version` in `.claude-plugin/plugin.json`, then push a matching tag (`v1.0.1`). CI validates the skill and the plugin, and attaches `assistant-core.zip` to the GitHub release.

## License

[MIT](LICENSE)
