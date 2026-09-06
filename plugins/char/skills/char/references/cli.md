# CLI

The installed CLI travels with the desktop app. Check `char-nightly --help` for the available command surface.

```sh
char-nightly --version
char-nightly db status
char-nightly search 'launch' --limit 10
char-nightly pages export --page-id '<page-id>'
char-nightly pages export --daily today
```

Search prints JSON; export prints markdown with `char:block` IDs. The daily selector accepts `today` or `YYYY-MM-DD`. Pass exactly one selector.

For requested edits, export the page and copy a returned block ID:

```sh
char-nightly pages edit --page-id '<page-id>' --replace-block '<block-id>' --markdown 'Updated text'
char-nightly pages edit --page-id '<page-id>' --insert-after-block '<block-id>' --markdown 'New paragraph'
char-nightly pages edit --page-id '<page-id>' --delete-block '<block-id>'
char-nightly pages export --page-id '<page-id>'
```

Use `--markdown-file <path>` for multiline content or `--markdown-file -` for stdin. Keep edits to the same page sequential. Writes use Char's editor operation pipeline and apply directly.

For diagnostics, use `db schema`, `db examples`, and `debug agent --help`. Prefer purpose-built commands. If a read needs SQL, use one statement through `db sql` with bound values in `--param '<json-array>'`. Never write page content directly with SQL.
