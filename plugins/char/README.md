# Char for agents

Search and edit local Char pages through the Nightly CLI and MCP. This bundle contains the portable plugin, one shared skill, and manifests for Codex, Claude Code, and Cursor.

See the [repository installation guide](https://github.com/fastrepl/char-agent-plugin#readme), [setup](skills/char/references/setup.md), [CLI commands](skills/char/references/cli.md), and [MCP tools](skills/char/references/mcp.md).

The plugin launches `char-nightly mcp`. It requires Char Nightly `0.0.1-nightly.80` or newer. MCP is local stdio. Page edits apply directly through Char's editor operation pipeline, and export may persist normalized editor state for stable block IDs.
