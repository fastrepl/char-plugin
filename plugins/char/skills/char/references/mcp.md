# MCP

Launch with `char-nightly mcp`. This is a local stdio server, with JSON-RPC on stdout and diagnostics on stderr. It uses the same desktop bridge and native fallback as the CLI. It has no hosted endpoint or cloud OAuth flow.

- `get_status` takes `{}` and reports channel, database path, and bridge availability. Read-only.
- `search` takes `{ "query": "launch", "limit": 10 }`. Limit defaults to 20 and accepts 1–50. Returns the CLI's search hits (`kind`, `id`, `title`, `snippet`, `rank`) as JSON text. Only `kind: "page"` IDs can be used with `export_page`. Read-only.
- `export_page` takes `{ "pageId": "<returned-page-id>" }` or `{ "daily": "today" }`. Returns `{ "pageId": "...", "markdown": "..." }` as JSON text. May persist normalized editor state to stabilize block IDs, so it is not marked read-only.
- `edit_page` takes a page selector plus `edit`, and applies it directly. Export first and verify afterward.

```json
{
  "pageId": "<returned-page-id>",
  "edit": {
    "type": "replace",
    "blockId": "<returned-block-id>",
    "markdown": "Updated text"
  }
}
```

Other edits are `insert-after` with `blockId` and `markdown`, or `delete` with only `blockId`. Pass exactly one of `pageId` and `daily`. The server does not expose arbitrary SQL, shell commands, or agent lifecycle hooks as MCP tools.
