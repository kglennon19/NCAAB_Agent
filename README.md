# NCAAB Line Scout — v3

A KenPom four-factor spread-setting agent for NCAA basketball. Built as a single HTML file with no server dependencies.

## Live App
**[Open the agent →](https://YOUR-USERNAME.github.io/ncaab-agent)**

## Features
- KenPom four-factor model (AdjEM, eFG%, TO%, ORB%, FT rate)
- Recency component — last-10 AdjEM momentum (captures tournament hot streaks)
- Neutral site detection — home court zeroed for all tournament games
- EV spread comparison vs market lines
- Daily archive + ATS tracking
- Post-mortem training loop — Pearson correlation analysis, weight auto-tuning
- Weight change changelog — before/after MAE isolation per adjustment
- Mobile responsive — works on Pixel/Android via Chrome address bar sync

## Data Sync (Desktop)
Paste scripts in browser F12 console:
- **Sync ESPN** — open `espn.com/mens-college-basketball/scoreboard`, paste script
- **Sync KenPom** — open `kenpom.com` (logged in), paste script

## Data Sync (Android / Pixel)
- Copy the script from the Game Slate tab
- Navigate to ESPN or KenPom in Chrome
- Tap the address bar → paste → Go

## Model Formula
```
Spread = Base(AdjEM × 0.55)
       + eFG% swing × (wEFG/0.15)
       + TO% swing  × (wTO/0.15)
       + REB swing  × (wREB/0.15)
       + FT swing   × (wFT/0.15)
       + Recency    × (wCtx/0.20)
       + Site (0 for all tournament games)
```

## Deployment
This repo auto-deploys to GitHub Pages on every push to `main`.
The live URL updates within ~60 seconds of any commit.

## Version History
See [commits](../../commits/main) for full change log.
