# Water Softener of Indianapolis, IN — Workspace

## Boilerplate build status (informational — not per-city data)
This section tracks what the *template itself* contains, independent of any
city. Update it when the boilerplate gains or loses a component; do not fill
in per-city data here — that's the rest of this file, below.

| Component | Status |
|---|---|
| Keystatic CMS | ❌ REMOVED — phone-call-based rank-and-rent model, site.config.ts edited directly, see PROVISION.md "CMS — No Keystatic" |
| Output mode | Static (`output: "static"`, `@astrojs/vercel`, zero serverless functions) |
| Full design system (global.css) | ✅ deep navy `#1B3A6B` / warm gold `#C89B3C` theme, already set in `site.config.ts`'s `design` object before this session started — a deliberate per-site override from the boilerplate's teal/orange default |
| Layout.astro (utility bar + Services-dropdown nav + minimal footer) | ✅ unchanged from boilerplate |
| Homepage (hero, brand-IS opening, services grid, GPG data, 2 alternating image-text, IndianapolisMap, why-choose-us, FAQ accordion, slim CTA bar) | ✅ fully written this session, brief-grounded, Koray rules applied |
| PageHero.astro (split inner-page hero: breadcrumbs, H1, opening paragraph, CTAs left; real photo or GPG stat-card right) | ✅ wired into all 21 inner pages — 19 now show a real photo, 2 (`installation`, `salt-free-installation`) still show the GPG stat-card fallback, no photo generated for those yet |
| Favicon (`public/favicon.svg`) | ✅ added in a later session — navy `#1B3A6B` rounded-square badge, light water-droplet mark, warm gold `#C89B3C` highlight ellipse tying in the accent color, distinct from the droplet marks used on the Minneapolis/Tampa/Henderson sibling sites |
| Real photography (`src/assets/images/`) | ✅ added in a later session — 22 WebP images (homepage hero + 2 alternating-section tiles + 19 inner-page headers). Sourced as 23 AI-generated (Gemini) images saved to `public/`, hand-matched to the correct page by visually inspecting each one's content (filenames were meaningless hashes), converted to WebP via `sharp` and moved into `src/assets/images/`, then wired through `astro:assets`'s `<Image>` component on the homepage and via a `headerImage` import + `image={headerImage}` prop on each `<PageHero>` call. 1 of the 23 source images was an unused near-duplicate; 2 header slots (`installation-header`, `salt-free-installation-header`) have no matching photo yet — see Notes |
| Opening paragraph pattern (Glendale Elite: Brand IS on homepage, Brand OFFERS inside the hero on inner pages) | ✅ applied on every page |
| QuoteForm.astro | ✅ present, `businessEmail` still the `BUSINESS_EMAIL` placeholder token (no tenant yet) |
| Breadcrumbs.astro | ✅ present |
| LocalSchema.astro | ✅ present |
| GPGSlider.astro | ✅ added to `water-quality.astro` this session (PROVISION.md Step 5b) |
| GPGSliderMini.astro | ✅ added to `comparison.astro` this session |
| SystemTour.astro | ✅ added to `installation.astro` this session |
| QuickFacts.astro | ✅ **new this session** — a reusable, site.config-driven "Verified Local Water Data" callout added to every EAV-scored page. Weaves all 7 non-placeholder EAV facts (GPG range + label, water source, water authority, population, county, ZIP codes, neighbourhoods) into 3–4 short sentences using the exact literal formatting the quality gate's Rule 14 substring-matches against, plus an "as of 2026" currency signal (Rules 33/38) and a hardness-scale comparison sentence (Rule 42). Not part of the original boilerplate — built to solve a real, recurring EAV-density gap found while scoring this site. |
| IndianapolisMap.astro | ✅ city-specific, built this session from `CityMap.astro`, using Henderson's `HendersonMap.astro` as the interaction-pattern reference. Verified interactively — see Notes. |
| CLAUDE.md / PROVISION.md | ✅ pre-existing, unchanged |
| InstallationProcess.astro / Testimonials.astro | ❌ not built — not required by PROVISION.md Step 5b (only the neighbourhood map is listed as required city-specific work) |

**Next action**: This site is content-complete, quality-gated, has a favicon
and real photography, and is pushed to GitHub. Remaining provisioning steps
(7–10: Vercel deploy, custom domain, Search Console, citations) have not
been done yet — see Provisioning checklist below. Optionally: generate the
2 missing photos (`installation-header`, `salt-free-installation-header`)
before deploying.

## Site identity
- Domain:           watersoftenerofindianapolis.com
- City:              Indianapolis, IN
- GPG:               12-20 (Very Hard) — Citizens Energy Group's published range
- Water source:      The White River, Fall Creek, Eagle Creek Reservoir, Geist Reservoir, and Morse Reservoir, supplemented by area groundwater wells
- Water authority:   Citizens Energy Group (Citizens Water)
- Primary keyword:   water softener indianapolis in (search volume unverified — no keyword-tool access this build)
- GitHub repo:       https://github.com/assignmenthelptalk/-Indianapolis (private, `main` branch, pushed)
- Vercel project:    not yet created
- Vercel URL:        not yet created
- Live domain:       not yet connected — Step 8 not done

## Folder structure
- Local-SEO-Toolkit/
    data/watersoftenerindianapolisin/briefs/               ← 24 EAV briefs (one per fixed page + per neighbourhood)
    data/watersoftenerindianapolisin/quality-report-*.json ← quality gate reports
- waterSoftenerProjects/watersoftenerindianapolisin/
    src/site.config.ts                     ← city config (only file meant to change per city) — not touched this session, already fully filled
    src/components/QuickFacts.astro        ← new reusable EAV-density component (this session)
    src/components/IndianapolisMap.astro   ← new city-specific neighbourhood map (this session)
    src/pages/                             ← all page files
    dist/                                  ← built static HTML (after npm run build)

## Page status
All 22 pages have real, brief-grounded, Indianapolis-specific content —
Koray's 14 core writing rules applied, EAV facts woven in, Step 6c gotchas
addressed proactively. `about` and `contact` are written but are not scored
by the quality gate (no EAV brief exists for these two page types — see
`eavPageTypes.js` and PROMPTS.md's "all pages except about and contact"
note), matching this portfolio's established convention.

| Page                           | Written | Score  | Ship-ready |
|--------------------------------|---------|--------|------------|
| homepage                       | ✅      | 83/100 | ✅         |
| water-quality                  | ✅      | 86/100 | ✅         |
| hard-water                     | ✅      | 91/100 | ✅         |
| installation                   | ✅      | 80/100 | ✅         |
| comparison                     | ✅      | 81/100 | ✅         |
| faq                            | ✅      | 84/100 | ✅         |
| neighbourhood                  | ✅      | 80/100 | ✅         |
| repair                         | ✅      | 81/100 | ✅         |
| about                          | ✅      | —      | — (not scored, no EAV brief) |
| contact                        | ✅      | —      | — (not scored, no EAV brief) |
| quote                          | ✅      | 96/100 | ✅         |
| products                       | ✅      | 83/100 | ✅         |
| whole-home-filtration          | ✅      | 82/100 | ✅         |
| reverse-osmosis                | ✅      | 79/100 | ❌         |
| resin-bed-replacement          | ✅      | 85/100 | ✅         |
| brine-tank-cleaning            | ✅      | 84/100 | ✅         |
| salt-based-installation        | ✅      | 88/100 | ✅         |
| salt-free-installation         | ✅      | 86/100 | ✅         |
| water-softener-sizing          | ✅      | 90/100 | ✅         |
| new-construction-installation  | ✅      | 80/100 | ✅         |
| control-head-repair            | ✅      | 88/100 | ✅         |
| free-water-test                | ✅      | 94/100 | ✅         |

22 pages total (excludes `thank-you` and the QDP-gated `[serviceArea]`
dynamic route, which builds zero pages while `serviceAreas: []`).
**19 of 20 scored pages are 80+ and ship-ready. Average score: 85/100.**
✅ = done | 🔄 = in progress | ⏳ = not started | ❌ = blocked

## Quality gate (last run: 2026-09-25, rescored after real photography was added)
Score threshold: 80/100
Run: cd C:\Users\lenevo\Local-SEO-Toolkit
     npm run score-built-site -- --business watersoftenerindianapolisin --dist C:\Users\lenevo\waterSoftenerProjects\watersoftenerindianapolisin\dist

Rescored after wiring in real photography (favicon + 22 images) to check
whether replacing the reverse-osmosis page's GPG stat-card fallback with a
real photo would close the last point. **It did not move the score** —
still 79/100, same set of failed rules. That photo swap doesn't touch page
prose, so this was expected in hindsight; it's confirmed rather than
assumed now.

**reverse-osmosis (79/100, 1 point under threshold)** — every remaining
failed rule traces to a documented, deliberate trade-off rather than
missing content:
- Rules 2 + 12 (10 pts): the standard FTC affiliate-disclosure sentence
  ("We may earn a commission... if you purchase through them") trips both
  the hedge-word check and the conditional-structure check. PROVISION.md's
  Step 6c gotchas explicitly say to leave this sentence untouched — this is
  an accepted, permanent gate failure on any page carrying an affiliate
  link (also present on comparison/products/whole-home-filtration, which
  clear 80 anyway because they don't stack as many of the other structural
  losses below).
- Rule 6 (5 pts): an FAQ question ("How often does an RO membrane need to
  be replaced?") reads as passive to the checker — per Step 6c, FAQ
  `<summary>` questions are not rewritten into declarative claims to chase
  this rule.
- Rules 15/20 (2 pts): CTA/nav link text ("[📞 Call for a Free
  Consultation][Get a Free Water Softener Quote in Indianapolis]" and
  similar) gets swept into the surrounding paragraph by the checker's naive
  sentence splitter, reading as a context-setting opener with no action
  verb. Confirmed this session to be unrelated to the PageHero image vs.
  stat-card fallback — the score was identical before and after the real
  photo was wired in.
- Rule 26 (1 pt): breadcrumb list items have no preceding intro sentence
  (they're the first element on the page) — an accepted structural loss,
  consistent with the existing breadcrumb-anchor-text gotcha.
- Rule 28 (1 pt): the mandated H1 ("Reverse Osmosis Systems in
  Indianapolis, IN | Trusted Local Specialists" — PROVISION.md's fixed
  pattern for this page type) contains no literal "water"/"softener"/
  "installation" token the checker's Rule 28 keyword list requires.
- Rule 31 (1 pt): one remaining >35-word sentence, same CTA/nav-link chrome
  merge as Rules 15/20.
- Rule 32 (1 pt): "Very Hard" (the WQA classification label, `gpgLabel`)
  reads as an empty intensifier to the checker — unavoidable while
  displaying the real classification, same as every other page.

Three concrete fix attempts were made in an earlier session and verified
via rebuild+rescore (reordering an FAQ question to lead with "if", adding a
single terminating period to break up the product-card feature list into a
shorter sentence, rewording the card's lead sentence to avoid a
pronoun-opener flag) — each was kept only if it didn't regress the score.
The page settled at 79/100; crossing to 80 would require touching the
shared CTA/nav link markup or the affiliate disclosure wording, both of
which are used by — or would risk — the 19 other already-passing pages.

## Current task
All 22 pages written this session with brief-grounded, Indianapolis-specific
content. Three interactive components wired in (GPGSlider → water-quality,
GPGSliderMini → comparison, SystemTour → installation). `leaflet` +
`@types/leaflet` installed; `IndianapolisMap.astro` built from `CityMap.astro`
using Henderson's `HendersonMap.astro` as the reference implementation, with
5 verified neighbourhood pins (Broad Ripple, Meridian-Kessler, Fountain
Square, Irvington, Castleton) and neighbourhood-specific hard water issues
tied to each area's real housing-stock character (Broad Ripple/Irvington:
older streetcar-era/Victorian housing with original galvanized plumbing;
Meridian-Kessler: large historic homes with multiple original bathrooms;
Fountain Square: dense older bungalow district; Castleton: newer
1970s–2000s construction with different exposure via pools/irrigation/
tankless heaters). `astro.config.mjs` (`ssr.noExternal: ["leaflet"]`) and
`Layout.astro` (Leaflet stylesheet `<link>`) both updated. `npm run build`
passes clean (0 errors, 0 warnings) throughout. Quality gate run and
iterated to 19/20 pages ship-ready (85/100 average) — see Quality gate
section above for the one page (reverse-osmosis, 79/100) still under
threshold and exactly why. Map verified interactively via a local dev
server: all 5 pins visible simultaneously, hover tooltip, click-to-report,
and Reset View all confirmed working — the default view needed adjustment
(see Notes) after an initial check showed only 2 of 5 pins visible.
Business registered in Local-SEO-Toolkit's `config/businesses.json` (a
toolkit-local step, not a deployment) so the quality gate could run.
**Since this build**: a favicon and real photography (22 images) were
added in a later session, and the repo was pushed to GitHub — see Site
identity above. **Still not done**: Vercel deploy, custom domain, DNS,
Search Console, citations, and service-area pages.

## Local data
- Neighbourhoods:  Broad Ripple, Meridian-Kessler, Fountain Square, Irvington, Castleton
- ZIP codes:       46220, 46203, 46219, 46256
- County:          Marion County
- Population:      887,642 (2020 Census, Indianapolis balance)

## SpringWell affiliate links
- /follow/softener/ — salt-based softener (wired into homepage + comparison + products)
- /follow/combo/    — softener + filtration combo
- /follow/ro/       — reverse osmosis system

## Provisioning checklist
Mirrors PROVISION.md step-for-step, in the same order — check PROVISION.md
itself if a step here needs more detail than fits on one line.

- [x] Step 1 — GitHub repo — created and pushed: https://github.com/assignmenthelptalk/-Indianapolis (`main`)
- [x] Step 2 — Boilerplate copied into the project + `npm install` (done before this session)
- [x] Step 3 — `src/site.config.ts` filled in with real city data (done before this session; phone/email still placeholders — no tenant yet)
- [x] Step 4 — ~~Keystatic~~ REMOVED — no CMS step
- [x] Step 5 — Content written for all 22 pages
- [x] Step 5b — GPGSlider, GPGSliderMini, SystemTour wired in; IndianapolisMap built and verified interactively
- [x] Step 6 — `npm run build` — 0 errors, 0 warnings confirmed (multiple times, most recently after the map center/zoom fix)
- [~] Step 6b — Quality gate run: 19/20 pages 80+ (85/100 average). reverse-osmosis at 79/100 — see Quality gate section for the specific, documented reasons and what would be required to close the last point
- [ ] Step 7 — Deploy to Vercel — **intentionally out of scope this session**
- [ ] Step 8 — Custom domain — **intentionally out of scope this session**
- [ ] Step 9 — Google Search Console — **intentionally out of scope this session**
- [ ] Step 10 — Citations — **intentionally out of scope this session**

## Notes
_Add any city-specific notes, open data gaps, or decisions made here._

- **Open data gaps, marked `[PLACEHOLDER]`-equivalent (`[NEEDS DATA: ...]`)
  in the generated EAV briefs, never invented**: typical install duration,
  warranty terms, exact local price range, financing options, local
  permit/code requirement specifics, maintenance/salt-refill interval,
  household-sizing-by-grain-capacity table specifics, and whether a free
  trial/test period exists beyond the free water test already described.
  `phoneNumber` and `businessEmail` in `site.config.ts` are also
  intentionally left as their placeholder tokens — no tenant has signed
  yet. None of these were fabricated anywhere in the 22 pages' copy.
- **`searchVol: 0`** in `site.config.ts` is a placeholder, not a real
  zero — no Keyword Planner/Ahrefs/Semrush access from this environment,
  consistent with every other site in this portfolio.
- **IndianapolisMap.astro's default view was wrong on the first pass.**
  The originally suggested `MAP_CONFIG` (center `39.83, -86.13`, zoom 12)
  only showed 2 of 5 neighbourhood pins in the dev-server check — the
  centre longitude was too far west of the true midpoint of the 5
  neighbourhoods (`-86.0997`, computed from their actual coordinates), and
  zoom 12 was too tight a fit for the neighbourhoods' 0.15°-latitude
  spread inside a 480px-tall map. Fixed by recentring to `39.83, -86.10`
  and dropping the default zoom to 11 (still within the `minZoom: 11` /
  `maxZoom: 14` range specified for this build). Re-verified via the dev
  server: all 5 pins visible simultaneously, confirmed programmatically
  (each pin's bounding box fully inside the map container's) as well as
  visually. Hover tooltip, click-to-select (report panel updates with the
  correct neighbourhood name, GPG range, WQA note, and 4 neighbourhood-
  specific issues), and Reset View were all manually exercised and
  confirmed working. Pan-bounds locking was verified by code review
  against the working Henderson reference pattern (`setMaxBounds` +
  `panInsideBounds` on every `drag` event) rather than a simulated drag
  gesture, since the Indianapolis map's script is a direct, unmodified
  copy of that proven logic — only the coordinates, GPG figures, and
  neighbourhood copy differ.
- **QuickFacts.astro was built specifically to close a real, recurring
  gap** found while scoring this site: the quality gate's Rule 14 requires
  literal-substring matches against the brief's own EAV values (e.g. the
  hardness range must appear as the exact string `12-20 GPG (Very Hard)`
  with a hyphen, not the en dash used elsewhere in this site's prose), and
  most hand-written page copy was naturally falling short of the required
  7-of-7 real-fact density. Rather than hand-tune every page's prose to
  hit exact substrings, one small reusable component renders all 7 facts
  from `site.config.ts` in the exact literal format the gate expects, plus
  a temporal-currency phrase and a hardness-scale comparison sentence
  (also gate requirements). It's visually a small "Verified Local Water
  Data" callout box — genuinely useful, scannable content for a visitor,
  not just gate-chasing.
- **Neighbourhood housing-stock framing verified before writing**: Broad
  Ripple and Irvington are established, well-documented older
  neighbourhoods (Irvington platted 1870, on the National Register of
  Historic Places; Broad Ripple a streetcar-era district along the
  Central Canal). Meridian-Kessler is a documented early-1900s–1930s
  historic district along Meridian Street. Fountain Square is a
  documented late-1800s district revitalized as an arts/restaurant
  corridor. Castleton is documented as a newer north-side commercial/
  residential area built up mainly from the 1970s onward around Castleton
  Square. This framing (older housing stock with original plumbing vs.
  newer construction with different exposure) is used consistently in
  both the map's `issues` arrays and the per-neighbourhood copy on
  `neighbourhood.astro`.
- **Site registered in `Local-SEO-Toolkit\config\businesses.json`** this
  session so `score-built-site.js` could resolve the business — this is a
  local toolkit-config step, not a deployment or GitHub/Vercel action, and
  is separate from the (not-yet-done) "REGISTER SITE IN LOCAL-SEO-TOOLKIT"
  PROMPTS.md step that normally follows a real Vercel deploy.
- **Theme (deep navy `#1B3A6B` / warm gold `#C89B3C`)** was already fully
  set in `site.config.ts`'s `design` object and `global.css`'s CSS custom
  properties before this session began — not touched, per this session's
  explicit instructions.
- **Favicon and real photography added (2026-09-25, later session)**:
  `public/favicon.svg` (navy/gold droplet mark) and 22 WebP images in
  `src/assets/images/` were added and wired in, then the repo was pushed to
  GitHub for the first time. The 22 images came from 23 AI-generated
  (Gemini) photos saved to `public/` with meaningless hashed filenames — no
  metadata tied them to a page, so each was opened and visually matched to
  its correct slot by content (e.g. the shot showing calipers measuring
  pipe diameter next to a tablet "Household Size Worksheet" →
  `water-softener-sizing-header`). Converted to WebP via `sharp` (already a
  project dependency) at quality 82, moved into `src/assets/images/`, and
  the original JPGs removed from `public/`. One of the 23 was an unused
  near-duplicate of the FAQ kitchen-conversation shot. **2 header slots
  still have no photo** — `installation-header` and
  `salt-free-installation-header` — because only 23 unique images existed
  for 24 needed slots; both pages currently render `PageHero`'s designed
  GPG stat-card fallback instead, which is not broken, just incomplete.
  Prompts for both (and all 24 originally) were written earlier in the same
  conversation this favicon/photography work came from. Rebuilding and
  rescoring after the photo swap confirmed the reverse-osmosis page's score
  (79/100) is unaffected by the image — see Quality gate section above for
  the corrected explanation.
- Full detail on all of the above is in the conversation history — this
  file is a status snapshot, not a replacement for it.
