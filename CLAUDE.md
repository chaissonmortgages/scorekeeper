# Scores app: notes for Claude Code

Personal card game scorekeeper, installed on a phone as a PWA. Not a product. Keep it simple.

## Structure
- `index.html`: the whole app (HTML, CSS, vanilla JS). No frameworks, no build step, no dependencies.
- `sw.js`: offline cache. Bump `VERSION` on every change to `index.html`.
- `manifest.webmanifest`, `icon-192.png`, `icon-512.png`: home screen install.

## How the code is laid out
- State lives in `localStorage` under key `scores.v1` as `{ games: [...] }`.
- Simple game: `{ id, type: 'simple', name, players, rounds: [{ points: [...] }], lowWins, created, updated }`.
- Blob game: `{ id, type: 'blob', name, players, upAgain, cells, created, updated }` where `cells[round][player] = [bid, got]` as strings ('' when empty).
  Cards per round come from `blobSchedule()`, NT/T from `blobNT()`, scores from `blobPoints()` (Wizard scoring). Running totals are computed, never stored.
- `totals()` handles both types.
- Blob is deliberately a paper style grid with no validation. Keep it that way: Mack prefers pen and paper over anything fussier.
- Views: `renderHome`, `renderNew`, `renderGame` (which calls `renderSimple` or `renderBlob`). Each one rebuilds `#app` with innerHTML.

## Adding a new game type
1. Add a button to the game type selector in `renderNew` and any settings it needs.
2. Write `renderX(g)` and route to it from `renderGame`.
3. Push rounds as `{ points: [...] }` plus whatever extra fields you want for history.
4. Don't change the saved data shape in a way that breaks old games. If you must, migrate in `load()`.

## Style rules
- Mobile first, big tap targets, works one handed.
- Never use em dashes in UI text or comments.
- Don't add libraries or a build step unless asked.
