# GB system sell price and grid mix

KeelAI's half-hourly view of the GB system sell price and the generation mix, live at https://dist-flame-sigma.vercel.app/

The whole site is one file, `index.html`. There is no build step and nothing to install.

## What it shows

- System sell price by settlement period, with average, min, max and latest, a budget line, and CSV export
- Grid mix by settlement period, with gas share, the latest mix, a stacked chart by fuel type, and CSV export
- Today, 7 days, 30 days, month to date or a custom range of up to 93 days

## Branding

KeelAI design system: the navy dark scope, Light Signal Blue as the one accent, Segoe UI with Open Sans as the web fallback, and the KeelAI lockup and app icon. Data colours are kept as they were: fuel types, gas in orange, and green above budget and yellow below.

## Data sources

All data comes from the Elexon BMRS Insights API, which is public and needs no key.

- System sell price: `balancing/settlement/system-prices/{date}`
- Generation by fuel type (transmission-connected plant): `datasets/FUELHH`
- Actual or estimated wind and solar, including plant on local networks (B1630): `generation/actual/per-type/wind-and-solar`

Wind and solar in the grid mix come from B1630. Everything else comes from FUELHH. Small gas, CHP and battery sites on local networks aren't in either dataset.

## Hosting

The repo is connected to the existing Vercel project, so the link doesn't change.

- Framework preset: Other
- Build command: none
- Output directory: root of the repo
- Production branch: `main`

## Making changes

1. Create a branch, for example `grid-mix-v2`, and commit the new `index.html` to it.
2. Vercel builds a preview link for the branch. Check it on a phone and a laptop against live data.
3. When it looks right, merge the branch into `main`. That updates the live link.

If a change goes wrong, revert the commit on `main` and Vercel redeploys the previous version.
