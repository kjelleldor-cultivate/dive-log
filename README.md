# Kjell Eldor's Dive Log

An interactive dashboard of my scuba diving: total dives, bottom time, depth, air consumption (SAC) and the sites I've dived. Every visit reads my log live from Google Sheets.

## How it works

- `index.html` is the whole site: one page with no build step, using d3 from cdnjs.
- The data comes from the **Dive Log** tab of a Google Sheet, published to the web as CSV (File → Share → Publish to web).
- To point it at a different sheet, change `CSV_URL` near the top of the script in `index.html`.

## Map

Known sites are pinned from a built-in list in `index.html` (`SITE_GEO`). For a new site that isn't on the list, add `Lat` and `Lng` columns to the sheet and fill them in for that row. Otherwise the site is pinned approximately to its region (for example Gozo), or listed under the map as not yet placed.

Site names are matched ignoring capitals, extra spaces and a leading "The".

## Updating

Add dives in the Google Sheet. The page picks them up the next time it loads, or straight away if you press **Re-read sheet**. Google can take up to about 5 minutes to refresh a published CSV.

The page expects the sheet's header row (`Dive No.`, `Date`, `Location`, `Duration (min)`, `Max Depth (m)` and so on) and stops reading at the `Summary` row. You can reorder columns or add new ones, but renaming headers will break it.

## Hosting

Settings → Pages → Deploy from a branch → `main` / root.
