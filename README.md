# Char for agents

Official Char plugin for Codex, Claude Code, Cursor, and compatible agents. Search local Char pages, tasks, people, and organizations, export page content, and apply requested page edits.

## Requirements

Install [Char Nightly 0.0.1-nightly.80](https://char.com/api/v1/ota/desktop/nightly/char-nightly-0.0.1-nightly.80-mac-arm64.dmg) or newer and enable its CLI in settings. The CLI must include the MCP command:

```sh
char-nightly --version
char-nightly mcp --help
```

Nightly `0.0.1-nightly.80` is the first release with MCP. The plugin uses your local Nightly data.

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

This repository includes a Cursor marketplace manifest and a portable agent plugin at [`plugins/char`](plugins/char). For direct MCP configuration:

```json
{
  "mcpServers": {
    "char": {
      "command": "char-nightly",
      "args": ["mcp"]
    }
  }
}
```

If the client cannot find `char-nightly`, replace `command` with the absolute CLI path returned by `command -v char-nightly`. Desktop apps may have a different PATH from your terminal.

The shared skill can also be installed independently from [`plugins/char/skills/char`](plugins/char/skills/char).

## Tools

- `get_status` confirms the local channel and desktop bridge status.
- `search` finds pages, tasks, people, and organizations.
- `export_page` returns markdown with stable block IDs. It may persist normalized editor state.
- `edit_page` applies a requested block edit directly in Char. Export first and verify after editing.

See [CLI commands](plugins/char/skills/char/references/cli.md), [MCP inputs](plugins/char/skills/char/references/mcp.md), and [setup](plugins/char/skills/char/references/setup.md).

This is a local stdio integration. It does not provide a hosted MCP endpoint. The plugin contains no credentials; it uses the installed Char CLI.
