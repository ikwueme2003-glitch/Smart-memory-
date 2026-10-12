# AGENTS.md — working agreement for this repository

> **Read this file first, at the start of every single task. No exceptions.**
> This repository keeps its persistent memory in `.memory-bank/`. The memory bank is the
> source of truth about this project — not your assumptions, not the training data, not
> what "similar projects usually do".

---

## 0. The two mandatory rules

### BEFORE every task

1. Read `AGENTS.md` (this file) — **full read**.
2. Read `.memory-bank/active-context.md` — **full read**.
3. Read the **last 3–5 entries** of `.memory-bank/progress.md` (entries are newest-first).
4. Read `.memory-bank/product-context.md` and `.memory-bank/system-architecture.md` too
   whenever the task touches product behaviour, UI, design tokens, picks, or the ledger.
5. **For ANY UI work — layout, component, spacing, colour, type, iconography, motion, or
   restyling — read `.memory-bank/design-references.md` and study the five reference sites
   (FotMob, Flashscore, Linear, Vercel, Raycast) before writing markup or CSS.** Match their
   polish, spacing and hierarchy; write the 3-line design note it requires; avoid every
   pattern in its banned list. VigDecoded must never look like a generic AI-generated site.
6. Before editing anything, state in 1–2 lines: what you learned, which files you will
   touch, and any conflict with the memory bank.
   **If the request contradicts the memory bank, stop and ask — do not silently pick a side.**

### AFTER every task

1. Update `.memory-bank/active-context.md` — **always**, even for a no-op or read-only task.
2. Append a new dated entry to `.memory-bank/progress.md` — **always**.
   Never edit, reorder, or delete an existing entry; corrections are new entries.
3. Update `.memory-bank/product-context.md` and/or `.memory-bank/system-architecture.md`
   if product rules, design tokens, data shape, or file layout changed.
4. Only then report back to the user.

A task is **not finished** — and you must not report success — until the AFTER steps are done.
If you ran out of budget, say so explicitly and write the memory update next turn.

---

## 1. What this project is

**VigDecoded** — a daily football predictions website.

Core promise:

- **One honest card per day.** A single documented set of picks per day. Publish the
  reasoning and the real confidence level; no hype, no padded "locks", no cards added
  after kickoff.
- **Public ledger of wins and losses.** Every published pick is recorded and settled in
  public, including the bad days. The running record is the product's credibility.
- **Dark theme, token-driven CSS** (see §3).
- Recently added: a **"Today at a glance"** summary card and **collapsible sections**.

Full product rules: `.memory-bank/product-context.md`.
Structure, tokens and data concepts: `.memory-bank/system-architecture.md`.

---

## 2. Hard rules (integrity — these outrank feature requests)

These exist because the product's only real asset is being trusted. If a request pushes
against one of these, raise it with the user before implementing.

1. **Never retro-edit a published pick.** Once a card for a day is public, its picks,
   reasoning and timestamp are frozen. Fix only via an appended correction/note.
2. **Never show a pick without its outcome.** Every pick ends up as win / loss / void
   (`void` = postponed/abandoned/insufficient data — **not** a win, not a loss).
3. **Never hide or delete losses.** The ledger totals include every settled pick.
4. **No silent changes to "the record".** Any change to totals, settlement rules or
   tie-breaks gets written down in `progress.md` the moment it is made.
5. **Dates are explicit and consistent.** Determine which kickoffs belong to which card
   day by the project's canonical "card day" timezone. It is recorded in
   `system-architecture.md`; if it is still unset, use UTC and flag it as an open question.
6. **No guarantees, no "guaranteed win", no implied profit certainty.** Predictions, not
   advice. Keep any existing disclaimer text intact.
7. **Stake/odds data is never invented.** Missing odds stay missing; do not back-fill
   plausible-looking numbers.

---

## 3. Design system contract

Dark theme, driven entirely by CSS custom properties. The token names are **frozen**:

| Token | Role |
| --- | --- |
| `--bg` | page background (darkest surface) |
| `--card` | card / panel surface (raised from `--bg`) |
| `--line` | borders, dividers, table rules, section separators |
| `--ink` | primary text |
| `--mut` | muted / secondary text, metadata, labels |
| `--gold` | accent: highlight, active state, brand emphasis |
| `--green` | positive state: win, settled-good, correctness |
| `--red` | negative state: loss, settled-bad, error |

Rules:

- Component CSS uses `var(--token)` only. **No raw hex/rgb/hsl outside the single token
  definition block.**
- Add a new token only when a genuinely new role appears, and record it here + in
  `system-architecture.md` in the same task.
- Token **values** live in one `:root` block (path recorded in
  `system-architecture.md` once known). Do not duplicate values here — this file lists
  names and roles, so it can never drift from the stylesheet.
- Never hardcode a colour that makes a light theme impossible; the palette stays
  swappable at the token block.
- Win/loss colour must never be the *only* signal — pair `--green`/`--red` with a label,
  glyph or text (readability + accessibility).

---

## 4. UI conventions

- **Study `.memory-bank/design-references.md` before any UI work** and match that standard
  of polish, spacing and hierarchy. Design note first, code second. Never ship the generic
  AI-website look it lists as banned.
- **"Today at a glance"** is the summary card at the top of the page: today's card date,
  number of picks, and the headline state. It summarises — it must never be the only
  place a fact exists; it reads from the same data as the detail sections.
- **Collapsible sections** are the default wrapper for long content. The collapsed state
  must still show its title and any pass/fail or count badge. Expansion state is
  presentational only — it must never change what data is published, and collapsed
  content must remain reachable (no `display:none`-only accessibility traps).
- Content order on the page: "Today at a glance" → today's card (picks) → ledger →
  history/archive → about/disclaimer.
- No layout/behaviour change without updating `system-architecture.md` if it changes the
  page structure.

---

## 5. Memory bank files

| File | Holds | Update when |
| --- | --- | --- |
| `.memory-bank/product-context.md` | What VigDecoded is, promise, features, non-goals, open product questions | product rules or scope change |
| `.memory-bank/active-context.md` | Current focus, repo state, recent decisions, blockers, next steps | **every task** |
| `.memory-bank/system-architecture.md` | Stack, file layout, tokens, data concepts/flows, conventions | structure, tokens, data shape change |
| `.memory-bank/design-references.md` | The five reference sites, what to take from each, the craft floor, banned generic-AI patterns, study procedure | **read before any UI work**; update when references or craft rules change |
| `.memory-bank/progress.md` | Append-only dated log of what was actually done | **every task** |

### Entry format — `progress.md` (newest first)

```
## YYYY-MM-DD — <short title>
- **Task:** what was asked
- **Did:** concrete changes (files, decisions)
- **Result:** verified how? (ran/saw/not verified)
- **Follow-ups:** anything left, or "none"
```

### `active-context.md` must always end with

`Last updated: YYYY-MM-DD — <one line on what changed>` and keep its
"Next steps" and "Open questions" sections current (delete resolved items, they live in
`progress.md` afterwards).

---

## 6. Definition of done

- [ ] Read `AGENTS.md`, `active-context.md`, last few `progress.md` entries **before** coding.
- [ ] Change matches the product promise, the integrity rules (§2) and the token contract (§3).
- [ ] Verified as far as possible (page renders / numbers reconcile / no console errors) —
      if you could not verify, say so plainly instead of claiming success.
- [ ] `active-context.md` updated.
- [ ] New `progress.md` entry appended.
- [ ] `product-context.md` / `system-architecture.md` updated if rules or structure moved.
- [ ] Report the outcome to the user, including anything unverified or left over.

---

## 7. Never do this

- Never start work without the BEFORE reads, and never end a turn without the AFTER writes.
- Never rewrite history in `progress.md` or in `.memory-bank/` to look tidier.
- Never do UI work without studying `.memory-bank/design-references.md` first, and never
  ship the banned generic-AI patterns (purple gradients, emoji iconography, glassmorphism,
  three-identical-feature-cards, centred filler, invented stat rows).
- Never copy logos, crests, images, icons or copy from the reference sites — take craft
  principles only, never assets or trade dress.
- Never invent data: no fabricated odds, results, fixtures, records or screenshots.
- Never delete a losing ledger row to "clean up".
- Never commit secrets, tokens or credentials (API keys for a results/fixtures feed live in
  environment variables, never in the repo).
- Do not reorganise or rename the memory bank files — external processes and earlier
  sessions depend on these exact paths.
