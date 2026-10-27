# Todo: daily planner

A single-file, offline-capable daily to-do app with a morning and evening adhkar tab. It runs entirely in the browser: no server, no account, no tracking.

**Open the app:** https://husein-eng.github.io/Todo/

## Features

- **Daily planner**: add tasks per date, with priority, one or more categories, notes, and repeat rules (daily, weekly on chosen days, monthly).
- **Week strip and history**: jump between days, see a monthly calendar, a 14-day chart, streaks, and per-category stats.
- **Paste a list**: paste a whole list and review the parsed tasks before adding. Supports `#category`, `!high`, `!medium`, `!low`, `@daily`, `@monthly`, `@mon,thu`, and `[x]` for done.
- **Sorting and views**: sort by priority or manually (drag, with a lock to prevent accidental moves), compact mode, hide done, group by category, multi-select actions.
- **Undo** for recent changes, and templates for pasted lists.
- **Adhkar tab**: morning and evening adhkar (Hisnul Muslim) in Arabic with Indonesian and English meanings and the number of repetitions. The time of day is picked automatically and can be switched manually.
- **English and Indonesian** interface, with a toggle on the main page.
- **Works offline** once opened, and can be installed to the home screen as an app.
- **Swipe** left or right to move between tabs.

## Install on your phone or laptop

1. Open the link above in Chrome (or another modern browser).
2. Phone: tap the menu, then **Install app** or **Add to Home screen**. Laptop: click the install icon in the address bar.
3. Open it once with internet so it can be used offline later.

## Sync between devices (optional)

The app works fully without sync. To sync, open the **Data** tab and connect a GitHub token.

- Create a classic personal access token with **only the `gist` scope**.
- Choose an **encryption password** (at least 12 characters). Use the same token and password on every device.
- Data is encrypted in your browser (AES-GCM, key derived with PBKDF2) before it is uploaded to a secret gist in your own GitHub account. If you forget the password, the cloud copy cannot be opened.
- The token and password are stored only in your browser's local storage on each device. Do not use sync on shared devices.
- A token with the `gist` scope can access all gists in your account. Revoke it in GitHub settings if a device is lost.

## Privacy

- This repository contains only the app's code. **Your tasks are not stored here.** They live in your browser and, if you enable sync, in an encrypted gist in your own account.
- The site is served from a public repository (a GitHub Pages requirement on the free plan), so the code is visible to anyone. It contains no personal data, tokens, or passwords. Never commit secrets to this repository.

## Repository files

| File | Purpose |
|---|---|
| `index.html` | The whole app (HTML, CSS, JavaScript) |
| `manifest.webmanifest` | Lets the app be installed to the home screen |
| `sw.js` | Service worker for offline use |
| `icon-192.png`, `icon-512.png` | App icons |

## Updating the app

Replace `index.html` (and `sw.js` when it changes) through **Add file, Upload files**, then commit. Open the app twice, or hard refresh (Ctrl+Shift+R), to see the new version.

## About the adhkar content

- The Arabic and English text comes from the open dataset listed under Third-party notices, which follows *Hisnul Muslim* by Sa'id bin Ali bin Wahf al-Qahtani (chapter: morning and evening adhkar).
- The Indonesian text is a **meaning translation prepared by an AI assistant**, not an official translation.
- Hadith references per dhikr are not included. The grading of narrations, repetition counts, and time windows are matters of scholarship and may differ between scholars. **Please verify the content with a trusted reference or teacher before relying on it.**

## Third-party notices

The adhkar text is taken from [YousefAsalya/Islamic-Pro-azkar-API](https://github.com/YousefAsalya/Islamic-Pro-azkar-API), used under the MIT License:

```
MIT License

Copyright (c) 2026 Islamic Pro - Azkar API Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
