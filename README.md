# Ascendant Skill-Tree Games

**Everything is now in one file: `index.html`.** It opens on a home screen where you pick which skill tree to play, and you can switch between them anytime with the **⇄** button in the top bar. Each game is a zoomable RPG skill tree with a real in-browser query engine, boss fights, XP, achievements, and Low/Med/High mode. All client-side — no server, no build step.

- **SQL Ascendant:** the high-value 20% of SQL plus an Application Support / Data & Analytics track (NULLs, CASE, text/dates, duplicates, UNION, CTEs, windows, indexes, transactions, troubleshooting).
- **Databricks Ascendant:** the Databricks Lakehouse for a support/analytics engineer — Spark SQL (runs live), Delta Lake (MERGE, time travel, OPTIMIZE/Z-Order, VACUUM, partitioning), PySpark literacy, and Platform & Ops (Unity Catalog, clusters, jobs/workflows, troubleshooting). Spark-SQL-style queries execute in the sandbox; Delta/PySpark/platform commands are shown as read-only reference plus active-recall quizzes.

Progress is saved separately for each game (different `localStorage` keys), so playing one never affects the other. The theme switches automatically (blue/purple for SQL, red/orange for Databricks).

**Play locally:** double-click `index.html`.

> The older standalone files (`databricks.html`, `SQL-SkillTree.html`) are now redundant — `index.html` contains both. You can delete them.

---

## Host it on GitHub Pages (access from your work laptop)

1. **Create a repo** on GitHub, e.g. `sql-ascendant` (Public is simplest; Private also works with Pages on most plans).
2. **Add the file.** Upload `index.html` to the repository root (the file must be named exactly `index.html`). Easiest path: on the repo page click **Add file → Upload files**, drag in `index.html`, then **Commit changes**.
3. **Enable Pages.** Go to **Settings → Pages**. Under **Build and deployment → Source** choose **Deploy from a branch**. Set **Branch = `main`** and **folder = `/ (root)`**, then **Save**.
4. **Wait ~1 minute.** Refresh the Pages settings screen; it will show your live URL:
   `https://<your-username>.github.io/<repo-name>/`
5. Open that URL on your work laptop. Bookmark it. Progress is saved per-browser via `localStorage`.

Both games live at the same URL — just pick one on the home screen and use **⇄** to switch.

### Updating later
Edit `index.html` in the repo (or re-upload it) and commit. Pages redeploys automatically in a minute or two.

---

## Note on the SQL engine
The interactive sandbox uses **sql.js** (SQLite compiled to WebAssembly), loaded from the cdnjs CDN at runtime. GitHub Pages serves over HTTPS, so this works out of the box.

If your **work network blocks cdnjs**, the skill tree still works but the query sandbox won't run. To make it fully offline/self-contained, host the two engine files yourself:

1. Download `sql-wasm.js` and `sql-wasm.wasm` (v1.10.3) from cdnjs and put them in the repo next to `index.html`.
2. In `index.html`, change the script tag and the `locateFile` path from
   `https://cdnjs.cloudflare.com/ajax/libs/sql.js/1.10.3/`
   to `./` (the local folder).

Ask and I can produce that self-contained version for you.

---

## What's inside
- **23 nodes** across a core SQL spine and a 🛠️ app-support track: NULLs & COALESCE, CASE logic, text/pattern matching, dates, UNION, finding duplicates, window functions, CTEs, indexes/EXPLAIN, transactions, and a Troubleshooting capstone.
- **Each node:** Discover (visual) → Explore (multi-example sandbox) → Practice → Master → Boss → 💎 Elite (High mode only).
- **Low / Med / High mode** in the top bar genuinely scales the challenge: each node has a difficulty ladder, and the **Challenge tab serves a harder question** as you go Low → Med → High (Low = core question + auto-hints; High = the boss/elite-tier question + 1.5× XP). Switch mode anytime to re-attempt a node at a tougher tier; clearing all tiers fully masters the node (👑).
- **Game systems:** XP, levels, combo streaks, 11 achievements, an intelligent "recommended next" guide.

Answers are graded by comparing result sets, so any correct phrasing of a query passes.
