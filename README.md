# Scores

A tiny card game scorekeeper for my phone. One HTML file, no build step, no server, no accounts. Scores save on the phone itself.

## Game types

**Basic.** Add players, then after each round type in everyone's points. Totals add up automatically. Use the +/- button for negative scores. Tap any past round to fix it. Option for "lowest score wins".

**Blob.** A paper style score sheet:
- Names across the top with each player's total, cards and NT/T down the left side
- Starts with the most cards possible (13 for 4 players) and goes down to 1, with the option to come back up
- Trump pattern is no trump, trump, trump, repeat. The trump suit itself is whatever card you flip, so the app doesn't track it
- Each player gets two small boxes per round (bid, then what they got) and a bigger box with their running total
- Wizard scoring: hit your bid and get 20 + 10 per trick. Miss and lose 10 for each trick you were off
- The row being played is highlighted

## Put it on your phone

It needs to be served from a web address once so the phone can install it. Easiest is GitHub Pages:

1. Push this repo to GitHub
2. Repo **Settings > Pages**, set Source to `main` branch, `/ (root)`, Save
3. Open `https://<your-username>.github.io/<repo-name>/` on your phone
4. **iPhone (Safari):** Share > Add to Home Screen. **Android (Chrome):** menu > Install app

After that it opens full screen like a normal app and works with no signal.

## Run it on your computer

```
python3 -m http.server 8000
```
Then open http://localhost:8000

## Notes

- Data is in the browser's local storage on each device. Deleting the app from the home screen or clearing Safari data wipes it.
- When you change `index.html`, bump `VERSION` in `sw.js` so installed copies update.
