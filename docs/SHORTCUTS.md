# Surf shortcuts

Keyboard and mouse shortcuts for Surf. Type `help keys` in the console for a short list of the main ones. For everything you can type at the prompt, see [COMMANDS.md](COMMANDS.md).

## Window shortcuts

These work from anywhere in the window, whether the console or the page has the keyboard focus. Surf only reacts when you press exactly these keys, so combinations such as Ctrl+Alt+T are left for the page or Windows.

### Tabs

| Keys | What it does |
| --- | --- |
| Ctrl+T | Opens a new tab. |
| Ctrl+W | Closes the current tab. |
| Ctrl+Shift+T | Reopens the last closed tab. Surf remembers the last 20. Holding the keys down reopens one tab, not many. |
| Ctrl+Tab | Switches to the next tab. It wraps from the last tab to the first. |
| Ctrl+Shift+Tab | Switches to the previous tab. It wraps from the first tab to the last. |
| Ctrl+1 to Ctrl+8 | Switches to the tab in that position. Nothing happens if there is no such tab. |
| Ctrl+9 | Switches to the last tab. |

The number keys on the numeric keypad work too.

### Focus

| Keys | What it does |
| --- | --- |
| Ctrl+L | Moves to the console. |
| F6 | Switches between the page and the console. A tab with no page keeps the focus in the console. |

### Console size

| Keys | What it does |
| --- | --- |
| Alt+Shift+Up | Makes the console one line taller. |
| Alt+Shift+Down | Makes the console one line shorter. |

The `size` command sets the height as a percentage, and `mini` collapses the console to its prompt line. Sizes set with these keys, the divider or `size` last until you quit Surf. The size Surf starts with is a setting. See [COMMANDS.md](COMMANDS.md) and [SETTINGS.md](SETTINGS.md).

## Console keys

These work while you are typing at the prompt.

| Keys | What it does |
| --- | --- |
| Enter | Runs the line. |
| Tab | Completes the word with the selected suggestion. Press it again for the next match. |
| Shift+Tab | Goes back to the previous match. |
| Up | Moves up the suggestion list when it is open. Otherwise it brings back the previous command; Surf keeps the last 50. |
| Down | Moves down the suggestion list when it is open. Otherwise it moves forward to the next command, stopping at the newest one. |
| Esc | Hides the suggestion list when it is open. Otherwise it clears the line, and on an empty line it closes a console that grew to show a long answer. |
| Home | Moves the cursor to the start of what you typed, just after the prompt. |
| End | Moves the cursor to the end of the line. |
| Shift+Home, Shift+End | Selects from the cursor to the start or the end of the line. |
| Backspace, Left | Stop at the prompt. You cannot delete or move into it. |
| Mouse wheel | Scrolls the console. |

While you type, matching commands, sites and tabs are listed above the prompt with what each one does, and you can click one to take it. Turn the list off with Command suggestions in [Settings](SETTINGS.md). Completion only works when the cursor is at the end of the line. Pasting text that has several lines joins them into one line with spaces. Normal text editing keys such as Ctrl+C, Ctrl+V and Shift+arrows work as usual.

## Mouse

### Tab strip

| Action | What it does |
| --- | --- |
| Click a tab | Switches to it. Clicking a discarded tab wakes it up. |
| Middle-click a tab | Closes it. |
| Click the x on a tab | Closes it. The x shows on the current tab and when you point at another. In icon-only tab mode, only the current tab has one. |
| Click the plus button | Opens a new tab. |
| Click the back or forward arrow | Goes back or forward one page in the current tab, like `back` and `forward`. The arrows sit beside the logo and dim when there is nowhere to go. |
| Click a group label | Collapses the group, or expands it again. Tabs from the same site sit together under one label when smart grouping is on, and collapsed groups are not remembered after you restart. |
| Mouse wheel over the tabs | Scrolls the tab strip when there are more tabs than fit. |
| Drag the empty space in the title bar | Moves the window. |

Tabs cannot be dragged to a new order. Tabs from one site are kept together automatically.

### Window and page

| Action | What it does |
| --- | --- |
| Drag the divider above the console | Changes the console height. It snaps to whole lines. |
| Drag the bar between split pages | Changes how much room each page gets in a split view. |
| Click a page in a split view | Makes it the current page. A light line marks its top. |
| Click the empty page area | Moves the keyboard focus to the console. |
| Click into a web page | Gives the focus to the page, and closes a console that had grown to show a long answer. |
| Window buttons | Minimize, maximize and close, in the top right. Pointing at the maximize button offers the Windows 11 snap layouts. |
