# 🚗 PLATEDEX — Vanity Plate Database

A searchable, crowdsourced database of weird, rejected, and spotted-in-the-wild vanity license plates. Seeded with real FOIA-released data from state DMVs.

## Live site

Deploy to GitHub Pages — just push this repo and enable Pages on the `main` branch. The whole app is a single `index.html`, no build step needed.

## Data sources

The seed data comes from public records releases:

| Source | State | Year | Notes |
|--------|-------|------|-------|
| Massachusetts FOIA | MA | 2022 | ~900 rejected plates from the RMV, released by Gannett papers before a new law shielded the records |
| NYC DMV FOIA | NY | 2010–2014 | Available on [Kaggle](https://www.kaggle.com/datasets/crawford/nyc-rejected-vanity-plates) |
| Colorado DMV | CO | 2022 | Reported by Denver Post |
| MuckRock FOIA project | CA, VA, OR + others | 2013–2014 | [github.com/dannguyen/dmv-vanity-plate-rejections](https://github.com/dannguyen/dmv-vanity-plate-rejections) |
| Crowdsourced | Various | Ongoing | Submitted via the site |

## Adding more data

To bulk-import new plates, edit the `SEED` array in `index.html`. Each entry looks like:

```js
{
  id: 99,
  plate: "EXAMPLE",
  state: "CA",
  status: "rejected",        // "rejected" | "approved" | "spotted"
  reason: "Why it's notable",
  tags: ["punny", "rude"],   // see ALL_TAGS in the script
  source: "CA FOIA 2023",
  year: 2023
}
```

## Features

- 🔍 Search by plate text
- 🗂 Filter by status (rejected / approved / spotted IRL)
- 🗺 Filter by state
- 🏷 Filter by tags (rude, punny, cryptic, car-related, nsfw-adjacent, sports, political, food, animals, names, cringe, based, inexplicable)
- 📋 Detail view for each plate
- ➕ Submit a sighting form (adds to session — for persistent submissions, wire up a backend or a GitHub Issues form)

## Making submissions persistent

Right now submissions only persist for the session. To make them permanent, a few options:

1. **GitHub Issues as a backend** — use the GitHub API to open an issue on submission, then manually curate + add to SEED
2. **Netlify Forms** — add `netlify` attribute to the form for free form handling
3. **Supabase** — free Postgres backend, swap the in-memory array for a real DB

## License

Data from FOIA releases is public record. Crowdsourced submissions are CC0.
