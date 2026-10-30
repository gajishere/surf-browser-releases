# Changelog

All notable changes to Surf Browser are listed here. The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and Surf uses [semantic versioning](https://semver.org/).

## [1.0.0] - 2026-10-30

The first public release.

### Browsing from the console

- A Command Prompt style console under every page, with a `C:\Web>` prompt that shows the current site.
- Type a site name (`youtube`), an address (`example.com`, `localhost:3000`) or anything else to search. A leading `?` always searches, and typos of popular sites get a "Did you mean" hint.
- Commands: `start`, `cd`, `back`, `forward`, `reload`, `copy`, `type`, `mode`, `pip`, `ping`, `bookmark`, `tree`, `rd`, `batch`, `echo`, `rem`, `cls`, `size`, `mini`, `color`, `settings`, `help`, `ver` and `exit`, each with `/?` usage.
- Slash commands (`/help`), chaining with ` & `, Tab completion, and Up/Down history of the last 50 commands.
- Scripts: `batch add` saves `.bat` scripts of commands that you run by typing their name.

### Tabs

- Windows Terminal style tabs in the title bar, with site names or icons only.
- Smart grouping of tabs from the same site under a collapsible label.
- Background tabs sleep after 5 minutes and are discarded after 30 by default, unless they play media or download.
- Workspaces: `cd \name` switches between named sets of tabs.
- Reopen closed tabs with Ctrl+Shift+T, and optionally restore the last session on start (Settings, On start).

### Pages

- Built-in ad blocking with uBlock Origin Lite, on by default, with daily update checks verified by SHA-256.
- Force dark mode with the bundled Dark Reader.
- Text mode (`mode text`) that shows a page as monospace text in your console colors.
- Picture-in-picture (`pip`) and automatic picture-in-picture when you leave a tab.
- Downloads with progress in the console, and a choice of download folder.

### Settings and privacy

- A DOS-style Settings page (`settings`): colors, font, cursor, console height, tab titles, search engine, start-up, tab sleep, media, ads, cookies, tracking prevention, pop-ups and downloads.
- Third-party cookie blocking, tracking prevention levels, pop-up blocking, and Clear data on exit.
- No telemetry. Settings, history, bookmarks and browser data stay in `%LOCALAPPDATA%\SurfBrowser`.

### Performance

- The web engine starts while the window is being built, so the first page appears sooner.
- Surf's own process uses about 38 MB, and the console keeps at most about 9,000 lines.

[1.0.0]: https://github.com/gajishere/surf-browser-releases/releases/tag/v1.0.0
