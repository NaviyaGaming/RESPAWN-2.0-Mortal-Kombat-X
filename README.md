# RESPAWN 2.0 — Mortal Kombat X Player Selection Tracker

An interactive, single-file web app for running a round-robin qualifier to select the top 3 players (from a pool of 5) to compete in the RESPAWN 2.0 Mortal Kombat X esports event.

Built for the IEEE Student Branch & Computer Society Student Branch esports selection process.

**[Live demo →](#)** *(replace with your GitHub Pages URL once deployed — see below)*

---

## What it does

- Runs a **round-robin** format — all 5 players play each other once (10 matches total)
- Tracks results with a simple **points system**: Win = 3 pts, Draw = 1 pt, Loss = 0 pts
- Live **standings table** with rank badges (gold / silver / bronze for top 3)
- Interactive **match grid** — click a cell to cycle through Win → Draw → Loss → Clear
- Auto-updating stats: matches played, remaining, and qualified count
- Announces the **top 3 qualified players** once all matches are recorded
- Fully self-contained — no build step, no backend, no database. Everything runs in the browser.

---

## Tech stack

- Plain HTML, CSS, and vanilla JavaScript (no frameworks, no build tools)
- [Tabler Icons](https://tabler.io/icons) loaded via CDN for icon glyphs
- All state is held in-memory in the browser tab (see [Limitations](#limitations) below)

---

## File structure

```
.
├── index.html    # the entire app (rename mk_player_selection_tracker.html to index.html)
└── README.md
```

GitHub Pages serves whatever file is named `index.html` at the root of the published branch/folder, so make sure the tracker file is named `index.html` (or update your Pages settings to point at the correct file).

---

## Deploying to GitHub Pages

1. **Create a new repository** (or use an existing one) on GitHub.
2. **Add the file** — rename `mk_player_selection_tracker.html` to `index.html` and place it at the repository root (or inside a `/docs` folder if you prefer that convention).
   ```bash
   git add index.html README.md
   git commit -m "Add Mortal Kombat X player selection tracker"
   git push origin main
   ```
3. **Enable GitHub Pages:**
   - Go to your repository → **Settings** → **Pages**
   - Under **Build and deployment**, set **Source** to `Deploy from a branch`
   - Choose the branch (usually `main`) and the folder (`/root` or `/docs`, matching where you placed `index.html`)
   - Click **Save**
4. **Wait a minute or two.** GitHub will publish the site at:
   ```
   https://<your-username>.github.io/<repository-name>/
   ```
5. Open that URL — the tracker should load and be fully interactive.

---

## How to use it during the event

1. Open the deployed page (or the local file) on the day of the selection matches.
2. As each match finishes, find the row for the winning player and the column for their opponent in the **match grid**.
3. Click that cell:
   - 1st click → **Win** (green)
   - 2nd click → **Draw** (yellow)
   - 3rd click → **Loss** (red)
   - 4th click → clears the result
4. The **Standings** table and stats update automatically after every click.
5. Once all 10 matches are recorded, a banner appears naming the **3 qualified players** who advance to the RESPAWN 2.0 Mortal Kombat X tournament.
6. Use **Reset all results** to clear everything and start over (e.g., for a re-run or a different session).

---

## Tiebreaker rules

Standings are sorted by:
1. **Points** (Win = 3, Draw = 1, Loss = 0)
2. **Total wins** (if points are tied)
3. **Round wins** (manual tracking column, if you need a finer tiebreaker)

---

## Limitations

- **No persistence** — results are held only in the browser tab's memory. Refreshing the page or closing the tab clears all results. This is a live, in-session tool, not a saved record.
- If you need to save results between sessions, take a screenshot of the final standings, or note down the results before closing the page.
- Player names are hardcoded as "Player 1"–"Player 5" — see [Customizing player names](#customizing-player-names) below to use real names.

---

## Customizing player names

Open the HTML file in a text editor and find this line near the top of the `<script>` section:

```javascript
const PLAYERS = ["Player 1","Player 2","Player 3","Player 4","Player 5"];
```

Replace the placeholder names with your actual participants, e.g.:

```javascript
const PLAYERS = ["Nadeesha", "Kavindu", "Ishara", "Tharindu", "Sanduni"];
```

Save the file and re-deploy (commit and push) for the change to take effect on GitHub Pages.

---

## License

Free to use, modify, and distribute for your event.
