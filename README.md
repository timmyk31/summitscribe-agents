# SummitScribe for AI agents

Plugins that connect AI coding agents and assistants to [SummitScribe](https://summitscribe.app), so they can read your meeting notes, transcripts and action items.

Every package points at the same remote MCP server, `https://summitscribe.app/api/mcp`, and carries the same skill. All tools are read-only. There's no local server and no code to run.

## Before you install

Cursor and Gemini CLI sign you in through your browser the first time they connect. You approve the connection on summitscribe.app, pick which data it can read, and can disconnect it later in Account settings, then Developer & agents, under Connected apps. You don't need a token for them.

For Claude Code, OpenClaw and the config snippets, create a token at [summitscribe.app](https://summitscribe.app) in Account settings, then Developer & agents. Give it the `mcp:read` scope plus the data scopes you want (`meetings:read`, `notes:read`, `transcripts:read`, `actions:read`, `search:read`). Use a separate token for each tool so you can revoke one without breaking the others.

Keep the token in the tool's secret prompt or in the `SUMMITSCRIBE_TOKEN` environment variable. Don't paste it into a chat or commit it. If you think it leaked, revoke it at summitscribe.app.

## Install

**Claude Code**

```
/plugin marketplace add timmyk31/summitscribe-agents
/plugin install summitscribe@summitscribe
```

Claude Code asks for your token when you enable the plugin and keeps it in secure storage.

**Cursor**

Install SummitScribe from the Cursor Marketplace, or copy this repository's `cursor` folder to `~/.cursor/plugins/local/summitscribe` and run **Developer: Reload Window**. The first time Cursor connects, it opens summitscribe.app so you can approve it. Browser sign-in needs port 8787 free. If it's busy, or sign-in fails, add the server with a token instead, using the Cursor snippet at [summitscribe.app/developers/agents](https://summitscribe.app/developers/agents).

**Gemini CLI**

```
gemini extensions install https://github.com/timmyk31/summitscribe-agents
```

The first time Gemini connects, it opens summitscribe.app in your browser so you can approve it. Run `/mcp auth summitscribe` if it doesn't.

Other tools (VS Code, Codex, OpenClaw, Hermes, Muse) need only a config snippet. See [summitscribe.app/developers/agents](https://summitscribe.app/developers/agents).

## Data

When your agent calls a tool, the meeting content it reads goes to that agent's vendor, under that vendor's terms. See the [SummitScribe privacy policy](https://summitscribe.app/privacy).

## Support

Email info@summitscribe.app. Report security issues the same way.

This repository is generated from SummitScribe's source; pull requests aren't merged here.
