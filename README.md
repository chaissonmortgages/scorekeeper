# Scores

A tiny card game scorekeeper for my phone. One HTML file, no build step, no server, no accounts. Scores save on the phone itself.

## Game types

**Basic.** A paper style grid: names and totals across the top, one box per player per round. Type each score and the totals add up. New rows appear as you fill them in.

**Blob.** A paper style score sheet:
- Names across the top with each player's total, cards and NT/T down the left side
- Starts with the most cards possible (13 for 4 players) and goes down to 1, with the option to come back up
- Trump pattern is no trump, trump, trump, repeat. The trump suit itself is whatever card you flip, so the app doesn't track it
- Each player gets two small boxes per round (bid, then what they got) and a bigger box with their running total
- Wizard scoring: hit your bid and get 20 + 10 per trick. Miss and lose 10 for each trick you were off
- The row being played is highlighted

## Put it on your phone

Hosted on Netlify, linked to this GitHub repo. Every push to `main` redeploys automatically, and the installed app grabs the new version the next time it's opened with signal.

One time setup:
1. Netlify: Add new site > Import an existing project > GitHub > `scorekeeper`. Leave build settings blank (`netlify.toml` handles it) and deploy
2. Open the Netlify URL on your phone
3. **iPhone (Safari):** Share > Add to Home Screen. **Android (Chrome):** menu > Install app

After that it opens full screen like a normal app and works with no signal.

## Run it on your computer

```
python3 -m http.server 8000
```
Then open http://localhost:8000

## Notes

- Data is in the browser's local storage on each device. Deleting the app from the home screen or clearing Safari data wipes it.
- When you change `index.html`, bump `VERSION` in `sw.js` so installed copies update.
