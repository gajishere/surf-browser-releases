# Surf privacy

This page explains what Surf keeps on your PC, what Surf itself sends over the network, and how to remove everything.

In short: Surf has no analytics or telemetry, it keeps your data in one folder on your PC, and the only network request it makes by itself is a once-a-day check for an ad-blocker update.

## What Surf stores on your PC

Everything is stored under `%LOCALAPPDATA%\SurfBrowser`. Nothing is stored next to `SurfBrowser.exe`.

| File or folder | What it holds | How long it is kept | Removed by "Clear data on exit"? |
|---|---|---|---|
| `history.json` | The address, title and time of pages you visited (web addresses only) | Up to 90 days and 5000 pages; older entries are dropped | Yes. Deleted when Surf closes, and not written while the setting is on |
| `sites.json` | The sites you visited, with a visit count and last-visit time, used to complete site names | The 500 most recently visited sites | Yes. Deleted when Surf closes, and not written while the setting is on |
| `commands.json` | The last commands you typed in the console, so the Up arrow can recall them | The last 50 commands | Yes. Deleted when Surf closes, and not written while the setting is on |
| `session.json` | The addresses of your open tabs, so "Last session" can restore them | Up to 100 tabs; replaced each time your tabs change. Written only while On start is Last session, and left in place if you change that option later | No |
| `bookmarks.json` | Your bookmarks | Until you remove them; up to 500 | No |
| `workspaces.json` | Your named workspaces and their tabs | Until you remove them; up to 20 | No |
| `scripts\*.bat` | Console scripts you create | Until you delete them | No |
| `settings.json` | Your settings. See [SETTINGS.md](SETTINGS.md) | Until you delete it | No |
| `Extensions\uBOLite` | The unpacked uBlock Origin Lite ad blocker, and a small `state.json` that remembers the installed version and the time of the last update check | Old versions are cleaned up after an update | No |
| `WebView2` | The browser profile (see below) | Managed by the browser engine | Yes, the browsing data inside it (see below) |

Surf may also leave short-lived helper files while it writes: `.tmp` copies of the files above, and `.bak` copies (`settings.json.bak`, `bookmarks.json.bak`) made when it finds a file it cannot read. The ad blocker briefly writes its bundled package to your temp folder as `surf-ubol-*.zip` while unpacking it, and deletes it afterwards. While it updates, it also uses an `update.lock` file, a `download-*.zip.part` file and temporary unpack folders inside `Extensions\uBOLite`, and removes them when it is done.

### The browser profile

Surf shows web pages with the Microsoft Edge WebView2 engine. The engine keeps its own data for the pages you visit in `%LOCALAPPDATA%\SurfBrowser\WebView2`: cookies, cache, site data, saved passwords and the like. The same folder holds a small `surf-engine.json` file that Surf uses to match its engine start-up options.

### Clear data on exit

When this setting is on, Surf deletes all browsing data in the profile (cookies, history, cache, site data and saved passwords) when it closes, and deletes `history.json`, `sites.json` and `commands.json`. It tries for up to about five seconds before it gives up and lets Surf close.

It does not remove your bookmarks, workspaces, scripts, settings, `session.json`, the ad blocker files, or files you downloaded.

## What Surf sends over the network

### Requests made by Surf itself

Surf's own code makes these requests and no others:

1. **Ad-blocker update check.** While **Block ads** is on, Surf asks GitHub whether a newer uBlock Origin Lite exists.
   - Where: `https://api.github.com/repos/uBlockOrigin/uBOL-home/releases/latest`.
   - When: about 30 seconds after Surf starts and then at most once every 24 hours. The time of the last check is saved in `Extensions\uBOLite\state.json`. If a check fails, Surf does not retry until the next day.
   - What is sent: an ordinary HTTPS GET request with the headers `User-Agent: SurfBrowser/1.0` and an `Accept` header. It carries no cookies and no data from your browsing. GitHub sees your IP address, as any website does.
   - If a newer version exists, Surf downloads it from `https://github.com/uBlockOrigin/uBOL-home/releases/download/` (GitHub redirects the download to its file hosts). Surf installs it only if the file matches the SHA-256 checksum that GitHub published for it.
   - When **Block ads** is off, Surf makes no request at all.
2. **`ping` command.** Only when you type `ping`, Surf looks up the name you gave with your system's DNS and sends four ICMP echo requests to that address, like the Windows `ping` command.

That is the complete list. Surf does not fetch search suggestions, site icons or news from any server of its own. When you type a search, Surf opens your chosen search engine's results page like any other page (see below). Site icons shown on tabs are the ones the page itself provides.

### Requests made by the pages you visit

When you open a page, the page loads and its sites receive requests just as in any other browser: your IP address, cookies, and whatever the page asks for. If you type a search, the text goes to the search engine you picked in Settings. The ad blocker, tracking prevention and cookie settings below reduce this but cannot remove it.

### The WebView2 runtime

The Microsoft Edge WebView2 runtime is a Microsoft component that is installed on your PC separately from Surf. It may send diagnostic or other data to Microsoft under Microsoft's own terms, which Surf does not control. Surf does not turn this on or off. See Microsoft's documentation for the WebView2 runtime for details.

## Privacy settings

All of these are in the Settings page; see [SETTINGS.md](SETTINGS.md) for how to change them and their values.

- **Block ads** (on by default): blocks ads with the bundled uBlock Origin Lite. See [THIRD-PARTY-NOTICES.md](../THIRD-PARTY-NOTICES.md).
- **Block third-party cookies** (off by default): blocks cookies from sites other than the one you are visiting. Takes effect after a restart.
- **Tracking prevention** (Balanced by default): sets the level of the browser engine's tracking prevention to Off, Basic, Balanced or Strict.
- **Clear data on exit** (off by default): see above.
- **Pop-ups** (Block by default): stops pages from opening new windows or tabs unless you caused it.
- **Download folder**: where downloads are saved. Empty means your Downloads folder.

## Telemetry

Surf has no analytics, usage tracking, crash reporting or telemetry. Its code contains none, and it does not phone home. The only network access by Surf's own code is the list above.

## Remove everything

1. Close Surf.
2. Delete the folder you unzipped Surf into, or the small `.exe` if you use that download.
3. Delete the folder `%LOCALAPPDATA%\SurfBrowser`. Paste that path into the File Explorer address bar to open it.

Surf does not write to the Windows registry, and it does not store data anywhere else. Files you downloaded stay in your download folder until you delete them. If you set the `WEBVIEW2_USER_DATA_FOLDER` environment variable, the browser engine keeps its profile in that folder instead of `WebView2`, so delete that folder too.

## See also

- [SETTINGS.md](SETTINGS.md)
- [COMMANDS.md](COMMANDS.md)
- [README](../README.md)
