# Char for agents

<img src="assets/icon.png" width="96" height="96" alt="Char">

Search and read the Char pages you explicitly share with agents. Claude Code, Codex, and Cursor use one hosted MCP service with Char account sign-in. The service is read-only and remains accessible while Char is closed.


## Setup

1. In Char, open **Settings → Account → Cloud access for agents**.
2. Select pages and choose **Share selected pages**. This uploads server-readable copies, separately from encrypted device sync.
3. Install this plugin and sign in to Char when your agent requests access.

```json
{
  "mcpServers": {
    "char": { "type": "http", "url": "https://char.com/api/mcp" }
  }
}
```

For Claude Code, install the Fastrepl marketplace or load the bundle with `claude --plugin-dir /absolute/path/to/plugins/char`. Codex and Cursor use the host manifests shipped in this bundle.

## Data and tools

`get_status` reports sharing and the last upload time. `search` finds shared pages. `export_page` reads a snapshot as Markdown without changing the source page. These tools cannot edit pages, access local files, or download recordings or attachments.

Selected pages update from the publishing desktop while Char is running. Changes made while it is closed appear after that desktop syncs and uploads again. Use the returned `publishedAt` when freshness matters. Removing a page locally removes its cloud copy on the next successful upload; **Turn off and delete cloud copies** revokes all sharing immediately when the server confirms it.

See the [setup reference](skills/char/references/setup.md) and [MCP reference](skills/char/references/mcp.md). The [local CLI](skills/char/references/cli.md) is a separate optional workflow and is not required for cloud MCP.

## Branding

The bundled square Char icon is used by Codex. Cursor uses the same published icon by URL. All clients use the same shared skill and hosted MCP configuration.
