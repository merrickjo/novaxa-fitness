# Novaxa — Personalized Exercise Sets

[![Made with HTML](https://img.shields.io/badge/built%20with-HTML%2FCSS%2FJS-5eead4?style=flat-square)](https://github.com/merrickjo/novaxa-fitness)
[![No build step](https://img.shields.io/badge/build-none%20required-60a5fa?style=flat-square)](#getting-started)
[![License](https://img.shields.io/badge/license-unlicensed-lightgrey?style=flat-square)](#license)

Novaxa is a single-page web app that generates a personalized workout on the spot. Tell it how recovered you feel, what equipment you have, and how much time you've got — it builds a warm-up, main set, and cool-down, then runs you through it with a live timer.

**[Open the live app →](https://merrickjo.github.io/novaxa-fitness/)** *(enable GitHub Pages on this repo to activate this link — see [Getting Started](#getting-started))*

---

## Features

- **Recovery-aware programming** — a 0–100% recovery slider maps to a work/rest ratio and an allowed intensity range (tiers 1–3), so a rough day yields an easier session automatically.
- **Equipment-driven exercise pool** — select any combination of body weight, pull-up bar, kettlebell, dumbbell, incline treadmill, full treadmill, TRX, or skipping rope. Kettlebell and dumbbell entries take a load (kg) that scales rep ranges and filters out tier-3 moves once the load gets heavy.
- **Focus targeting** — Recommended (balanced), Core, Legs, or Upper.
- **Smart session builder** — guarantees at least one exercise per piece of equipment you checked, caps body-weight moves at ~50% of the set when other gear is selected, and rotates across muscle groups.
- **48-hour recovery memory** — session history is kept in `localStorage` so the generator avoids re-hammering a muscle group trained at moderate/high intensity in the last two days (and avoids exact repeats too).
- **Guided session player** — phase-by-phase timer (warm-up → work → rest → cool-down) with pause, skip, and restart, a running progress bar, an "up next" preview, and a full plan list.
- **20 or 30-minute sessions** — both include a built-in 2–3 minute warm-up and cool-down.

## How it works

1. **Setup screen** — pick recovery %, focus, equipment (+ load for weighted gear), and total time.
2. **Generation** — `generateWorkout()` filters the exercise library by equipment and recovery-allowed tiers, applies the heavy-load safety rule, then builds the main set in passes: equipment coverage → muscle-group rotation (respecting recency and the body-weight cap) → relaxed fallback passes so the set is never short.
3. **Session player** — the plan (warm-up block, main exercises with per-exercise work/rest, cool-down block) runs as a sequential timer.
4. **History** — on completion, the main exercises are logged to `localStorage` (`novaxa_history`, 14-day retention) to inform the next session's muscle-recovery check.

## Tech stack

Vanilla HTML, CSS, and JavaScript in a single `index.html` file. No framework, no build tooling, no backend — the exercise library, session logic, and UI all live client-side, with `localStorage` as the only persistence layer.

## Getting started

No installation or build step required.

**Run locally**
```bash
git clone https://github.com/merrickjo/novaxa-fitness.git
cd novaxa-fitness
open index.html   # or just double-click it
```

**Host it for free (GitHub Pages)**
1. Repo → Settings → Pages
2. Source: `Deploy from a branch` → Branch: `main` / `root`
3. Save — the app will be live at `https://merrickjo.github.io/novaxa-fitness/` within a minute or two.

## Roadmap ideas

- [ ] Export/share a generated session
- [ ] Editable exercise library (add custom moves/equipment)
- [ ] Progress dashboard over the stored session history
- [ ] PWA support for offline use on a phone at the gym

## Contributing

This is currently a single-owner project. Issues and pull requests are welcome — please open an issue first for anything beyond a small fix.

## License

No license has been added yet, which by default reserves all rights to the author. Add a `LICENSE` file (e.g. MIT) if you want to allow reuse.
