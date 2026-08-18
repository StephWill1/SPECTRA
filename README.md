# SPECTRA
 
A daily remote sensing puzzle, in the spirit of [Wordle](https://www.nytimes.com/games/wordle) and [pydle.net](https://pydle.net). One small challenge a day, a handful of guesses, a result you can share.
 
**[Play it here→](#)** *https://stephwill1.github.io/SPECTRA/*
 
New puzzles drop every day at 00:00 UTC. Everyone gets the same one.
 
## How to play
 
There are two modes, switchable from the tabs at the top.
 
### Signature
You're shown a reflectance curve sampled from a single pixel, across six bands: Blue, Green, Red, NIR, SWIR1, SWIR2. Guess what surface it came from: healthy forest canopy, stressed vegetation, a burn scar, bare soil, open water, or impervious surface like pavement.
 
Guess wrong and you'll get a hint plus one fewer attempt remaining. Guess right (or run out of attempts) and you'll see the answer, the computed NDVI, and a short explanation of why the curve looks the way it does.
 
### Function
You're shown a "before" and "after" raster grid, plus a line of R code with the function name blanked out. Guess which `terra` operation produced the change: `aggregate()`, `focal()`, `terrain()`, `classify()`, `mask()`, or `crop()`. Same guess-and-hint format as Signature mode.
 
### Difficulty
Puzzles get harder as the week goes on:
 
- **Early week:** 3 easily distinguishable classes.
- **Mid week:** 5 classes.
- **Late week:** all 6, including confusable pairs and one fewer guess.
### Streak
Solve the day's puzzle and your streak goes up; miss it and it resets, same as most daily puzzle games. Your streak is saved in your browser, per mode.
 
### Sharing
After finishing, "Copy Result" gives you a spoiler-free emoji summary (🟩🟥⬛) to paste anywhere, without giving away the answer.
 
---
 
## For developers
 
This is a static site — plain HTML/CSS/JS, no server or backend required.
 
| File | Purpose |
|---|---|
| `index.html` | The game (this is `spectra.html`, renamed for GitHub Pages) |
| `extract-spectra.R` | Optional — pulls real Sentinel-2/Landsat pixel spectra via the Microsoft Planetary Computer STAC catalog and writes `puzzle-bank.json` |
| `puzzle-bank.json` | Optional — if present, Signature mode uses these real values instead of its built-in synthetic curves |
 
**Running locally:** opening `index.html` directly works, but if you want the `puzzle-bank.json` fetch to succeed, serve the folder instead of opening the file directly:
 
```bash
python3 -m http.server 8000
``` 
