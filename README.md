# hunt-n-peck

[![Build status](https://ci.appveyor.com/api/projects/status/jet85wsdqn10grhk/branch/master?svg=true)](https://ci.appveyor.com/project/zsims/hunt-and-peck/branch/master)

> **This is a fork of [zsims/hunt-and-peck](https://github.com/zsims/hunt-and-peck).** It adds multiple interaction modes so a hint can move the mouse and click (left or right) in addition to the original UI Automation invoke. See [Interaction modes](#interaction-modes) below.

Simple vimium/vimperator style navigation for Windows applications based on the UI Automation framework. In essence, it works the same as screen readers or accessibility programs but with the goal of making any Windows program faster to use.

It works for any Windows program (excluding Modern UI apps :))

NOTE: hunt-n-peck is sporadically maintained, please consider one of the various forks.

# Download

<https://github.com/zsims/hunt-and-peck/releases/download/release%2F1.7/HuntAndPeck-1.7.zip>

# How to change font size

Find the application icon in tray, click right mouse button, select `Options`, then use the `FontSize` menu to change the font size.

# Screenshots

![ScreenShot](https://raw.github.com/zsims/hunt-n-peck/master/screenshots/explorer.png)
![ScreenShot](https://raw.github.com/zsims/hunt-n-peck/master/screenshots/visual-studio.png)

## To use

1. Launch the executable.
2. With any window focused, press `Alt + ;`
    - The tray can be highlighted with `Ctrl + ;`
3. An overlay window will be displayed, type any of the hint characters you see.

## Interaction modes

This fork adds modifier keys that change what happens when a hint is selected. Hold the modifier while typing the hint characters:

| Modifier | Action |
| --- | --- |
| _(none)_ | UI Automation **invoke** (the element's primary action, e.g. press a button). This is the original behaviour. |
| **Left Shift** | Move the mouse pointer to the hint and perform a real **left click**. |
| **Right Shift** | Move the mouse pointer to the hint and perform a real **right click** (e.g. open a context menu). |

Why the click modes? Invoke talks to a control through the UI Automation `InvokePattern`. Some applications (notably Electron / web-based apps such as Microsoft Teams) expose hints but do not implement that pattern, so invoke does nothing. A real synthesized mouse click goes through the normal OS input path and works on those controls.

Alternatively, Hunt and Peck can be launched via the command-line or AutoHotKey by specifying `/hint`:

```
hap.exe /hint
```

Or in tray mode with

```
hap.exe /tray
```

# Supported Elements

Only UI Automation elements with "Invoke" patterns are supported (and displayed).
