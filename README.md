# Tab Manager

[![Manifest V3](https://img.shields.io/badge/Manifest-V3-brightgreen.svg)](https://developer.chrome.com/docs/extensions/mv3/intro/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Cross-Browser](https://img.shields.io/badge/Browser-Chrome%20%7C%20Firefox%20%7C%20Edge%20%7C%20Brave-orange.svg)](#installation)
[![Version](https://img.shields.io/badge/Version-2.0.0-informational.svg)](manifest.json)

**Tab Manager** is a powerful, lightweight Manifest V3 browser extension built to declutter your browser, eliminate duplicates, reclaim system memory, and organize your workflow into structured workspaces.

---

## Key Features

### 🗂️ Smart Tab Grouping
- **Preset Grouping**: Automatically organize tabs into native browser tab groups by domain or subdomain.
- **Custom Mapping Rules**: Define custom domain-to-label rules (e.g., `github.com => Work`, `youtube.com => Media`).
- **One-Click Management**: Quickly expand or collapse tab groups across your active window or all windows.

### 🧹 Intelligent Duplicate Cleanup & Undo
- **Flexible Matching Modes**:
  - **Exact URL**: Matches full URLs identically.
  - **Ignore Hash (`#`)**: Groups URLs pointing to different anchors on the same page.
  - **Ignore Query (`?`)**: Merges links carrying tracking parameters (like `?utm_source`).
  - **Domain + Path Only**: Considers tabs duplicates if their host and path match.
- **Preservation Rules**: Choose which tab survives cleanup — keep the active tab, pinned tab, or most recently accessed tab.
- **Context Menu Integration**: Right-click any web page and select *"Close all duplicates of this tab"*.
- **Multi-Level Undo**: Safely recover from accidental cleanups with up to 30 undo steps.
- **Badge Counter**: Optional real-time badge on the toolbar icon showing currently detected duplicates.

### 🧘 Zen Mode
- Instantly stash and close all background tabs in the active window into a dedicated session.
- Free your workspace and mental focus with a single click, with full restoration available whenever you need it.

### 💾 Workspace Sessions
- **Session Snapshots**: Save your open tabs across the current window or all windows as named workspaces.
- **Instant Restore & Manage**: Reopen entire project workspaces in a new window or clean up old sessions.
- **Import & Export**: Backup and migrate workspaces via clean JSON payloads.

### ⚡ Memory Saver & Auto-Hibernation
- **Auto-Discard Inactive Tabs**: Free up system RAM by putting idle background tabs to sleep after a customizable period of inactivity.
- Hibernated tabs remain in your tab bar and reload automatically upon selection.

### ⏰ Tab Snooze
- Temporarily hide tabs and set an alarm for them to reappear automatically after a set duration (minutes or hours).

### 🔍 Quick Search & Tab Sorting
- **Instant Search**: Filter through tabs across open windows by title or URL with debounced real-time search.
- **Sort Options**: Order tabs alphabetically by domain or title, by recent activity, or with pinned tabs first.
- **Audio & Discard Indicators**: Visual markers highlight tabs currently playing audio or resting in a discarded state.

### 🛡️ Global Exclusions & Privacy
- **Rule Protections**: Prevent critical tabs from being closed or modified (skip pinned tabs, audible tabs, or muted tabs).
- **Domain Blocklist**: Exclude sensitive or mission-critical domains from automated actions.
- **100% Local & Offline**: All processing occurs locally within your browser. No analytics, tracking, or remote data transmission.

---

## Keyboard Shortcuts

| Shortcut (Default) | Action |
| --- | --- |
| `Ctrl + Shift + G` | Group tabs using current group preset |
| `Ctrl + Shift + D` | Remove duplicate tabs using current rules |
| `Ctrl + Shift + U` | Undo last duplicate cleanup |

> [!TIP]
> You can customize these shortcuts at any time via your browser's shortcut manager:
> - **Chrome / Brave / Edge**: `chrome://extensions/shortcuts`
> - **Firefox**: `about:addons` &rarr; Cog icon &rarr; *Manage Extension Shortcuts*

---

## Installation

### Google Chrome / Brave / Microsoft Edge
1. Clone or download this repository to your local machine:
   ```bash
   git clone https://github.com/sandeshpatel/tab-manager.git
   ```
2. Open your browser and navigate to the Extensions page:
   - Chrome / Brave: `chrome://extensions`
   - Microsoft Edge: `edge://extensions`
3. Enable **Developer mode** (toggle switch in the top-right corner).
4. Click **Load unpacked** and select the root directory of this repository (`tab-manager`).

### Mozilla Firefox
1. Open Firefox and navigate to `about:debugging#/runtime/this-firefox`.
2. Click **Load Temporary Add-on...**.
3. Select the [`manifest.json`](file:///home/reak/git/extension/tab-manager/manifest.json) file inside the project directory.

---

## Options & Configuration

Access the extension settings page by clicking the gear icon in the popup or right-clicking the extension icon and selecting **Options**:

- **General**: Set default sort order, scope (current window vs. all windows), and default snooze durations.
- **Automation & Cleanup**: Configure duplicate matching algorithms, duplicate preservation priority, scheduled background scans, and auto-discard idle thresholds.
- **Workspaces**: Create, restore, delete, import, and export saved workspace sessions.
- **Advanced Logic**: Define custom domain grouping rules, set global exclusion rules (pinned, audible, muted), and configure ignored domains.

---

## Architecture & Permissions

Built strictly adhering to **Manifest V3** with cross-browser compatibility:

- [`background.js`](file:///home/reak/git/extension/tab-manager/background.js): Service worker handling browser alarms, context menus, storage synchronization, tab grouping, auto-cleanup, and tab discarding.
- [`popup.html`](file:///home/reak/git/extension/tab-manager/popup.html) / [`popup.js`](file:///home/reak/git/extension/tab-manager/popup.js): High-performance popup UI with event delegation, DOM fragment rendering, and sanitized outputs.
- [`options.html`](file:///home/reak/git/extension/tab-manager/options.html) / [`options.js`](file:///home/reak/git/extension/tab-manager/options.js): Dedicated full-page options interface for comprehensive rule management.

### Permissions
- `tabs`: Query, organize, discard, and manage browser tabs.
- `tabGroups`: Create, label, color, and manage tab groups.
- `storage`: Synchronize user settings, workspace sessions, and undo stacks.
- `alarms`: Schedule periodic cleanup scans, memory saver checks, and tab snooze reminders.
- `contextMenus`: Provide right-click quick actions on web pages.

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
