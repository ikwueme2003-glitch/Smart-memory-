# System architecture — VigDecoded

_Last reviewed: 2026-10-12 (memory bank created)._

> ⚠️ **Repo state at time of writing:** this checkout contains only `README.md`, `AGENTS.md`
> and `.memory-bank/`. The site code lives outside this snapshot so far. The "Stack" and
> "File layout" sections below are therefore partially **unverified** — every unverified
> item is marked and must be corrected on the first task that touches real code.
> Do not treat guesses here as facts; fix the file instead.

---

## 1. Product shape (verified — from the product description)

- A dark-themed website serving football predictions.
- One **card** per **card day**.
- A **public ledger** of settled picks.
- Top-of-page **"Today at a glance"** summary card.
- Long content in **collapsible sections**.

## 2. Stack

| Layer | Status | Notes |
| --- | --- | --- |
| Markup / rendering | **Unverified** | Record the real answer here on first code task |
| Styling | **Partially verified** | Dark theme, plain CSS custom properties (`:root` token block) |
| Client JS | **Unverified** | Collapsible sections imply some interactivity (`<details>` or JS toggle) |
| Data source for fixtures/results | **Unverified** | If an API is used, its key belongs in env vars, never the repo |
| Hosting / build | **Unverified** | |

## 3. File layout

```
/                      ← repo root
├── README.md
├── AGENTS.md                       ← agent contract, read every task
└── .memory-bank/
    ├── product-context.md          ← what VigDecoded is
    ├── active-context.md           ← current state (read every task)
    ├── system-architecture.md      ← this file
    ├── design-references.md        ← UI standard: 5 reference sites, craft floor, banned patterns
    └── progress.md                 ← append-only dated log
```

**To fill in on the next code task:** exact stylesheet path, exact JS path, page/component
files, and where card data + ledger data are stored.

## 4. Design tokens (frozen contract)

Single `:root` block holds the values; components reference the names only.

| Token | Role |
| --- | --- |
| `--bg` | page background — darkest surface |
| `--card` | card / panel surface, raised above `--bg` |
| `--line` | borders, dividers, table rules, section separators |
| `--ink` | primary text |
| `--mut` | muted text — metadata, labels, secondary copy |
| `--gold` | accent — highlight, active state, brand emphasis |
| `--ink` on `--gold` must stay legible | |
| `--green` | positive — win, settled-good |
| `--red` | negative — loss, settled-bad, error |

Conventions:

- Token **values** live in exactly one place (the `:root` block); names/roles live in
  `AGENTS.md` §3 so they cannot drift.
- No raw hex/rgb/hsl in component rules.
- Colour is never the sole signal for win/loss — pair it with text or a glyph.
- Any new token is added to the `:root` block, `AGENTS.md` §3 and the table above in the
  same task.

## 5. Page structure (target order)

1. Header / brand (VigDecoded)
2. **"Today at a glance"** — card date, pick count, headline state
3. **Today's card** — the picks, each with reasoning + confidence, frozen at publish time
4. **Ledger** — settled picks with outcomes and running totals
5. **History / archive** — previous days
6. **About / disclaimer**

Sections 3–6 are candidates for **collapsible sections**: collapsed state keeps the title
plus a count or pass/fail badge so the page is still scannable while closed.

## 6. Data concepts

Names below are conceptual; align them with real field/variable names on the first code task.

| Concept | Meaning | Key fields |
| --- | --- | --- |
| **CardDay** | The unit of publication — one card per day | `date`, canonical timezone, publish time |
| **Card** | The published set of picks for a day, immutable after publish | `day`, `picks[]`, published-at, notes |
| **Pick** | One prediction | fixture/teams, competition, kickoff, market, selection, reasoning, confidence, `status` |
| **Outcome** | Settlement of a Pick | `win` \| `loss` \| `void`, settled-at |
| **LedgerEntry** | The public record row for a settled Pick | `pick`, `outcome`, running totals |
| **Summary ("at a glance")** | Derived view of the day | date, pick count, settled/played count, headline |

**Invariants**

1. `Card` for a past day is never mutated — corrections append.
2. `Pick.outcome` is `win`, `loss` or `void`; never null once the day is closed.
3. A `void` is neither a win nor a loss and must be excluded from (or explicitly handled in)
   win-rate maths — decide once, apply consistently.
4. "At a glance" values are **derived** from the same Card/Pick/Ledger data as the detail
   sections, never maintained separately.
5. Ledger totals include every settled pick; nothing is filtered out of the record.
6. Card-day membership is decided by one canonical timezone (currently UTC until recorded
   otherwise).

## 7. Data flow (conceptual)

```
fixtures ──▶ today's card (published, frozen) ──▶ picks rendered in Today's card section
                                     │
results ──▶ settlement (win/loss/void) ──▶ ledger entry ──▶ running totals
                                     │
                                     └──▶ "Today at a glance" summary (derived)
```

No step may write to a published card; settlement only ever adds outcome data.

## 8. Conventions

- **UI work follows `design-references.md`** — that file holds the visual standard (the five
  reference sites, the craft floor: spacing ladder, type scale, tabular numerals, states),
  plus the list of banned generic-AI patterns. Study it before any layout/component change.
- Keep styling token-driven; layout changes that alter the page order update §5.
- Collapsible sections: if using native `<details>/<summary>`, style `summary` with
  `--ink`/`--mut` and the marker with `--gold`; if JS-driven, keep the toggle a button with
  `aria-expanded`.
- Accessibility: visible focus (`--gold` outline is the natural choice), reduced-motion
  respect, no colour-only meaning.
- Secrets (fixture/results API keys) via environment variables only.

## 9. Unknowns to confirm on the next code task

- [ ] Rendering approach and framework (or plain static HTML)
- [ ] Stylesheet path + exact `:root` token values
- [ ] Collapsible implementation (`<details>` vs JS) and its markup pattern
- [ ] Where card and ledger data actually live (file, database, CMS, API)
- [ ] How results are fetched and how settlement is performed (manual vs automated)
- [ ] Canonical card-day timezone + publish cutoff
- [ ] Hosting/deploy target and how a change goes live
- [ ] Whether odds are stored, and in what format
