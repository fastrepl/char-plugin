# Setup and troubleshooting

1. Use a Char desktop release with **Settings → Account → Cloud access for agents**.
2. Sign in, select up to 50 pages, and choose **Share selected pages** after reading the disclosure. Each selected page must contain at most 65,536 characters of Markdown.
3. Install this plugin in Codex, Claude Code, or Cursor. On connection, sign in to Char and grant read access.
4. Run `get_status`, then `search` with an empty query to confirm uploaded pages are available.

The plugin requires no installed CLI, API key, or running desktop to read existing snapshots. The publishing desktop must run to upload new changes. It uploads periodically while signed in; another device can take over by saving its selection.

If a page is missing, select it in Char and check the last upload time. If sign-in fails, reconnect the Char MCP account. Never request the user's session cookies, OAuth tokens, or recovery key in chat.

To revoke all access, choose **Turn off and delete cloud copies** in Char and wait for confirmation. Disconnecting one OAuth client stops that client's access but does not remove copies still shared with other authorized clients. Signing out of the desktop stops uploads; it does not revoke existing cloud sharing.

For an explicitly requested local workflow, Char Nightly 0.0.1-nightly.80 or newer includes `char-nightly mcp` and the commands in the [CLI reference](cli.md). This is a separate local stdio server and does not share the hosted server's tool contract.
