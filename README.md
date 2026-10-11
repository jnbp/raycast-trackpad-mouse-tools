# Trackpad & Mouse Tools

Change trackpad and mouse settings from Raycast instead of digging through System Settings.

The main reason this exists: switching **secondary click** between two fingers and a corner. Some days
you want a two-finger tap, some days you rest a second finger on the trackpad and keep triggering it.
Give **Toggle Secondary Click** a hotkey and flip between the two in a second. The same goes for mouse
speed when you switch between a trackpad and a mouse, or between a desk and a couch.

## Commands

| Command | What it does |
| --- | --- |
| Toggle Secondary Click | Two fingers ↔ corner (bottom right by default, bottom left in the command preferences) |
| Secondary Click with Two Fingers | Sets it to two fingers |
| Secondary Click in Bottom Right Corner | Sets it to the bottom right corner |
| Secondary Click in Bottom Left Corner | Sets it to the bottom left corner |
| Toggle Tap to Click | Tap to click on or off |
| Toggle Natural Scrolling | Natural scrolling on or off (macOS applies it to trackpad and mouse) |
| Toggle Three Finger Drag | Three finger drag on or off |
| Set Mouse Speed / Set Trackpad Speed | Pick a speed from 1 to 10 right in the Raycast search bar |
| Increase Mouse Speed / Decrease Mouse Speed | Mouse tracking speed one step up or down |
| Left Click / Right Click / Middle Click | Click at the pointer, from a hotkey |
| Hold Left / Right / Middle Button | Press a button and keep it down until you run it again, click, or a few seconds pass |
| Release Mouse Buttons | Releases every button this extension holds |
| Trackpad & Mouse Settings | Every option below in one searchable list |

All one-shot commands confirm the change with a HUD, so they work well with hotkeys.

## Trackpad & Mouse Settings

The list is grouped like System Settings:

| Section | Settings |
| --- | --- |
| Trackpad · Point & Click | Secondary click, tap to click, look up & data detectors, click pressure, tracking speed, force click |
| Trackpad · Scroll & Zoom | Natural scrolling, zoom in or out, smart zoom, rotate |
| Trackpad · More Gestures | Swipe between pages, swipe between full-screen apps, Mission Control, App Exposé, Notification Center, Show Desktop |
| Mouse | Tracking speed, scrolling speed, double-click speed, pointer acceleration, Magic Mouse secondary click |
| Accessibility | Dragging style: off, without drag lock, with drag lock, three finger drag |

Press `↵` to toggle a setting or move to its next option, `⌘K` to pick any option, and `⌘⇧⌫` to restore the
macOS defaults for everything in the list.

## How it works

The extension writes the same preferences System Settings writes, for the built-in trackpad, the Magic
Trackpad and the Magic Mouse, and asks macOS to reload them so changes apply right away. Gesture settings
handled by the Dock (Mission Control, App Exposé, Show Desktop) restart the Dock for a moment.

Three finger drag and three finger swipes cannot be used together. When you turn on three finger drag, the
swipes move to four fingers, exactly as macOS does it.

If macOS ever refuses the live reload, the extension tells you, and the change takes effect after you log
out and back in. System Settings only shows a new value after you reopen it.

## Clicks from the keyboard

Trackpads have no middle button, and macOS offers no gesture for it. **Middle Click** clicks the middle
button wherever the pointer is: give it a hotkey in Raycast and use it to open links in a new tab, close
browser tabs, or paste the selection in a terminal. **Left Click** and **Right Click** work the same way.

The **Hold** commands press a button and keep it down. Raycast only knows when a hotkey is pressed, not
when it is released, so each hold command has a **Release** preference:

| Release | The button goes up |
| --- | --- |
| When I Run the Command Again | when you press the hotkey a second time |
| After the Next Click | when you click the trackpad or mouse once, the default (a left hold waits for a right click) |
| After a Few Seconds | after the number of seconds you set, 5 by default |

Running the command again always releases the button immediately, whatever the preference says. This is meant for 3D and design apps that orbit or pan while the middle
button is down. Some apps only react to a real mouse drag; many offer their own alternative, for example
Blender's *Emulate 3 Button Mouse*. If a button ever stays stuck, run **Release Mouse Buttons**.

All click commands use the Accessibility permission Raycast already has, so nothing else needs to be
installed.

## What it cannot do

A middle click on a three or four finger tap, remapping mouse buttons, smooth scrolling or a scroll
direction just for the mouse need an app that runs
in the background all the time and intercepts every input event, such as
[Mac Mouse Fix](https://macmousefix.com). A Raycast extension only runs while you use it, so it works
alongside those apps instead of replacing them.

## Privacy

Everything happens locally. The extension needs no network access. Only the click commands use a permission:
Accessibility, which Raycast already has.

## Install without the Raycast Store

1. Download **[install-trackpad-mouse-tools.zip](https://github.com/jnbp/raycast-trackpad-mouse-tools/releases/latest/download/install-trackpad-mouse-tools.zip)** and double-click it to unzip.
2. Double-click **install-trackpad-mouse-tools.command**. It checks Raycast and Node.js, downloads the latest release and imports the extension into Raycast.

**To update**, run the same file again. It always fetches the newest release.

### If macOS blocks the file

Files downloaded from the internet are not signed by Apple, so macOS may refuse to open them on the first
double-click. Either open **System Settings › Privacy & Security** and click **Open Anyway**, or run the
installer from Terminal, which is never blocked:

```bash
bash ~/Downloads/install-trackpad-mouse-tools.command
```

Requirements: macOS, [Raycast](https://raycast.com) and Node.js 22 or newer (installed automatically
through Homebrew if it is missing).
