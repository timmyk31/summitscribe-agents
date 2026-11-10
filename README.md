# SummitScribe for AI agents

Plugins that connect AI coding agents and assistants to [SummitScribe](https://summitscribe.app), so they can read your meeting notes, transcripts and action items.

Every package points at the same remote MCP server, `https://summitscribe.app/api/mcp`, and carries the same skill. All tools are read-only. There's no local server and no code to run.

## Before you install

Create a token at [summitscribe.app](https://summitscribe.app) in Settings, under Developer & agents. Give it the `mcp:read` scope plus the data scopes you want (`meetings:read`, `notes:read`, `transcripts:read`, `actions:read`, `search:read`). Use a separate token for each tool so you can revoke one without breaking the others.

Keep the token in the tool's secret prompt or in the `SUMMITSCRIBE_TOKEN` environment variable. Don't paste it into a chat or commit it. If you think it leaked, revoke it at summitscribe.app.

## Install

**Claude Code**

```
/plugin marketplace add timmyk31/summitscribe-agents
/plugin install summitscribe@summitscribe
```

Claude Code asks for your token when you enable the plugin and keeps it in secure storage.

**Cursor**

Install SummitScribe from the Cursor Marketplace, or add this repository as a plugin source. Then set `SUMMITSCRIBE_TOKEN` under Plugins, Configure.

**Gemini CLI**

```
gemini extensions install https://github.com/timmyk31/summitscribe-agents
```

Gemini asks for your token at install and keeps it in the system keychain.

Other tools (VS Code, Codex, OpenClaw, Hermes, Muse) need only a config snippet. See [summitscribe.app/developers/agents](https://summitscribe.app/developers/agents).

## Data

When your agent calls a tool, the meeting content it reads goes to that agent's vendor, under that vendor's terms. See the [SummitScribe privacy policy](https://summitscribe.app/privacy).

## Support

Email info@summitscribe.app. Report security issues the same way.

This repository is generated from SummitScribe's source; pull requests aren't merged here.
