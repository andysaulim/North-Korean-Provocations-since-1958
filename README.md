# North Korean Provocations Database (1958–2026)

**CSIS Beyond Parallel · Korea Chair**  
[beyondparallel.csis.org](https://beyondparallel.csis.org)

An interactive database tracking **540 verified North Korean provocations** since 1958 — missile tests, nuclear detonations, conventional military attacks, terror operations, cyber operations, and hybrid/psyops activity.

## Live database
Hosted via GitHub Pages: <https://andysaulim.github.io/North-Korean-Provocations-since-1958/>

## Contents at a glance
| Category | Records |
|---|---|
| Missile | 234 |
| Artillery / Conventional | 196 |
| Hybrid / Psyops | 40 |
| Other | 29 |
| Terror / Assassination | 13 |
| Nuclear Program | 13 |
| Cyber Operations | 9 |
| Nuclear Test | 6 |
| **Total** | **540** |

Records span the eras of Kim Il-sung (135), Kim Jong-il (90), and Kim Jong-un (315).

## Features
- 540 records across **8 categories**
- Multi-select category filter pills
- Filter by DPRK leader era and US president
- Year range and severity filters
- Full-text search with highlighting
- Stacked bar chart with DPRK leader / US president era overlays
- Summary tables — provocations by DPRK leader and by US president (clickable to filter)
- Sortable columns
- Per-event permalink and citation (Chicago, APA, MLA, BibTeX)
- CSV and JSON export (respects active filters)
- Social sharing — X, Bluesky, Facebook, LinkedIn
- Mobile card layout at ≤640px
- Glossary tooltips for key acronyms (ICBM, SLBM, MLRS, etc.)
- **Automatic dark mode** (follows the reader's OS/browser preference)
- **Keyboard-accessible** filters, sortable headers, and summary rows; screen-reader labels for severity
- **Resilient rendering** — the database, filters, and stats still work even if the charting library fails to load

## Deployment

### GitHub Pages
1. Push this repo to GitHub
2. Go to **Settings → Pages → Source → Deploy from branch → main → / (root)**
3. Your database will be live at <https://andysaulim.github.io/North-Korean-Provocations-since-1958/>

Open Graph / Twitter social-card tags are embedded directly in `index.html` and point at `nk-provocations-og.svg`, so shared links preview correctly with no extra setup.

### WordPress (Beyond Parallel)
1. Open `index.html` in a text editor, copy everything
2. In WordPress, add a **Custom HTML** block to your page
3. Paste the full file contents
4. Use a **Full Width** page template (no sidebar) for best results

### OG Social Image
`nk-provocations-og.svg` is referenced by the page's meta tags. On WordPress you can also upload it to the Media Library and set it as the page's Featured Image; Yoast SEO or All-in-One SEO will pick it up for Twitter/LinkedIn cards.

## Updating records

### Option A — edit the file directly
Records are hardcoded in the `RECORDS` array in `index.html`. To add new events:
1. Find `const RECORDS = [` in the file
2. Add new record objects at the top of the array (newest first):
```js
{
  date: 'YYYY-MM-DD',
  cat: 'missile',           // missile | nuclear_test | nuclear_program | conventional
                            // | terror | hybrid | cyber | other
  event: 'Event name',
  desc: 'Full description.',
  sev: 4,                   // 1–5
  source: 'Yonhap',
  sourceType: 'yonhap',     // yonhap | kcna | nknews | kor | intl
  url: 'https://...',
  leader: 'kim_jong_un'     // kim_jong_un | kim_jong_il | kim_il_sung
}
```

### Option B — Google Sheets live sync (no code edits)
`index.html` can load records from a published Google Sheet at page load, so the
team can update the database from a spreadsheet without touching the HTML.

1. Build a sheet with these columns, in order:
   `Date | Category | Event | Description | Severity | Source | SourceType | URL | Leader | Casualties`
   (the `Casualties` column is optional; a header row is auto-detected and skipped)
2. In Google Sheets: **File → Share → Publish to web → (your tab) → CSV**
3. Copy the published CSV URL and paste it into `const SHEET_URL = '';` near the top of the `<script>` block in `index.html`

If the sheet fails to load, or returns fewer than ~10 rows, the page automatically
falls back to the hardcoded `RECORDS` array so the database always renders. When a
sheet loads successfully, the masthead shows a “· synced live” indicator.

## Severity scale
| Score | Level | Examples |
|---|---|---|
| 5 | Critical | ICBMs, all nuclear tests, Cheonan sinking, Yeonpyeong shelling |
| 4 | High | IRBMs, long-range cruise missiles, nuclear program events |
| 3 | Moderate | SRBMs, MLRS tests, exchanges of fire with casualties |
| 2 | Low | Artillery fire, minor infiltrations, anti-ship missiles |
| 1 | Minor | Balloon launches, GPS jamming, loudspeakers |

## A note on aggregate figures
The database records only **individually documented incidents** with known dates and
sources. Some headline figures shown on the page are broader estimates that are *not*
derived from the per-record data (e.g. the “Documented Deaths” card, and the ROK figure
of 3,693 armed-agent infiltrations between 1954–1992). Those estimates live in clearly
labeled constants near the top of the `<script>` block (`ESTIMATED_DEATHS`,
`ESTIMATED_DEATH_EVENTS`) and can be revised there.

## Citation
CSIS Korea Chair. *North Korean Provocations Database, 1958–2026.* Beyond Parallel. Center for Strategic and International Studies, 2026. beyondparallel.csis.org

## License
© 2026 Center for Strategic and International Studies. All rights reserved.  
Data compiled from open-source reporting. See individual source links within the database.
