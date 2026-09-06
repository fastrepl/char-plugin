# Cloud MCP

Endpoint: `https://char.com/api/mcp`. Transport: Streamable HTTP. Authentication: Char OAuth; required scope `char:content:read`.

| Tool          | Input                                | Result                                                         |
| ------------- | ------------------------------------ | -------------------------------------------------------------- |
| `get_status`  | `{}`                                 | Cloud sharing status, selected-page count, and `publishedAt`   |
| `search`      | `{ "query": "launch", "limit": 20 }` | Shared page IDs, titles, kind, source update time, upload time |
| `export_page` | `{ "pageId": "returned-id" }`        | Page Markdown and timestamps, or `page_unavailable`            |

Search accepts an empty query to list pages and limits results to 1–50. Exporting does not normalize editor state or create block IDs. All three tools are read-only, idempotent, non-destructive, and limited to the signed-in account's shared pages. There is no cloud `edit_page` tool.

An unavailable page may be unshared, deleted, or absent from the last upload. Do not infer which unless the user confirms it. `publishedAt` is the cloud upload time; `updatedAt` is the source page's update time.
