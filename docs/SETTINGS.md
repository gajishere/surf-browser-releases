# Surf settings

This page lists every setting in Surf, what it does, its default and the values it accepts.

## Open the Settings page

Type `settings` in the console and press Enter. The page opens in a tab. See [COMMANDS.md](COMMANDS.md) for the other commands and [SHORTCUTS.md](SHORTCUTS.md) for the keyboard shortcuts.

The page looks like the rest of Surf: a console-style screen headed `C:\Settings>`, with each setting on its own row and dotted leaders between the label and the value. It uses the colors and font from your Look settings.

- A toggle shows `[✓]` when it is on and `[x]` when it is off.
- A choice or a number shows the value between `<` and `>`. Click the arrows, or press Left and Right, to change it.
- A text setting (Home page, Download folder) shows its value in square brackets, or `(none)` when it is empty. Press Enter to edit it, Enter again to save, or Esc to cancel.
- The last row, `Reset to defaults`, asks for a Yes or No before it puts every setting back to its default.

Keys on the page: Up and Down move between rows, Left and Right change the value, Enter or Space activates the row, and Esc goes back to the console. A short `Saved` message appears after each change. If you enter a value Surf cannot use, the page shows an `ERR:` message and keeps the old value.

Changes apply as soon as you make them and are saved automatically. Where a setting needs Surf to restart, the page says so under that row, and this document says so too.

## Where settings are stored

Settings are saved to `%LOCALAPPDATA%\SurfBrowser\settings.json`. The page shows the exact path at the bottom.

You can edit the file by hand while Surf is closed. Surf reads it once, when it starts, and does not watch it, so edits made while Surf is running are not picked up and are overwritten the next time Surf saves.

- The file is JSON. Comments and trailing commas are allowed.
- A key that is missing, or whose value is not valid, falls back to its default. Other keys are not affected.
- Choices are not case-sensitive, and a number outside its range is moved to the nearest allowed value.
- If the file is not a JSON object at all, Surf starts with the defaults, shows `Settings could not be read; using defaults.`, and keeps a copy of the file as `settings.json.bak` before it saves anything new.
- Keys Surf does not know are kept when it saves.

## Look

| Label | Key | Default | Values |
|---|---|---|---|
| Text color | `textColor` | `7` (White) | One of the 16 console colors, `0` to `F` |
| Background color | `backgroundColor` | `0` (Black) | One of the 16 console colors, `0` to `F` |
| Font | `font` | Consolas | Consolas, Cascadia Mono, Cascadia Code, Lucida Console, Courier New |
| Font size | `fontSize` | 14 | A whole number from 10 to 24 |
| Cursor | `cursorShape` | Underscore | Underscore, Block, Bar |
| Blinking cursor | `cursorBlink` | On | On or off |
| Console lines | `consoleLines` | 1 | A whole number from 1 to 10 |
| Tab titles | `tabTitles` | Name | Name, Icon only |
| Force dark mode | `forceDark` | Off | On or off |

**Text color** and **Background color** use the same 16 colors as the Command Prompt `color` command, named by a hex digit: `0` Black, `1` Blue, `2` Green, `3` Aqua, `4` Red, `5` Purple, `6` Yellow, `7` White, `8` Gray, `9` Light Blue, `A` Light Green, `B` Light Aqua, `C` Light Red, `D` Light Purple, `E` Light Yellow, `F` Bright White. The two colors must be different. In the file the value is the digit in quotes, for example `"textColor": "7"`.

**Font** is the console font. Only fonts installed on your PC are offered. If the saved font is not installed, Surf uses Consolas.

**Font size** is the console text size in pixels.

**Cursor** is the shape of the console cursor. In the file the values are `underscore`, `block` and `bar`.

**Blinking cursor** turns the cursor blink on or off.

**Console lines** is how many lines tall the console at the bottom of the window is. The window can limit this when it is small.

**Tab titles** chooses whether tabs show the site name or only the site icon. In the file the values are `name` and `icon`.

**Force dark mode** draws web pages in a dark theme using the bundled Dark Reader (see [THIRD-PARTY-NOTICES.md](../THIRD-PARTY-NOTICES.md)). It applies at once and does not need a restart.

## Search and startup

| Label | Key | Default | Values |
|---|---|---|---|
| Search engine | `searchEngine` | Google | Google, DuckDuckGo, Bing, Brave, Ecosia |
| On start | `onStart` | Blank tab | Blank tab, Home page, Last session |
| Home page | `homePage` | empty | A web address, or empty |

**Search engine** is used when you type something that is not a site or a web address, for example `start cats`. In the file the values are `google`, `duckduckgo`, `bing`, `brave` and `ecosia`.

**On start** decides what Surf opens when it starts. In the file the values are `blank`, `home` and `session`.

- Blank tab opens one empty tab.
- Home page opens the address in Home page.
- Last session reopens the tabs you had open when you last closed Surf. Surf saves your open tabs only while this option is selected.

**Home page** is opened when On start is Home page. Enter an address such as `example.com`; Surf stores it as a full `http` or `https` address. Leave it empty for none. It can be up to 2048 characters.

## Tabs and media

| Label | Key | Default | Values |
|---|---|---|---|
| Smart tab grouping | `smartGrouping` | On | On or off |
| Sleep after | `suspendAfterMinutes` | 5 minutes | 1 minute, 5 minutes, 15 minutes, 30 minutes, 1 hour, Never |
| Discard after | `discardAfterMinutes` | 30 minutes | 5 minutes, 15 minutes, 30 minutes, 1 hour, 2 hours, Never |
| Mute background tabs | `muteBackgroundTabs` | Off | On or off |
| Auto picture-in-picture | `autoPip` | Off | On or off |
| Block autoplay | `blockAutoplay` | Off | On or off |

**Smart tab grouping** puts tabs of the same site next to each other under a label.

**Sleep after** puts a tab that has been in the background for that long to sleep to save memory. A tab is not put to sleep while it is playing media or downloading. In the file the values are the number of minutes as text (`"1"`, `"5"`, `"15"`, `"30"`, `"60"`), and `"0"` means Never.

**Discard after** frees the memory of a background tab completely after that long. The tab reloads when you select it. A tab is never discarded sooner than Sleep after. In the file the values are the number of minutes as text (`"5"`, `"15"`, `"30"`, `"60"`, `"120"`), and `"0"` means Never.

**Mute background tabs** silences every tab you are not looking at.

**Auto picture-in-picture** moves the video of a tab you leave into a small picture-in-picture window, and takes it back when you return.

**Block autoplay** stops pages from playing media until you interact with them. This takes effect when Surf restarts.

## Privacy and downloads

These settings are explained further in [PRIVACY.md](PRIVACY.md).

| Label | Key | Default | Values |
|---|---|---|---|
| Block ads | `blockAds` | On | On or off |
| Block third-party cookies | `blockThirdPartyCookies` | Off | On or off |
| Tracking prevention | `trackingPrevention` | Balanced | Off, Basic, Balanced, Strict |
| Clear data on exit | `clearDataOnExit` | Off | On or off |
| Pop-ups | `popups` | Block | Block, Allow |
| Download folder | `downloadFolder` | empty (your Downloads folder) | A full folder path such as `D:\Downloads`, or empty |

**Block ads** blocks ads with the bundled uBlock Origin Lite (see [THIRD-PARTY-NOTICES.md](../THIRD-PARTY-NOTICES.md)). It can be switched on and off without restarting. While it is on, Surf also checks for a newer uBlock Origin Lite about once a day; see [PRIVACY.md](PRIVACY.md).

**Block third-party cookies** blocks cookies set by sites other than the one you are visiting. This takes effect when Surf restarts.

**Tracking prevention** sets the level of the browser engine's built-in tracking prevention. In the file the values are `off`, `basic`, `balanced` and `strict`.

**Clear data on exit** deletes your cookies, history, cache, site data and saved passwords when Surf closes. See [PRIVACY.md](PRIVACY.md) for exactly what it clears and what it keeps.

**Pop-ups** decides whether pages can open new windows or tabs on their own. With Block, a new tab opens only when you cause it, for example by clicking a link. With Allow, a page may also open one by script. In the file the values are `block` and `allow`.

**Download folder** is where downloads are saved. Leave it empty to use your Downloads folder. Enter a full path that starts with a drive letter, such as `D:\Downloads`; network (UNC) paths and relative paths are not accepted. If Surf cannot use the folder, it prints a notice in the console and saves to Downloads instead.

## Reset

The `Reset to defaults` row at the bottom of the page puts every setting back to its default after you confirm.

## See also

- [COMMANDS.md](COMMANDS.md)
- [SHORTCUTS.md](SHORTCUTS.md)
- [PRIVACY.md](PRIVACY.md)
- [README](../README.md)
