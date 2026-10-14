# Rians US — site mockup

Static mockup of rians.us built for review and hosted on GitHub Pages: the home page and the
*French Crème Brûlée Vanilla* product page, on one graphic base.

## Publish

1. Copy this `docs/` folder to the root of `Flog71/rians-us` and push to `main`.
2. Repo → **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main`, folder: **/docs** → Save.
3. Live a minute later at `https://flog71.github.io/rians-us/` (product page) and
   `https://flog71.github.io/rians-us/home.html` (home page).

To make the home page the entry point instead, rename `index.html` → `product.html` and
`home.html` → `index.html`, then update the two cross-links in each file.

## Files

| File | Role |
| --- | --- |
| `index.html` | product page — markup, styles and logic |
| `home.html` | home page — markup, styles and logic |
| `inspirations.html` | Inspirations (blog listing) |
| `french-customs-and-traditions.html` | article detail |
| `support.js` | runtime that renders the page |
| `assets/jar-spin.mp4` | scroll-scrubbed crème brûlée footage (2 MB) |
| `assets/creme-brulee-poster.png` | still frame shown while the video loads |
| `.nojekyll` | tells Pages to serve the files as-is |

## Before this becomes the production page

- Remove `<meta name="robots" content="noindex, follow">` and the `<link rel="canonical">`
  in `index.html` and `home.html`. Both are there so this mockup does not compete with the
  live rians.us page.
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

## Home page — content

Everything on the home page is the copy from rians.us, verbatim: the specialties introduction,
the two Sam's Club products, the three chapters of the story (1901 / 1951 / 1990s) and the four
secrets. Three blocks are **new proposals**, each switchable in the logic class at the bottom of
`home.html`:

| Prop | Block |
| --- | --- |
| `clubFinder` | *Found in one place only: Sam's Club* — pack shot, shop and club-finder buttons |
| `journal` | *From the journal* — three real blog articles pulled from rians.us/blog |
| `homeFaq` | *Questions we are asked most* — four brand-level Q&As, mirrored in the JSON-LD `FAQPage` |

Set any of them to `?? false` to drop the block. If `homeFaq` is dropped, remove the
`FAQPage` node from the JSON-LD in the `<head>` too.

## Menu

Crème Brûlée Vanilla · Chocolate Mousse · About us · Inspirations · Contact · **Buy at Sam's Club** (CTA).
"Inspirations" replaces "Blog"; its canonical stays `/blog/` so existing rankings are kept — if the
URL changes in production, add a 301 from `/blog/` to the new slug.

## Inspirations & article — SEO / GEO

- Listing: `CollectionPage` + `Blog` with every `BlogPosting`, `BreadcrumbList`, category filter.
- Article: `BlogPosting` (dates, author, image, section, `about`, `mentions` the Crème Brûlée, `speakable`),
  `FAQPage`, `BreadcrumbList`, visible breadcrumb, table of contents with anchors, H1 → H2 → H3 outline.
- GEO blocks (toggles in the logic class): `takeaways` (answer-first "In short" summary) and
  `productCard` (Crème Brûlée card in the café gourmand section). The festivals table and the third FAQ
  question are new content too.
- Article body is condensed from the live article; paste the final CMS copy in place.
