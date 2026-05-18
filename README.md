# Out of Road

A single-file, story-driven browser game inspired by Modest Mouse’s _The Lonesome Crowded West_ era vibe.

The project currently consists of one self-contained HTML file (`outofroad.html`) with:

- Handwritten HTML layout
- Inline CSS styling and animation
- Inline JavaScript game state, locations, branching actions, and rendering
- SVG scene drawing functions for each location

## Codebase review (quick overview)

### What’s here

- `outofroad.html`: the complete game app (UI, state machine, game loop, scene rendering, and interaction handlers).
- `modest-mouse-game.pdf`: supporting document/artifact for the project.

### Architecture notes

- **State-centric gameplay:** A single `state` object tracks money, bottles, inventory, flags, log entries, and location.
- **Location/action model:** Each location defines a description and list of actions with `available()` + `do()` callbacks.
- **Render-on-update flow:** User actions mutate state and trigger narrative/log/location updates.
- **No build step:** Open the HTML directly in a browser.

### Strengths

- Very approachable for prototyping (everything in one file).
- Story and interaction model are easy to extend (add a location/action block).
- No dependencies or tooling required to run.

### Improvement opportunities

- Split CSS and JavaScript into separate files for maintainability.
- Add a small testable game engine layer (pure functions for state transitions).
- Add linting/formatting (ESLint + Prettier) if the project grows.
- Add save/load support (e.g., `localStorage`).

## Getting started

### Run locally

Because this is a static HTML game, you can run it by either:

1. Opening `outofroad.html` directly in your browser, or
2. Serving the directory with a simple local server, for example:

```bash
python3 -m http.server 8000
```

Then visit <http://localhost:8000/outofroad.html>.

## Gameplay notes

- Goal: collect enough money for gas and get the Civic running.
- You’ll do this through conversations, odd jobs, and scavenging around town.
- Different actions become available as flags and inventory change.

## Suggested next steps

- Add a short “How to play” section in the UI.
- Introduce difficulty variants (e.g., required gas amount, random event frequency).
- Add ending variants and a score summary.

## License

No explicit license file is currently present. Add a `LICENSE` if you want clear reuse terms.

## Vercel deployment readiness

This project is now set up to deploy as a static site on Vercel:

- Added `index.html` as the default entry point Vercel serves at `/`.
- Added `vercel.json` with:
  - clean URL behavior
  - basic security headers
  - no-cache behavior for HTML
- Normalized smart punctuation in HTML/CSS/JS to standard ASCII quotes/dashes to avoid browser parse issues.

### Deploy steps

1. Push this repository to GitHub/GitLab/Bitbucket.
2. In Vercel, click **Add New Project** and import the repo.
3. Framework preset: **Other** (or leave auto-detected static).
4. Build command: _none_.
5. Output directory: _root_ (leave empty).
6. Deploy.

### Optional follow-ups

- Move inline CSS/JS out of `index.html` into `styles.css` / `game.js` for maintainability.
- Add a lightweight CI check (HTML validation + link check) before deployment.
- Consider self-hosting fonts to avoid third-party font request dependency.
