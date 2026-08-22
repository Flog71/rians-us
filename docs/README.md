# Rians US — product page mockup

Static mockup of the *French Crème Brûlée Vanilla* product page (rians.us), built for review
and hosted on GitHub Pages.

## Publish

1. Copy this `docs/` folder to the root of `Flog71/rians-us` and push to `main`.
2. Repo → **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main`, folder: **/docs** → Save.
3. Live a minute later at `https://flog71.github.io/rians-us/`.

## Files

| File | Role |
| --- | --- |
| `index.html` | the whole page — markup, styles and logic |
| `support.js` | runtime that renders the page |
| `assets/jar-spin.mp4` | scroll-scrubbed crème brûlée footage (2 MB) |
| `assets/creme-brulee-poster.png` | still frame shown while the video loads |
| `.nojekyll` | tells Pages to serve the files as-is |

## Before this becomes the production page

- Remove `<meta name="robots" content="noindex, follow">` and the `<link rel="canonical">`
  in `index.html`. Both are there so this mockup does not compete with the live rians.us page.
- Replace `og:image` with an absolute URL (`https://www.rians.us/...`) — social networks
  do not resolve relative paths.
- Wire real Sam's Club ratings, then add `AggregateRating` to the JSON-LD block.
- Three blocks are switched off in this build (`reviews`, `airFryer`, `seoAnnex` in the logic
  class at the bottom of `index.html`): member reviews, the air-fryer method, and the internal
  SEO/GEO annex. Flip `?? false` to `?? true` to bring any of them back.

## SEO / GEO notes

The page is rendered client-side, so the crawlable substance sits in the static `<head>`:
`title`, `meta description`, canonical, Open Graph, and a JSON-LD graph carrying
`Product` (with `offers.seller` = Sam's Club and full `NutritionInformation`), `FAQPage`
(the six Q&As verbatim), `HowTo`, `Organization` and `BreadcrumbList`. A `<noscript>` block
repeats the key copy — ingredients, allergens, calories, where to buy, the FAQ — for crawlers
that do not run JavaScript.
