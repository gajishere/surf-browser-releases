# Changelog

All notable changes to Surf Browser are listed here. The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and Surf uses [semantic versioning](https://semver.org/).

## [1.2.0] - 2026-10-31

### Added

- Suggestions as you type. Matching commands, sites, tabs, bookmarks and shortcuts appear above the prompt, each with a short note on what it does, and the rest of the selected match shows dimmed after the cursor. Tab takes the selected match and then moves to the next one; Up and Down move through the list and Esc hides it. After a command and a space, a dim hint shows what it expects. It can be turned off with Command suggestions in Settings, and Tab completes either way.
- `split site` shows a second page beside the current one. Click a page to make it the current one, drag the bar between them to resize, and `split off` goes back to one page.
- `f` labels every link, button and field in view. Type a label to follow it, or type it in capitals to open the link in a new tab.
- `find "text"` marks every match on the page and lists them in the console; `find n` jumps to match n and `find` alone clears the marks.
- `start /private` opens a private tab. Nothing from it goes into your history, and its sign-ins and cookies are deleted when the last private tab closes. The ad blocker works there too.
- `snip` saves a picture of the visible page to your download folder, and `snip /full` saves the whole page.
- `tasklist` shows every tab with its process, state and memory use, plus the engine's own processes and a total. `taskkill n` closes tab n and `taskkill /im site` closes every tab showing that site.
- `doskey name=command` makes your own shortcuts, with `$1` to `$9`, `$*` and `$T` as in Windows. `doskey` lists them and `doskey name=` deletes one.
- Efficiency mode (Settings, Tabs and media; on battery by default). Background tabs sleep after 1 minute and free their memory after 10, unless your own times are shorter or Never.

### Changed

- Up and Down move through the suggestion list while it is open, and through the commands you typed otherwise.

## [1.1.1] - 2026-10-31

### Added

- An installer, `Surf-1.1.1-win-x64-setup.exe`, now the recommended download. It installs Surf just for you (no admin rights) in `%LOCALAPPDATA%\Programs\Surf`, adds a Start menu shortcut and an optional desktop shortcut, and keeps Surf updating itself. Its uninstaller asks before deleting your settings, bookmarks and history. The portable zip and small exe are still there.

### Changed

- The app icon has rounded corners and a soft blue glow, so it sits better on the taskbar.

## [1.1.0] - 2026-10-31

### Faster

- Keep Surf ready in the background (Settings, Search and startup; off by default). Surf stays running hidden after you close it and starts when you sign in, so it opens in about 0.2 s. It uses about 108 MB while hidden.
- A cold start loads the first page in about 0.65 s, down from about 0.78 s in 1.0.0.

### Added

- Surf updates itself. Update Surf automatically (on by default) checks once a day and gets the new version ready for the next start; `ver /update` checks right away. Every download is checked against the SHA-256 that GitHub publishes.

### Changed

- Dark site icons, such as GitHub's, are shown white on the tab strip.

### Fixed

- Ad blocking on pages (YouTube, cosmetic filters) is set up again if Surf was closed during uBlock Origin Lite's first run.

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

[1.1.1]: https://github.com/gajishere/surf-browser-releases/releases/tag/v1.1.1
[1.1.0]: https://github.com/gajishere/surf-browser-releases/releases/tag/v1.1.0
[1.0.0]: https://github.com/gajishere/surf-browser-releases/releases/tag/v1.0.0
