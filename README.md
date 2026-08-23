<p align="center">
  <img src="assets/icon.png" width="128" height="128" alt="Mac Virtual Display — Native HiDPI virtual displays for remote Mac workflows">
</p>

<h1 align="center">Mac Virtual Display</h1>

<p align="center">
  <strong>Native HiDPI virtual displays for remote Mac workflows</strong><br>
  Create device-matched virtual displays for Galaxy Z Fold8 and iPad Pro, manage them from the menu bar, and optionally coordinate Sunshine streaming with safe display-layout restore.
</p>

<p align="center">
  <img src="https://img.shields.io/github/v/release/Joowonoil/MacVirtualDisplay?include_prereleases&label=Latest%20Release&color=blue" alt="Latest Release">
  <img src="https://img.shields.io/github/downloads/Joowonoil/MacVirtualDisplay/total?label=GitHub%20Downloads&color=green" alt="GitHub Downloads">
  <img src="https://img.shields.io/badge/Platform-macOS%2014.0+-blue" alt="Platform macOS 14.0+">
  <img src="https://img.shields.io/badge/Architecture-Apple%20Silicon-purple" alt="Apple Silicon">
</p>

<p align="center">
  <a href="https://ramterstudio.com/assets/macvirtualdisplay/MacVirtualDisplay.dmg">Download</a> ·
  <a href="https://github.com/Joowonoil/MacVirtualDisplay/releases">Releases</a> ·
  <a href="https://ramterstudio.com/mac-virtual-display/">Website</a> ·
  <a href="https://github.com/Joowonoil/MacVirtualDisplay/issues">Feedback</a>
</p>

> This is the official release, documentation, and issue-tracking repository for Mac Virtual Display. The application is proprietary; its source code is not published here.

> Download only from this repository or the official RamterStudio website. Development builds are not distributed publicly.

## Why Mac Virtual Display?

Remote-streaming quality depends on the Mac rendering a display that matches the client device. A mismatched physical monitor can introduce letterboxing, scaling, or an awkward desktop size.

Mac Virtual Display creates tested HiDPI profiles for remote devices and keeps the display workflow in one menu bar app.

## Display Profiles

| Device | Native resolution | HiDPI workspace | Refresh rate |
|---|---:|---:|---:|
| **Galaxy Z Fold8** | 2448 × 1848 | Looks like 1224 × 924 | 120 Hz |
| **iPad Pro 11-inch** | 2420 × 1668 | Looks like 1210 × 834 | 120 Hz |

The Fold and iPad profiles stay separate so each client can use its own native aspect ratio and workspace.

## Features

### Native HiDPI Virtual Displays

Create a crisp device-matched macOS workspace without depending on an always-on physical monitor.

### One-Click Profile Control

Choose a profile and turn its virtual display on or off directly from the menu bar.

### Safe Display-Layout Restore

The app saves the existing display arrangement before activation and restores it when the managed display is turned off or the app quits.

### Optional Sunshine Integration

When enabled, Mac Virtual Display coordinates Sunshine with the selected virtual display, restores the previous Sunshine output setting afterward, and stops only the Sunshine process it started.

### Read-Only Tailscale Status

See whether Tailscale is connected without giving Mac Virtual Display control over the Tailscale account or VPN lifecycle.

### Sunshine Setup Guidance

If Sunshine is not detected, the app explains that virtual displays still work independently and links to the official Sunshine download page.

## Typical Remote Workflow

1. Select the Fold or iPad profile.
2. Turn on the virtual display.
3. Optionally enable Sunshine integration for Artemis or Moonlight streaming.
4. Connect from the client device on the local network or through Tailscale.
5. Turn off the managed display to restore the previous Mac display layout.

## System Requirements

- **macOS 14.0+**
- Apple silicon Mac
- Sunshine is optional and required only for Sunshine-compatible streaming clients
- Tailscale is optional for local use and recommended for remote access outside the home network

## Installation

1. Download the signed and notarized [Mac Virtual Display DMG](https://ramterstudio.com/assets/macvirtualdisplay/MacVirtualDisplay.dmg) or use the [GitHub Releases](https://github.com/Joowonoil/MacVirtualDisplay/releases) page.
2. Open the DMG and drag MacVirtualDisplay to the **Applications** folder.
3. Launch Mac Virtual Display. It runs from the macOS menu bar.

Release checksums are published in [SHA256SUMS.txt](SHA256SUMS.txt).

Do not download development builds or repackaged copies from third-party sources.

## Privacy

Mac Virtual Display does not include analytics, tracking, or telemetry. Display profiles, layout backups, Sunshine configuration changes, and Tailscale status checks are handled locally on the Mac.

The app may contact the RamterStudio update feed when update checks are enabled. External links open only after an explicit user action.

## Source Code

Mac Virtual Display is proprietary software. This public repository contains release information, documentation, issue tracking, and approved product assets only. The application source code is maintained in a separate private repository.

## License

Mac Virtual Display and the materials in this repository are proprietary. See [LICENSE](LICENSE) for details.

## Feedback

If you have an issue or feature request, please [open an issue](https://github.com/Joowonoil/MacVirtualDisplay/issues) or email [ramterstudio@gmail.com](mailto:ramterstudio@gmail.com).

---

<p align="center">
  Made by <a href="https://ramterstudio.com">RamterStudio</a>
</p>
