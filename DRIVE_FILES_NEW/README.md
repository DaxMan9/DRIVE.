# DRIVE — Fitness & Nutrition Tracker

A self-contained fitness tracker for a weight-loss cut: weight trend, calorie
goals, workouts, meals, hydration and steps — all on-device, no account, no
backend. Built as a single dependency-free web app, deployed to GitHub Pages,
and packaged as a native Android app with Capacitor.

**Live demo:** (https://daxman9.github.io/DRIVE./)  <!-- update if you rename the repo -->

![Made with vanilla JS](https://img.shields.io/badge/JavaScript-vanilla-f7df1e)
![No dependencies](https://img.shields.io/badge/dependencies-none-brightgreen)
![PWA](https://img.shields.io/badge/PWA-installable-5a0fc8)
![Android](https://img.shields.io/badge/Android-Capacitor-3ddc84)

<!-- Add 2–3 screenshots here — recruiters look at these first.
     Drop images in a /screenshots folder and reference them:
![Today screen](screenshots/today.png) ![Meals](screenshots/meals.png)
-->

## Overview

DRIVE is a personal tracker built to support a cutting phase. Everything is
computed and stored client-side — the user's health data never leaves their
device. The same codebase runs three ways: in the browser, as an installable
PWA, and as a bundled Android APK.

## Features

- **Weight tracking** with a hand-drawn SVG trend graph, start/goal weights, and a goal reference line.
- **Calorie goal engine** — estimates maintenance calories and a target for a ~1 lb/week deficit, with a manual override.
- **Meal logging** with calories + macros, meal grouping (breakfast/lunch/dinner/snack), and daily totals against target.
- **Workout logging** with an exercise library (chest/back/legs/shoulders/arms/core) and auto-estimated calories burned.
- **Reusable presets** — save common foods and full workout templates for one-tap logging.
- **Water & step tracking** with daily goals and progress bars.
- **Offline-first** — installs to the home screen and works with no connection.
- **Data ownership** — JSON export/import for backups; nothing is uploaded anywhere.

## Engineering highlights

- **Zero dependencies, no build step.** The entire app is one self-contained HTML
  file with inline CSS and vanilla JavaScript — no framework, no bundler.
- **Offline PWA.** A service worker (network-first with cache fallback) plus a web
  app manifest make it installable and fully usable offline.
- **Custom data viz.** The weight trend chart is drawn directly as SVG with
  manual coordinate scaling — no charting library.
- **Nutrition science, done carefully.** BMR uses the Mifflin–St Jeor equation and
  automatically switches to Katch–McArdle when body-fat % is provided; TDEE
  applies an activity multiplier; the deficit target enforces a safety floor and
  is designed to avoid double-counting separately-logged workouts.
- **Exercise energy estimates.** Calories burned are computed from MET values ×
  body weight × duration, with a selectable intensity level.
- **Native packaging.** Wrapped with Capacitor into an Android APK so the app can
  ship fully offline and URL-independent — no hosting dependency.

## Tech stack

`HTML` · `CSS (custom properties / design tokens)` · `Vanilla JavaScript` ·
`Web Storage API (localStorage)` · `Service Workers / PWA` · `SVG` ·
`Capacitor (Android)` · `GitHub Pages`

## Run it locally

It's a static site — no install, no build:

```bash
# any static server works, e.g.
npx serve .
# or just open index.html in a browser
```

Also packaged as a native Android app via Capacitor for fully offline,
URL-independent use.

## Project structure

```
index.html        # the entire app (UI + logic + styles)
manifest.json     # PWA manifest
sw.js             # service worker (offline caching)
icon-192.png      # app icons
icon-512.png
```

## Data & privacy

All data is stored locally in the browser's `localStorage` / the app's storage.
There is no server, no analytics, and no third-party calls. Users can export a
JSON backup at any time from the in-app Data tab.

## License

MIT — see [LICENSE](LICENSE).
