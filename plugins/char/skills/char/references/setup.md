# Setup and troubleshooting

Install Char Nightly and enable its CLI in settings. Check `char-nightly --version`, `char-nightly db status`, and `char-nightly mcp --help`.

The MCP command requires Char Nightly `0.0.1-nightly.80` or newer. Reinstalling the CLI shim alone cannot add commands absent from the app bundle.

The plugin uses `char-nightly` on PATH. If a desktop agent cannot find it, configure the absolute CLI path returned by `command -v char-nightly`. A terminal and a desktop app may have different PATH values.

- Unknown `mcp` command: update Char Nightly. The skill can still use existing CLI search/export/edit commands.
- Wrong channel: verify `get_status` or `db status`. Do not switch channels without the user's intent.
- Unhealthy bridge: open or restart the matching Char app and retry. The CLI refuses direct fallback while an existing bridge descriptor is unhealthy.
- Missing page: search again or confirm the daily date. Do not create data merely to satisfy a read.
- Failed edit: export again before retrying; a timed-out operation may still complete.

See the [installation guide](https://github.com/fastrepl/char-agent-plugin#readme) for client configuration.
