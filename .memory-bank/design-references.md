# Design references — VigDecoded

**Design inspiration for the site. Mandatory reading before any UI work.**

_Last reviewed: 2026-10-12._

> Goal: VigDecoded should read as a **crafted, opinionated product** — a serious sports
> data tool — not as a generic AI-generated landing page. The five sites below are the
> standard to match on **polish, spacing and hierarchy**. They are not templates to copy.

---

## 0. The rule

**Before starting ANY UI work** — layout, new component, spacing, colour use, type scale,
iconography, motion, or even restyling existing copy — you must:

1. **Study the five reference sites** (procedure in §6). Not "recall vaguely" — actually
   look at the current live pages, because these products redesign.
2. **Name the specific things you are taking from them** — which hierarchy decision,
   which spacing behaviour, which density choice — in the design note (§6).
3. **Then build**, keeping the token contract in `../AGENTS.md` §3 intact.
4. **Avoid every pattern in §5.** If a screenshot of the result could be mistaken for a
   generic AI landing page, the work is not finished.

If a reference site is unreachable, use the recorded traits in §2 — but **say so** in the
progress entry. Never invent what a site looks like.

**Hard boundary:** take *principles and craft*, never *assets* — no logos, crests,
photography, icons, illustration, wordmarks or copy lifted from these sites, and no
reproducing their layouts so exactly that it reads as a clone. Trade dress stays theirs.

**Aesthetics never outrank integrity.** `../AGENTS.md` §2 wins every conflict. A polished
loss is still a *visible* loss — never style a losing record into something softer to look
tidier, and never let a nicer layout drop a `void` or hide a red day.

---

## 1. The five references and their role

| Site | Role for VigDecoded | What we take | What we never take |
| --- | --- | --- | --- |
| [fotmob.com](https://www.fotmob.com) | **Primary data-UI reference.** Football data, dark mode, dense but calm | Match/league row anatomy, count badges, muted micro-labels for status, honest empty states | Leaf-green brand identity, crest imagery, their app chrome |
| [flashscore.com](https://www.flashscore.com) | **Density reference** — how far to push information per pixel | Ultra-compact rows, right-aligned numerics, league separators, date stamp treatment | Ad clutter, gambling-disclaimer walls, banner patterns — our **anti-reference** for clutter |
| [linear.app](https://linear.app) | **Hierarchy & restraint reference** | Muted metadata with `·` separators, small count badges on groups, quiet type scale, confidence in whitespace | Their product screenshots, indigo/violet palette |
| [vercel.com](https://vercel.com) | **Surface & depth reference** | Dark surface layering, soft radial glow used *once*, proof-by-number, tight feature lists | Geist wordmark look, black-and-white minimalism pushed to sterility |
| [raycast.com](https://www.raycast.com) | **Typography & voice reference** | Bold short declarative labels + one short clause, section headings that state a fact, key-cap/precision motifs | Their keyboard illustrations, mac-native iconography |

## 2. What to take from each (verified observations)

Observed on the live sites, 2026-10-12. Re-check when you study (§6).

### FotMob — primary data UI
- **League group header row:** small crest + bold league name, with a **count badge** for
  how many matches are in that group. Group membership and size are readable at a glance.
- **Row anatomy:** team name → crest → status → score. Status is a **muted, uppercase,
  small** label (`FT`) that sits *between* the teams rather than competing with them.
- **Time/status formats:** `FT`, `3:45AM`, `+1 day` (relative qualifier for the next day).
  Compact, unambiguous, no verbose phrasing.
- **Tabs switch the ordering** of one list (`Live | On TV | By time`) — one surface, several
  lenses, instead of several separate widgets.
- **Collapsible groups:** a `Hide all` control collapses league sections — the same idea as
  our collapsible sections, at group level.
- **Honest empty state:** a group with nothing today shows *"No matches today"* plus a
  forward pointer *"4 matches start after midnight"*. **This is the tone to match for
  "no card today":** state the nothing, then point at what's next. No padding, no filler.

### Flashscore — density, and what NOT to do
- **League block:** tiny uppercase country/muted label (`ENGLAND:`) + league name, then a
  thin separator rule before the rows. Cheap, effective grouping with almost no pixels.
- **Rows are stripped to the bone:** team name, crest, score. Scores appear as adjacent
  digits with no separator — maximum density, minimum ornament.
- **Numeric columns are consistent and right-aligned**, so scanning vertically works.
- **Date stamp** is compact and day-first with a weekday: `12/10 Mo`.
- **Status vocabulary:** `Finished`, `FRO` (frozen), a plain kickoff time `18:00`, and `--`
  where a value is genuinely missing — **an empty slot is shown as empty, not faked.**
  That matches our no-invented-data rule.
- **Anti-reference:** the page is buried in ad slots, repeated gambling-disclaimer bands
  and cookie/interstitial noise. It is the most information-dense *and* the least trusted-
  feeling of the five. Learn the density; **never** the clutter.

### Linear — hierarchy and restraint
- **Group headers carry counts** (`Backlog 8`, `Todo 71`, `Done 53`) — the collapsed/summary
  view still tells you the size of what's inside.
- **Metadata is muted and separated by `·`** (`Karri · 2min ago`, `Linear App 1.6881… ⋅ Jun 25`).
  Secondary info never competes with primary info.
- **Small caps / figure-label motifs** (`Fig 0.1`, `Fig 0.2`) give a precise, engineered
  feel without decoration.
- **Quiet type scale:** large section headings against very small labels, with a big gap
  between the two — hierarchy comes from *contrast in scale*, not from colour or weight spam.
- **Restraint:** no gradient text, no glassmorphism, no floating 3D blobs. Flat surfaces,
  thin lines, generous whitespace.

### Vercel — surfaces and proof
- **Dark surface layering:** near-black page, panels a step lighter, 1px hairline borders.
- **A single soft radial glow** behind the hero — depth used *once*, as a focus device, not
  repeated on every card.
- **Proof-by-number:** a short sentence carrying one concrete metric ("...millions of agent
  conversations daily"), rather than adjectives. Ours is the ledger: real counts, real
  record.
- **Tight feature lists** in a bordered column (5 items, no icons, no paragraphs) — a list
  can be a list.
- **Monospace for machine text** (code, commands, CLI output). We have an analogue: odds,
  kickoff times, dates and record figures are machine data and should be set in a way that
  reads as data (see §4, tabular numerals).

### Raycast — typography and voice
- **Headline that says something:** "Your shortcut to everything." One line, no hype.
- **Punchy label pairs:** `Fast. Think in milliseconds.` / `Ergonomic. Keyboard First.` /
  `Reliable. 99.8% crash-free rate.` — a bold qualifier then one concrete clause. This is
  the *exact* register for our confidence labels and section headings.
- **Section headings state a fact** ("There's an extension for that.") rather than labels
  ("Features").
- **Precision motifs** (keycaps, exact percentages) signal engineering rigour, not marketing.
- **Primary + secondary action pairing** ("Download for Mac" with a quiet "Install via
  Homebrew" beside it): one clear action, alternatives visibly secondary.

## 3. Mapping onto VigDecoded's components

| Our component | Reference behaviour to apply |
| --- | --- |
| **"Today at a glance"** | Raycast label pairs + Vercel proof-by-number: date as the anchor, the headline state as a bold clause, the count as a tabular figure. A single soft glow *at most*, and only if the hero area needs it. Not a card with an emoji. |
| **Pick rows** | FotMob row anatomy: fixture → competition → muted uppercase status micro-label → selection. Numbers tabular and aligned. The reasoning text is muted and secondary to the selection. |
| **Collapsible sections** | Linear/FotMob group headers: title + **count or pass/fail badge visible while collapsed**, muted micro-label for context, `--line` separator. Native `<details>` is fine if the summary row is styled properly. |
| **Ledger table** | Flashscore density with Linear restraint: thin `--line` row rules, right-aligned numerics, no zebra shading, no drop shadows. Win/loss shown with label + token colour, never colour alone. |
| **Archive / history** | Flashscore date stamping (`12/10 Mo` style compactness) with FotMob's honest empty states. |
| **Empty / no-card state** | FotMob's `"No matches today"` + `"N matches start after midnight"`: state it plainly, point to the next thing, no filler copy and no fake card. |
| **Headings and labels** | Raycast: state a fact or a qualifier, keep it short. Linear: muted `·`-separated metadata beneath. |

## 4. Craft floor (non-negotiable specifics)

"Polish" is not a vibe — it is these decisions, applied consistently.

- **Spacing:** one scale, used everywhere (a 4/8px based ladder: 4, 8, 12, 16, 24, 32, 48, 64).
  No arbitrary values like `padding: 13px`. Vertical rhythm between sections must be
  *deliberately larger* than spacing inside a card.
- **Type scale:** a small, fixed set (e.g. 12 / 13 / 14 / 16 / 20 / 28 / 40). Hierarchy comes
  from size + `--ink` vs `--mut` contrast, not from six font weights.
- **Numerals:** `font-variant-numeric: tabular-nums` (or a mono face) for every figure —
  times, dates, odds, counts, records, scores. Numbers must align in columns.
- **Alignment:** numeric columns right-aligned; labels left-aligned; never centred body copy
  in a data table.
- **Separation:** prefer 1px `--line` hairlines and whitespace over shadows. If a shadow is
  needed as elevation, keep it subtle and consistent.
- **One accent:** `--gold` is the only accent. It marks the active/important thing. If gold
  is on three elements in one viewport, remove two.
- **Interactivity:** every interactive element has rest / hover / focus-visible / active
  states. `focus-visible` uses a visible `--gold` ring — never `outline: none` alone.
- **Micro-labels:** uppercase + letter-spaced + `--mut` for status/context labels
  (`FT`-style). Never let a micro-label carry information that exists nowhere else.
- **Motion:** 120–200ms, ease-out, and only to explain a change (expand, settle, appear).
  Respect `prefers-reduced-motion`.
- **States:** design empty, loading, single-item, and long-list states — not just the happy
  path with fake content. Missing values render as an explicit `—`, never invented.
- **Responsive:** the densest reference layouts still work at 360px. Check narrow before
  wide; collapse columns rather than shrinking type below 12px.

## 5. The "generic AI website" look — banned

If the page shows any of these, it is off-brand and must be fixed:

- **Purple/indigo/blue gradients**, gradient text, "aurora" mesh backgrounds, glowing orbs.
- **Emoji as iconography** (⚽🔥📊✅) or emoji-laden card titles.
- **Three identical feature cards** with a coloured rounded-square icon, a short title and
  two lines of filler.
- **Everything centred**, one narrow column, uniform 24px gaps, no visual rhythm.
- **`border-radius: 16px+` on everything**, especially stacked with thick soft shadows
  ("floating" cards) and glassmorphism blur.
- **Glassmorphism / backdrop blur** as a default surface treatment.
- **Hero filler:** a pill badge ("✨ Introducing…"), a gigantic headline, a floating mockup,
  and a `Get started` + `Learn more` button pair.
- **Corporate filler copy:** "Unlock the power of…", "Seamlessly…", "Empower your…",
  "Supercharge…", "Your all-in-one solution for…". Say the actual thing instead.
- **Icon-in-a-circle stat rows** ("10K+ Users | 99% Accuracy | 24/7") — invented-looking
  metrics with no source. We publish a *real* ledger, so any figure must be real or absent.
- **Decorative animation loops** (pulsing, floating, auto-rotating) and scroll-jacking.
- **Stock illustrations** of people at laptops / abstract 3D shapes.
- **Section headings that are just nouns in title case** ("Features", "Why Choose Us").
- **Uniformity without hierarchy:** every block the same size, every text the same weight,
  nothing clearly more important than anything else.
- **Padding-heavy emptiness:** a page that needs three scrolls to convey one card's picks.

When in doubt: **denser, quieter, more aligned.** FotMob and Linear are the tie-breakers.

## 6. How to study the references (procedure)

Do this at the start of any UI task; it takes a few minutes and changes the output.

1. **Open the live pages** — fetch/render fotmob.com, flashscore.com, linear.app, vercel.com,
   raycast.com. Note: some of these are large JS apps, so the fetched markup may be partial.
   Get what you can: real DOM structure, CSS values, inline styles, class names.
   If you can render/screenshot them, do — visual inspection beats markup.
2. **Extract, don't admire.** For each site write down:
   - the **spacing values** actually used between and inside blocks;
   - the **type scale** (sizes, weights, and which are muted);
   - **how a row/group is structured** and what the collapsed/summary state shows;
   - **what is deliberately NOT there** (no icons, no shadows, no borders) — restraint is
     the hardest part to copy and the most important;
   - one **specific** thing you will reuse, named in a sentence.
3. **Write a 3-line design note** before coding, in this shape:
   ```
   Design note — <task>
   Studying: <sites looked at, and roughly what they showed>
   Taking: <2–3 named decisions, e.g. "muted uppercase status labels on pick rows (FotMob);
            count badge visible on collapsed ledger header (Linear/FotMob)">
   Avoiding: <the generic-AI patterns most at risk in this task>
   ```
   Put the note in your working message, and a one-line version in the `progress.md` entry.
4. **Build, then self-review** against §4 and §5 before reporting done. A quick way to test:
   *would this look at home inside FotMob, Linear or Raycast — or on a generic AI landing
   page?* If the latter, keep working.

## 7. Review checklist for every UI diff

- [ ] Design note written *before* the change (§6).
- [ ] All colour via tokens; no raw hex/rgb/hsl outside the `:root` block.
- [ ] Spacing from the one ladder; type from the one scale.
- [ ] Figures tabular and aligned; missing values render `—`, never invented.
- [ ] Win/loss carried by label + colour, never colour alone.
- [ ] Collapsed state still shows its title and count/badge; nothing reachable only by expanding.
- [ ] Focus-visible states present; contrast holds in dark surfaces.
- [ ] Empty and no-card states written honestly (FotMob tone), not filled with filler.
- [ ] Zero patterns from §5 present.
- [ ] Verified in a browser at ~360px and desktop width, or explicitly reported as unverified.
