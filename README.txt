QUIET SUDOKU — INSTALLATION GUIDE
=================================

This is a small, self-contained Sudoku Progressive Web App (PWA).
The puzzle generator, answer checker and hint explanations run locally.
Once installed and cached, gameplay does not need an internet connection.

IMPORTANT: An HTML file opened directly from the iPhone Files app is NOT
a reliable way to install an offline PWA. The app must first be served
from an HTTPS website so Safari can register its service worker.

EASIEST FREE HOSTING OPTION: GITHUB PAGES
-----------------------------------------
You do not need to write code. This is a one-time upload of the files.

1. On a computer or iPhone, create/sign in to a GitHub account.
2. Create a new repository. Name it: quiet-sudoku
3. Upload ALL files from this folder to the repository's main/root folder:
   index.html, manifest.json, sw.js, icon-192.png, icon-512.png
4. In the repository, open Settings -> Pages.
5. Under Build and deployment, choose "Deploy from a branch".
6. Select branch "main" and folder "/ (root)", then Save.
7. Wait for GitHub Pages to publish the site. The URL will look like:
   https://YOUR-USERNAME.github.io/quiet-sudoku/
8. Open that URL in Safari on your iPhone while online.
9. Tap the Share button -> Add to Home Screen -> Add.
10. Open Quiet Sudoku from the new Home Screen icon while still online,
    leave it open for a few seconds, then test Airplane Mode.

OFFLINE CHECK
-------------
After installation and first load, enable Airplane Mode and reopen the
Home Screen app. If it loads, the cached app shell is working offline.
Keep the first online visit long enough for caching to complete.

FEATURES
--------
- Five difficulty settings.
- No timer, no ads, no accounts, no hint limits.
- Puzzle generation with a unique-solution check.
- Instant comparison against the puzzle solution.
- Unlimited hint explanations and answer reveal.
- Pencil notes, erase, restart, and local save/resume.

EXPLANATION ENGINE
------------------
- Naked singles and hidden singles.
- Locked candidates (pointing and claiming).
- X-Wing and Swordfish in row/column orientations.
- XY-Wing and XYZ-Wing candidate eliminations.
- Simple coloring, including same-color contradiction and color-trap eliminations.
- A bounded search-based contradiction proof as a fallback. This is not mislabeled as a full alternating-inference-chain (AIC) implementation.
- Iterative candidate elimination with a trace of the last deductions.
- A bounded exhaustive-search fallback for contradiction proofs when logical
  patterns do not force the requested cell. The app labels this as a search
  proof rather than pretending it is a named human technique.
- The advanced logical engine only claims to have proved the requested answer
  when its tracked candidates reduce that cell to the solution digit. If it
  cannot establish that, it falls back to a verified solution explanation.
- The reasoning board uses original clues plus user entries already verified
  correct, so a mistaken entry does not corrupt the explanation.
- Puzzle answers are generated from a completed valid grid, and clue removal
  is accepted only when the puzzle has a unique solution.

All solving, candidate checks, hints, and saves happen on the device.


Version 3.2 AIC update
The explanation engine includes an alternating-inference-chain / implication-graph proof pass. It derives strong links from bivalue cells and units with exactly two candidate positions, and weak links from mutually exclusive candidates. The AIC pass is used only when its implication search establishes that all alternatives to the verified answer contradict themselves. This is a practical AIC/forcing-chain subset, not an exhaustive implementation of every advanced Sudoku chain family.
