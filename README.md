# ❄️ WINTER ARC — Training Log

> Your offline-first pocket coach for Winter Arc Month 1. Log lifts, track bodyweight,
> chase streaks, smash PRs — no account, no backend, no signal required.

**Live app:** `https://dheeraj-90040.github.io/winter-arc-tracker/index.html`
Install it on Android Chrome via **⋮ → Add to Home screen → Install** and it runs
fullscreen, straight from your home screen — even in a signal-blind gym basement.

---

## ✨ Features

| Area | What you get |
|---|---|
| 📓 Training log | Full Month 1 plan (Full Body A/B → Upper/Lower split), per-set weight × reps × RIR inputs |
| 📈 Progress charts | Top-set weight-over-time line per exercise, with session count, delta & **all-time best** |
| ⚖️ Bodyweight trend | Daily weigh-ins + dashed 7-day rolling average |
| 🔥 Streaks | Animated header streak pill (shine sweep, ember glow at 3+ days) + milestone toasts at 3/7/14/30 |
| 🏆 PR detector | Beating a previous best top-set fires a **NEW PR** celebration toast on save |
| 🗓️ Week summary | Done vs pending days, per-day volume bars, animated week-progress bar, total kg & sets |
| ✏️ Editable plan | Tweak sets/reps/rest per exercise when your gym lacks a machine — remembered, with reset |
| 📝 Session notes | Energy, sleep, how it felt — saved per day |
| 🔔 Gentle nudges | In-app reminder banner after 2+ silent days (no push, no spam) |
| 💾 Backup | One-tap `.json` export of everything |
| 📴 Offline-first | Service worker + cache-first strategy; your data lives in `localStorage` |

## 📱 Install on Android

1. Open the live URL in **Chrome** (online, once — this primes the offline cache).
2. Tap **⋮ → Add to Home screen → Install**.
3. Train. Airplane mode works. Your numbers persist between sessions.

## 🗂️ Project structure

```
winter-arc-tracker/
├── index.html      # The entire app — plan data, UI, charts, storage (single file)
├── manifest.json   # PWA installer profile (standalone, portrait, icons)
├── sw.js           # Offline cache manager (cache-first, network fallback)
└── README.md       # You are here
```

## 🔒 Privacy

Everything stays on your device. `localStorage` holds your logs under the
`winterArcData_v2` key. There is no server, no analytics, no account.
Fresh download = fresh (empty) log — use **Export backup (.json)** before switching devices.

## 🛠️ Local development

No build step. Just open it:

```powershell
cd "C:\Users\DELL\Desktop\Winter Arc Tracker"
# option A: double-click index.html
# option B: serve it (service workers need http)
npx serve .
```

Push to deploy — GitHub Pages serves from `main` → `/ (root)`:

```powershell
git add index.html manifest.json sw.js
git commit -m "Update"
git push origin main
```

> ⚠️ After changing `index.html`, bump `CACHE_NAME` in `sw.js`
> (e.g. `winter-arc-cache-v2` → `-v3`) so installed phones fetch the new shell
> instead of serving the old cached copy forever.

## 🧪 Tested

Logic is covered by a DOM-stubbed Node smoke suite (streaks, volume math,
history, empty-save guard, reminders, charts) — 29 checks, all green.

## 🗺️ Roadmap ideas

- [ ] Rest timer between sets
- [ ] Plate calculator
- [ ] CSV export for spreadsheets
- [ ] Deload / Month 2 plan import
- [ ] iOS `apple-touch` splash screens

---

*Built for the grind. Leave with energy remaining — that's the program working.* ❄️🔥
