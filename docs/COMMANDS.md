# Surf commands

Everything in Surf is driven from the console at the bottom of the window, so this page lists every command it understands. For keys and mouse actions, see [SHORTCUTS.md](SHORTCUTS.md). For the options on the Settings page, see [SETTINGS.md](SETTINGS.md).

- [How input works](#how-input-works)
- [Browsing](#browsing)
- [Pages](#pages)
- [Bookmarks and history](#bookmarks-and-history)
- [Workspaces and scripts](#workspaces-and-scripts)
- [Console and look](#console-and-look)
- [Help and information](#help-and-information)
- [Easter eggs](#easter-eggs)
- [Quick reference](#quick-reference)

## How input works

The prompt shows where you are. With no page open it reads `C:\Web>`. On a page it adds the site, for example `C:\Web\youtube.com>`. In a named workspace the first part is the workspace name instead of `Web`, and on the Settings page it reads `C:\Settings>`. The examples below show the prompt as you would see it.

### Commands and anything else

- **Commands are not case-sensitive.** `START`, `Start` and `start` all work.
- **Anything that is not a command opens as an address or a search.** You do not need `start` for that. Type `youtube`, `example.com` or `best pizza near me` and Surf opens it in a new tab.
- **The rules, in order:**
  1. If the first word is a command, the command runs.
  2. If the whole line is the name of one of your [scripts](#batch), the script runs.
  3. Otherwise Surf treats the line as `start` followed by what you typed (see [start](#start)).
- **A leading `?` always searches.** `?youtube` searches for the word instead of opening the site. The `?` can sit right against the text or be followed by a space.
- **Add `/?` to any command** to print its usage, for example `cd /?`. `help command` shows the same text.

### Slash commands

Every command also works with a leading slash, so `/help` is the same as `help`. A slash is a firm signal that you mean a command: if the word is not a command, Surf prints an error and never searches. Type the name directly after the slash, as in `/cls`.

### Chaining commands with &

Put `&` between commands, with a space on each side, to run them one after another:

```text
C:\Web> start youtube & start github
C:\Web> cls & ver
```

- Only a single `&` with spaces around it chains commands. `&&` is not a chain operator.
- Every part must start with a command. If any part does not (an address, a search or a script name), the whole line is treated as one ordinary input instead.
- A line can chain up to 20 commands. A single line, together with any scripts it runs, stops after 100 commands.
- `batch` keeps the rest of its line as typed, so `batch add name start a & start b` saves both commands in the script. See [batch](#batch).

### Tab completion and history

- Press **Tab** to complete the word you are typing, and press it again for the next match. **Shift+Tab** goes back to the previous match. Completion works at the end of the line.
- The first word completes to commands, your scripts, your bookmarks, and site names (open tabs first, then popular and visited sites). Start the word with `/` to complete slash commands.
- After a command, Tab completes what that command takes: sites after `start`, `cd` and `tree`; `add`, `del` and `list` after `bookmark`; `add`, `del`, `list` and `show` after `batch`; bookmark names after `bookmark del`; script names after `batch del` and `batch show`; command names and `keys` after `help`; `title` after `copy`; `normal` and `text` after `mode`; workspace names after `cd \` and `rd \`.
- Press **Up** and **Down** to move through the commands you typed before. Surf keeps the last 50, skips a command that repeats the one before it, and remembers them between sessions unless Surf is set to clear its data on exit.
- **Esc** clears the line. On an empty line it closes a console that grew to show a long answer.

## Browsing

### start

Opens a site, an address or a search in a new tab. A blank new tab is reused instead of opening another.

```text
start site
start address
start search text
start ?search text
```

| Argument | What it does |
| --- | --- |
| `site` | The name of a bookmark, a popular site or a site you have visited, such as `youtube`. |
| `address` | A web address such as `youtube.com`, `localhost:3000` or `https://example.com`. |
| `search text` | Anything else is searched with your search engine (set in Settings). |
| `?text` | Searches the text after the `?`, even if it looks like a site name or an address. |

How a word is understood, in order:

1. A leading `?` searches.
2. A bare domain that looks like a typo of a popular site stops with a hint and a suggestion, for example `Did you mean youtube.com?`. Type the full `https://` address to open it anyway.
3. A real address opens. Addresses are `http://`, `https://` or `file://` addresses, domains with a dot, `localhost`, and IPv4 addresses, each with an optional port. `localhost` and IP addresses open over `http://`, domains over `https://`.
4. One word that is a bookmark name opens that bookmark. A bookmark wins over a site of the same name.
5. One word that is a popular site, or a site you have visited, opens that site.
6. Everything else, including any text with a space in it, is a search.

```text
C:\Web> start youtube
C:\Web> start localhost:3000
C:\Web> start ?youtube
```

Typing nothing after `start` prints `The syntax of the command is incorrect.`

### cd

Shows the current address, loads a new one in the current tab, or switches workspace.

```text
cd [address]
cd ..
cd \name
```

| Form | What it does |
| --- | --- |
| `cd` | Prints the address of the current page (`C:\Settings` on the Settings page, or the workspace folder when there is no page). |
| `cd address` | Loads a web address, bookmark or site name in the current tab. It follows the same rules as [start](#start), but a lone word that is not a bookmark or a known site prints `The system cannot find the path specified.` instead of searching. |
| `cd ..` | Goes back one page, like [back](#back). |
| `cd \name` | Switches to the workspace `name`, creating it if it does not exist. `cd \` opens the default workspace, `Web`. |

`cd..` and `cd\name` work without a space.

```text
C:\Web> cd
C:\Web> cd github
C:\Web\github.com> cd ..
C:\Web> cd \work
```

See [Workspaces and scripts](#workspaces-and-scripts) for more on workspaces.

### back

Goes back one page. `cd ..` does the same.

```text
C:\Web\example.com> back
```

Prints `There is no page open.` when the tab has nothing to go back from. Any extra text prints a syntax error.

### forward

Goes forward one page.

```text
C:\Web\example.com> forward
```

### reload

Reloads the current page.

```text
C:\Web\example.com> reload
```

## Pages

### copy

Copies the current page's address, or its title, to the Windows clipboard.

```text
copy [title]
```

```text
C:\Web\github.com> copy
C:\Web\github.com> copy title
```

Surf prints what it copied, cut to 100 characters for display. Surf's own pages (such as Settings) cannot be copied.

### type

Prints the page's text in the console, the way the Windows `type` command prints a file.

```text
type
```

```text
C:\Web\example.com> type
```

It prints at most the first 200 lines or 20,000 characters of the page, followed by a line such as `... (35 more lines)` when it stops early. It takes no arguments. It prints `This page has no text.` for a page without text, and it does not work on Surf's own pages.

### mode

Shows the current page as plain monospace text in your console colors, with no pictures or videos, or puts the page back as the site made it.

```text
mode [text | normal]
```

```text
C:\Web\example.com> mode text
Mode is text.
C:\Web\example.com> mode normal
Mode is normal.
```

`mode` alone prints the current mode. Only web pages (`http` and `https`) can be shown as text.

### pip

Shows the video on the page in a small window on top of other windows. Type it again to bring the video back.

```text
pip
```

```text
C:\Web\youtube.com> pip
```

Surf uses the video that is playing, or the largest one otherwise. It prints a message if there is no video on the page, if the video does not allow picture-in-picture, or if the video is not ready yet.

### ping

Checks whether a site is reachable and how fast it answers.

```text
ping site
```

`site` can be a site name such as `youtube`, a bookmark, a web address or a host name.

```text
C:\Web> ping youtube
C:\Web> ping example.com
```

It sends 4 requests, one a second, and prints the replies and a summary in the style of the Windows `ping`. Some sites do not answer ping even when they are up. `ping` with no site prints its usage.

## Bookmarks and history

### bookmark

Saves pages by name and opens them by typing the name.

```text
bookmark add [name]
bookmark list
bookmark del name
```

| Option | What it does |
| --- | --- |
| `add [name]` | Saves the current page as `name`. Without a name, Surf uses the site's name (`github` for github.com). An existing name is replaced. |
| `list` | Shows your bookmarks, sorted by name. |
| `del name` | Removes a bookmark. |

A name is one word of letters, digits and hyphens, up to 63 characters. A command name or an address (anything with a dot) cannot be a bookmark name. Only `http` and `https` pages can be bookmarked, and you can keep up to 500 bookmarks.

Type the name alone to open a bookmark. `start name` opens it in a new tab and `cd name` in the current tab. A bookmark wins over a site of the same name, and `?name` always searches. `bookmark` alone prints its usage.

```text
C:\Web\github.com> bookmark add code
Bookmark code saved.
C:\Web\github.com> bookmark list
C:\Web\github.com> bookmark del code
```

### tree

Shows the sites and pages you visited as a tree, like the Windows `tree` command.

```text
tree [site] [/d]
tree \
```

| Option | What it does |
| --- | --- |
| `site` | A site name such as `youtube`, or a web address, to show only that site. |
| `/d` | Shows every kept day instead of just today. The switch can go before or after the site. |
| `\` | Lists your workspaces instead, with the number of tabs in each. |

History keeps 90 days.

```text
C:\Web> tree
C:\Web> tree youtube /d
C:\Web> tree \
```

## Workspaces and scripts

A workspace is a named set of tabs. The default one is `Web`. Each workspace is like a folder: the prompt shows its name, and switching workspaces swaps the tabs you see.

### rd

Removes a workspace.

```text
rd [/s] [/q] \name
```

| Option | What it does |
| --- | --- |
| `name` | The workspace to remove. The default, `Web`, cannot be removed. |
| `/s` | Removes the workspace even when it still has tabs. |
| `/q` | Quiet mode, accepted for compatibility. It changes nothing. |

The workspace you are in cannot be removed. Switch away first with `cd \`. You can have up to 20 named workspaces.

```text
C:\work> cd \
C:\Web> rd /s \work
Workspace work removed.
```

### batch

Saves and runs scripts of console commands. A script is a list of commands, one per line.

```text
batch add name command
batch list
batch show name
batch del name
```

| Option | What it does |
| --- | --- |
| `add name command` | Adds a line to the script `name`, creating the script. Everything after the name is saved as typed. |
| `list` | Shows your scripts and how many lines each has. |
| `show name` | Prints the lines of a script. |
| `del name` | Deletes a script. |

To run a script, type its name. Typing `name.bat` also works.

```text
C:\Web> batch add morning start github
Script morning.bat created with 1 line.
C:\Web> batch add morning start youtube & start news.ycombinator.com
C:\Web> morning
```

Things to know:

- A script name follows the same rules as a bookmark name. It also cannot be a command name or an address.
- A script can run other scripts, up to 5 levels deep. A script that calls itself is stopped.
- Blank lines, `rem` lines and `::` lines are skipped, and so are `echo on` and `echo off`.
- A script can have up to 100 lines of up to 1024 characters each, and you can keep up to 100 scripts. A script file can be up to 64 KB.
- `exit` inside a script ends the script. It does not close Surf.
- Scripts are plain `.bat` text files. `batch` with no arguments prints the folder they are kept in.

### echo

Prints a line of text. It is mostly useful in scripts.

```text
echo [text]
```

```text
C:\Web> echo Good morning
Good morning
```

`echo` alone prints a blank line. `echo on` and `echo off` are accepted for old scripts and print nothing.

### rem

A comment. It does nothing, which makes it useful for notes in scripts.

```text
rem [comment]
```

```text
C:\Web> batch add morning rem open my usual sites
```

## Console and look

### cls

Clears the console.

```text
cls
```

### size

Sets the console height as a percentage of the window.

```text
size [percent]
```

`percent` is from 1 to 100, with or without a `%` sign. The console snaps to whole lines, and the page always keeps at least a few lines. `size` alone shows the current size.

```text
C:\Web> size 40
Console size is 40%.
```

Alt+Shift+Up and Alt+Shift+Down change the size a line at a time, and you can drag the divider above the console. See [SHORTCUTS.md](SHORTCUTS.md).

### mini

Collapses the console to its prompt line so the page gets nearly all of the window. Type `mini` again to restore it.

```text
mini
```

Because a collapsed console has no room for a visible reply, Surf announces the change to screen readers only.

### color

Sets the console text and background colors, like the Windows `color` command.

```text
color [attr]
```

`attr` is two hex digits, the background first and then the text. One digit sets only the text color. `color` alone restores the default, `07`. The two colors must differ: `color 00` prints `The text and background colors must be different.`

| Digit | Color | Digit | Color |
| --- | --- | --- | --- |
| `0` | Black | `8` | Gray |
| `1` | Blue | `9` | Light Blue |
| `2` | Green | `A` | Light Green |
| `3` | Aqua | `B` | Light Aqua |
| `4` | Red | `C` | Light Red |
| `5` | Purple | `D` | Light Purple |
| `6` | Yellow | `E` | Light Yellow |
| `7` | White | `F` | Bright White |

```text
C:\Web> color 0A
C:\Web> color 1F
C:\Web> color
```

The change applies at once and is saved. See [easter eggs](#easter-eggs) for a small surprise.

### settings

Opens the Settings page in a tab. Colors, font, cursor, search engine and start-up options are set there. Changes apply at once and are saved.

```text
settings
```

See [SETTINGS.md](SETTINGS.md) for every option.

## Help and information

### help

Lists the commands, or shows the usage of one.

```text
help [command]
help keys
```

```text
C:\Web> help
C:\Web> help bookmark
C:\Web> help keys
```

`help` alone lists the commands with a one-line summary each. `help keys` lists the main keyboard shortcuts; the full list is in [SHORTCUTS.md](SHORTCUTS.md).

### ver

Shows the Surf version.

```text
ver
```

```text
C:\Web> ver
C:\Surf [Version 1.0.0]
```

### exit

Quits Surf.

```text
exit
```

In a script, `exit` only ends the script.

## Easter eggs

These commands are real, but they are left out of the `help` list. `help matrix` and `help coffee` still show their usage.

### matrix

Digital rain over the page. Press any key to stop it.

```text
C:\Web> matrix
```

### coffee

Asks the browser for a coffee. It has an opinion about that.

```text
C:\Web> coffee
```

### The color tribute

The first time in a session that you set green text on a black background with `color 0A`, Surf says a short line about old terminals. It shows once per session.

```text
C:\Web> color 0A
```

## Quick reference

| Command | What it does |
| --- | --- |
| `start` | Opens a site, address or search in a new tab. |
| `cd` | Shows the address, loads one in this tab, goes back with `..`, or switches workspace with `\name`. |
| `back` | Goes back one page. |
| `forward` | Goes forward one page. |
| `reload` | Reloads the page. |
| `copy` | Copies the page address, or its title with `copy title`. |
| `type` | Prints the page's text in the console. |
| `mode` | Shows the page as plain text (`mode text`) or normal (`mode normal`). |
| `pip` | Shows the page's video in a small window on top. |
| `ping` | Checks whether a site is reachable. |
| `bookmark` | Saves (`add`), lists (`list`) and removes (`del`) named bookmarks. |
| `tree` | Shows your history as a tree, or your workspaces with `tree \`. |
| `rd` | Removes a workspace. |
| `batch` | Creates, lists, shows and deletes scripts; type a script's name to run it. |
| `echo` | Prints a line of text. |
| `rem` | A comment that does nothing. |
| `cls` | Clears the console. |
| `size` | Sets the console height as a percentage. |
| `mini` | Collapses or restores the console. |
| `color` | Sets the console colors. |
| `settings` | Opens the Settings page. |
| `help` | Lists commands, shows one command's usage, or lists keys with `help keys`. |
| `ver` | Shows the Surf version. |
| `exit` | Quits Surf. |
| `matrix` | Digital rain (hidden). |
| `coffee` | A teapot has something to say (hidden). |
