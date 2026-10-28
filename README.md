# Todo: daily planner

A single-file, offline-capable daily to-do app with a morning and evening adhkar tab. It runs entirely in the browser: no server, no account, no tracking.

**Open the app:** https://husein-eng.github.io/Todo/

## Features

- **Daily planner**: tasks per date with priority, one or more colored categories, notes, checklists, and repeat rules (daily, weekly on chosen days, monthly).
- **Done, on target or off target**: mark a task done, then flag it as "off target" when it was done but not as planned (for example, praying but not at the mosque).
- **Week strip, history, and weekly summary**: jump between days, monthly calendar, 14-day chart, streaks, per-category stats, and a summary of this week against the last one. The by-date list shows the last 30 days; the calendar can still browse older months.
- **Paste a list**: paste a whole list and review the parsed tasks before adding. Supports `#category`, `!high`, `!medium`, `!low`, `@daily`, `@monthly`, `@mon,thu`, and `[x]` for done.
- **Quick actions**: swipe a task right to complete it or left to delete it, tap » to move it to tomorrow, undo recent changes, and save pasted lists as templates.
- **Sorting and views**: three compact dropdowns above the list for sort (priority or manual, with a lock against accidental drags; the order syncs), category filter (colored to match the task tags), and view options (compact mode, hide done, group by category, multi-select). In multi-select you can delete the chosen tasks on the current date only (repeating tasks are skipped for that day) or permanently on all days.
- **Prayer times tab**: the five daily prayer times with a countdown to the next one, calculated offline for your location.
- **Adhkar tab**: morning and evening adhkar (Hisnul Muslim) in Arabic with Indonesian and English meanings, repetition counts, and a tap counter. Long counts are split into at most 10 or 20 taps, and completed sessions appear in History. Counts and history sync across your devices (the newest change per day and time of day wins).
- **Themes and languages**: dark, light, or automatic theme, and an English or Indonesian interface, both switchable from the top of the main page.
- **Works offline** once opened, and can be installed to the home screen as an app.
- **Swipe** left or right outside the task cards to move between tabs.

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

## Prayer times

- Open the **Prayer** tab. Times for Fajr, Dhuhr, Asr, Maghrib, and Isha are calculated on your device with the [Adhan](https://github.com/batoulapps/adhan-js) library, so they work without internet. Sunrise is shown as a reference.
- The default location is Surakarta. Tap **Location and method** to open a panel where you can choose another city, use your device location, or enter coordinates. Choose the calculation method (Kemenag Indonesia approximation, Singapore/MUIS, Muslim World League, or Umm al-Qura) and the Asr convention (standard or Hanafi).
- The location is stored only in your browser. Times follow the device time zone.
- **Results are approximate.** They can differ by 1 to 2 minutes from the official Kemenag schedule or your local mosque. The Kemenag option uses the 20 and 18 degree angles with a 2-minute precaution, which is an approximation of the official method. Please check against a schedule you trust.

## App lock and restoring versions

- **PIN**: in the **Data** tab you can set a PIN of at least 6 characters. It encrypts the sync token and password stored in your browser and covers the screen. The app locks again after 5 minutes in the background. It does **not** encrypt your task data on the device, so anyone with access to your browser can still read your tasks.
- **Restore**: with sync connected, **Restore an earlier version** lists recent revisions of the encrypted gist, so deleted tasks can be brought back. You can still undo a restore.

## Privacy

- This repository contains only the app's code. **Your tasks are not stored here.** They live in your browser and, if you enable sync, in an encrypted gist in your own account.
- Your prayer-time location is stored only in your browser and is never sent anywhere.
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

The prayer time calculation uses [Adhan](https://github.com/batoulapps/adhan-js) (adhan-js), bundled in `index.html` and used under the MIT License:

```
The MIT License (MIT)

Copyright (c) 2016 Batoul Apps

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
