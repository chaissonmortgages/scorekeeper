# Scores

A tiny card game scorekeeper for my phone. One HTML file, no build step, no server, no accounts. Scores save on the phone itself.

## Game types

**Simple tally.** Add players, then after each round type in everyone's points. Totals add up automatically. Use the +/- button for negative scores. Tap any past round to fix it. Option for "lowest score wins".

**Blob.** Handles the whole game:
- Cards per round run down and back up (for example 7, 6 ... 1 ... 6, 7), or down only, or up only
- Shows the dealer and trump suit each round (Hearts, Clubs, Diamonds, Spades, optional no trump)
- Enter bids, then tricks won. It checks tricks add up to the cards dealt
- Optional dealer rule: the dealer can't bid the number that makes total bids equal the tricks available
- Scoring: make your bid exactly and get the bonus (default 10) plus your bid. Miss and get 0. Both are adjustable

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
