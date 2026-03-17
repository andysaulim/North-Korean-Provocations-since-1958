# North Korean Provocations Database (1958–2026)

**CSIS Beyond Parallel · Korea Chair**  
[beyondparallel.csis.org](https://beyondparallel.csis.org)

An interactive database tracking 483 verified North Korean provocations since 1958 — missile tests, nuclear detonations, conventional military attacks, terror operations, and hybrid/psyops activities.

## Live database
Hosted via GitHub Pages: `https://[your-username].github.io/[repo-name]/`

## Features
- 483 records across 7 categories (Missile, Nuclear Test, Nuclear Program, Conventional, Terror/Assassination, Hybrid/Psyops, Other)
- Multi-select category filter pills
- Filter by DPRK leader era and US president
- Year range and severity filters
- Full-text search with highlighting
- Stacked bar chart with DPRK leader / US president era overlays
- Summary tables — provocations by DPRK leader and by US president (clickable to filter)
- Sortable columns
- Per-event permalink and citation (Chicago, APA, MLA, BibTeX)
- CSV and JSON export (respects active filters)
- Social sharing — X, Bluesky, Facebook, LinkedIn, Instagram
- Mobile card layout at ≤640px
- Glossary tooltips for key acronyms (ICBM, SLBM, MLRS, etc.)

## Deployment

### GitHub Pages
1. Push this repo to GitHub
2. Go to **Settings → Pages → Source → Deploy from branch → main → / (root)**
3. Your database will be live at `https://[username].github.io/[repo]/`

### WordPress (Beyond Parallel)
1. Open `index.html` in a text editor, copy everything
2. In WordPress, add a **Custom HTML** block to your page
3. Paste the full file contents
4. Use a **Full Width** page template (no sidebar) for best results
5. Set `index.html` hosted URL as the featured image source for OG/social cards

### OG Social Image
Upload `nk-provocations-og.svg` to WordPress Media Library and set it as the page's Featured Image. Yoast SEO or All-in-One SEO will pick it up automatically for Twitter/LinkedIn cards.

## Updating records
Records are hardcoded in the `RECORDS` array in `index.html`. To add new events:
1. Find `const RECORDS = [` in the file
2. Add new record objects at the top of the array (newest first):
```js
{
  date: 'YYYY-MM-DD',
  cat: 'missile',           // missile | nuclear_test | nuclear_program | conventional | terror | hybrid | other
  event: 'Event name',
  desc: 'Full description.',
  sev: 4,                   // 1–5
  source: 'Yonhap',
  sourceType: 'yonhap',     // yonhap | kcna | nknews | kor | intl
  url: 'https://...',
  leader: 'kim_jong_un'     // kim_jong_un | kim_jong_il | kim_il_sung
}
```

For Google Sheets live sync (auto-update without editing the file), contact the Korea Chair team to set up the published CSV feed.

## Severity scale
| Score | Level | Examples |
|---|---|---|
| 5 | Critical | ICBMs, all nuclear tests, Cheonan sinking, Yeonpyeong shelling |
| 4 | High | IRBMs, long-range cruise missiles, nuclear program events |
| 3 | Moderate | SRBMs, MLRS tests, exchanges of fire with casualties |
| 2 | Low | Artillery fire, minor infiltrations, anti-ship missiles |
| 1 | Minor | Balloon launches, GPS jamming, loudspeakers |

## Citation
CSIS Korea Chair. *North Korean Provocations Database, 1958–2026.* Beyond Parallel. Center for Strategic and International Studies, 2026. beyondparallel.csis.org

## License
© 2026 Center for Strategic and International Studies. All rights reserved.  
Data compiled from open-source reporting. See individual source links within the database.
