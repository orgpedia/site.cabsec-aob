# India's ministries as cells

An animated chart of how the Government of India's ministries have divided, merged and been created since 1947.
Each cell is a ministry, or a department or office in no ministry; its size is the number of subjects the
Government of India (Allocation of Business) Rules, 1961 give it, after each amendment. Before 1961 the
ministries come from the cabinet lists, with sizes worked back from 1961. The page plays the whole run or
one Prime Minister's term (`#pm-manmohan-singh`).

This repository is only the published website, served by GitHub Pages. It is a static page with no build
step and no server:

| File | What it is |
|---|---|
| `index.html` | the page |
| `engine.js` | the animation engine (deterministic, seekable) |
| `timeline.json` | the data: units, frames, events, office-holders |
| `l-en.svg` | the orgpedia wordmark |
| `people/` | photos of Presidents, Prime Ministers and Cabinet Secretaries |
| `amend/<n>/` | a page for each amendment: its page images with each change boxed, the changes read, and every edit made to read it |
| `ministry/<name>/` | a page for each ministry, department and office: its names, family, size over time, changes and subjects; `ministry/` is the index |
| `rules/<n>/` | the Rules after each amendment: the First Schedule linked to the Second (`rules/0/` is the Rules of 1961) |
| `pages/` | the amendments' page images (WebP), and `data/pages.json`, their sizes |
| `assets/` | the style and script of the document pages |

## Updating

The data and the page are made in `orgpedia/cabsec_all`, in `flow/aob-cells_`:

```
make timeline   # rebuild ui/timeline.json from the AoB data
make page-images   # once: the page images from the PDFs (PAGES_LIMIT=500 for a part at a time)
make site       # copy the chart and write the amendment and Rules pages into this repository
```

Then commit and push here. To preview locally: `python3 -m http.server 8000` in this folder, then open
http://localhost:8000.

## GitHub Pages

Settings → Pages → Build and deployment: Deploy from a branch, `main`, folder `/ (root)`. The `.nojekyll`
file tells Pages to serve the files as they are.

Data: Cabinet Secretariat, Government of India (cabsec.gov.in). Office-holders: pmindia.gov.in,
presidentofindia.gov.in, cabsec.gov.in.
