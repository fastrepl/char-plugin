# Char for agents

<img src="plugins/char/assets/icon.png" width="96" height="96" alt="Char">

Official Char plugin for Codex, Claude Code, Cursor, and compatible agents. Search and read the pages you explicitly share through Char's hosted MCP service.

## Setup

1. In Char, open **Settings → Account → Cloud access for agents**.
2. Select pages and choose **Share selected pages**. This uploads copies that Char and authorized agents can read, separately from encrypted device sync.
3. Install the plugin and sign in to Char when the agent requests access.

Agents can read uploaded pages while Char is closed. Updates upload from the publishing desktop while Char is running. The cloud plugin does not require a local CLI or MCP process.

## Codex

```sh
codex plugin marketplace add fastrepl/char-agent-plugin
codex plugin add char@fastrepl-char
```

Start a new task after installation so Codex loads the plugin.

## Claude Code

```text
/plugin marketplace add fastrepl/char-agent-plugin
/plugin install char@fastrepl-char
```

## Cursor and other clients

This repository includes a Cursor marketplace manifest and a portable plugin at [`plugins/char`](plugins/char). For direct MCP configuration:

```json
{
  "mcpServers": {
    "char": { "type": "http", "url": "https://char.com/api/mcp" }
  }
}
```

The shared skill can also be installed from [`plugins/char/skills/char`](plugins/char/skills/char).

## Tools and data

- `get_status` reports sharing status and the last upload time.
- `search` finds shared cloud pages.
- `export_page` returns a page snapshot as Markdown without changing it.

These tools are read-only. Only selected pages are uploaded; attachment files and recordings are excluded. Results include `publishedAt` so agents can report freshness. Local deletion removes a cloud copy on the next successful upload. **Turn off and delete cloud copies** revokes sharing when the server confirms it. Signing out stops updates but does not delete existing cloud copies.

See [setup](plugins/char/skills/char/references/setup.md) and [MCP inputs](plugins/char/skills/char/references/mcp.md). The [local CLI](plugins/char/skills/char/references/cli.md) remains a separate optional workflow for local data and editing.

Version 0.2.0 replaces the local stdio connection used by 0.1.x. Existing installations must update the plugin and complete Char OAuth sign-in.
