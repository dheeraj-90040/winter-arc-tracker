# ❄️ Winter Arc — Training Log

**Your entire Month-1 program, in your pocket, working in a basement with zero signal.**

Most workout apps need accounts, subscriptions, and cell service — exactly what you don't have mid-set in a concrete gym. This one is a single HTML file: open it once, install it, and it logs lifts, steps, bodyweight, streaks, and PRs fully offline, forever free.

## Overview

Winter Arc is an offline-first training log built around a 4-week re-entry program (Sept 9 → Oct 6, 2026): full-body machine days that evolve into an upper/lower split, RIR-based progression, walking + cardio targets, and daily steps. The app doesn't just display the plan — it enforces it: every session validates before it saves, every log is date-stamped, and every chart reads live from your own data.

**Live demo:** https://dheeraj-90040.github.io/winter-arc-tracker/index.html
(open once in Chrome → ⋮ → Add to Home screen → Install)

## Features

- **Guided daily logging** — every set validated before it counts; incomplete sessions can't fake a streak
- **"Mark as complete" switch** — flip it on to save with confetti, flip it off to unmark (your entries stay as a draft)
- **Proof you're progressing** — per-exercise strength curves, total-volume trend, this-week-vs-last-week, all-time bests
- **Steps dashboard** — goal arc, distance/kcal/active minutes, streak flame, achievements, weekly bars, one-tap logging modal
- **Bodyweight trend** — daily weigh-ins with a 7-day rolling average, so one bad morning never ruins the story
- **PR detector** — beat a previous best and the app throws you a full-screen celebration
- **Streaks that stick** — animated counter, milestone rewards at 3/7/14/30 days, gentle nudge when you go quiet
- **Your gym, your plan** — every exercise defaults to 3×12 but each one is individually customizable (timed holds for planks)
- **Zero-backend privacy** — everything lives in your browser's `localStorage`; no account, no tracking, no server
- **Native Android build** — the same code ships as an installable APK via Capacitor, with haptics on every save

## Demo

No screenshots yet — the fastest demo is the real thing (30 seconds):

1. Open https://dheeraj-90040.github.io/winter-arc-tracker/index.html in Chrome on your phone
2. Tap **⋮ → Add to Home screen → Install**
3. Turn on airplane mode and log a session — that's the whole pitch

Check the footer for the version tag (`v11`) to confirm you're on the latest.

## Installation

**Option A — use it in the browser (30 seconds, recommended):**

```text
1. Open the demo link above in Chrome (online, once — this primes the offline cache)
2. ⋮ → Add to Home screen → Install
3. Train. Airplane mode works.
```

**Option B — run it locally:**

```powershell
# No build step. Either double-click index.html,
# or serve it properly (service workers need http):
npx serve .
```

**Option C — build the native Android APK:**

```powershell
cd winter-arc-app
npm install
npx cap sync android
# then open android/ in Android Studio and press Run,
# or: .\android\gradlew.bat -p android assembleDebug
```

## Usage

- **Log tab** — pick your day, fill every set, flip **Mark as complete**. The switch won't turn on until every mandatory field is filled, and it tells you exactly what's missing.
- **Week tab** — see done vs pending days, per-day volume bars, and your total tonnage.
- **Progress tab** — strength curves, volume trend, and the week-over-week comparison.
- **Steps tab** — set a goal, hit **+ Log Steps**, watch bars turn green and badges unlock.
- **Footer** — Export backup (`.json`, do this before switching devices) and Reset (with confirmation).
- **Updating a saved day?** Toggle it off and on again — your entries are kept as a draft.

> ⚠️ Maintainer note: after changing `index.html`, bump `CACHE_NAME` in `sw.js`
> or installed phones will keep serving the old cached copy.

## Tech Stack

- **Single-file HTML/CSS/JS** — no framework, no bundler, no dependencies
- **`localStorage`** (`winterArcData_v2`) — the entire database, date-stamped and exportable
- **Service Worker** — cache-first offline shell (`winter-arc-cache-v*`)
- **Web App Manifest** — standalone install, custom launcher icons
- **Capacitor 8** — native Android wrapper (App, Haptics, StatusBar, SplashScreen plugins)
- **Node smoke suite** — 90+ DOM-stubbed checks covering validation, streaks, volume math, and rewards

## Roadmap

- [ ] Rest timer between sets
- [ ] Plate calculator
- [ ] CSV export for spreadsheets
- [ ] Month 2 plan import
- [ ] Screenshots + demo GIF for this README

## Contributing

This is a personal training project, but good ideas are welcome: open an issue describing the workout problem you hit, not just the feature you want. PRs that keep the single-file, zero-dependency, offline-first constraints get merged fastest.

## Why I built this

I needed a log that respects the actual conditions of training: chalky hands, no signal, no patience for sign-up screens. So I built the app I wanted to open between sets — strict enough to keep me honest, fast enough to never break flow.

## License

Personal project, all rights reserved for now — the code is public so you can learn from it. Ask before reusing it in your own app.

---

*Built for the grind. If this got you through a session, ⭐ star the repo — and go hit your steps.* ❄️🔥
