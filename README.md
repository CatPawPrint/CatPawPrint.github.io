# catpawprint.github.io

Public static endpoint served via GitHub Pages. CatPawPrint apps fetch
small JSON / config files from here at runtime — takedown lists, hot
configuration, parsers, etc. The repo is public; do **not** commit
secrets, API keys, or anything you wouldn't paste in a public gist.

URL pattern: `https://catpawprint.github.io/<app>/<file>`

## Layout

One top-level folder per consumer.

| Folder      | Consumer              | Purpose                                                  |
|-------------|-----------------------|----------------------------------------------------------|
| `parsers/`  | flutter_image_viewer  | git submodule — hot-update parsers (since 2022).         |
| `jigsaw/`   | apps/jigsaw           | Runtime config — currently `takedown.json` for emergency takedown of puzzle entries. |
| `sudoku/`   | (future)              | Reserved.                                                |

## Editing

1. Edit the JSON file locally.
2. Commit with a message that doesn't expose sensitive context (write
   `remove t1_005` rather than `t1_005 reported for copyright`).
3. `git push origin main`.
4. GitHub Pages rebuilds and serves the new content in ~1 minute.
   Verify at `https://catpawprint.github.io/<app>/<file>`.

## Notes

- Files served here are cached by GitHub's CDN; clients should also
  cache locally so an outage (~99.9% uptime, occasional 5-30min
  outages) doesn't break them.
- Schema versions live inside each JSON (e.g. `"version": 1`) so
  clients can fall back when they see a newer schema.
- Commit history is public — be mindful in commit messages.
