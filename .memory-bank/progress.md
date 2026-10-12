# Progress log — VigDecoded

**Append-only, newest entry first.** Add a new entry after every task — never edit,
reorder or delete an existing one. If an older entry turns out to be wrong, add a new
correction entry and reference the old one.

Entry format is defined in `../AGENTS.md` §5.

---

## 2026-10-12 — Design references recorded (UI standard)

- **Task:** Create `.memory-bank/design-references.md` listing five inspiration sites
  (FotMob, Flashscore, Linear, Vercel, Raycast) with clear instructions that before any UI
  work the agent must study them and match their polish, spacing and hierarchy, avoiding the
  typical AI-website look.
- **Did:** Wrote the file: the mandatory pre-UI rule (§0), per-site role table (§1), verified
  per-site takeaways with what to take *and* never take (§2), a mapping onto our components
  (§3), a concrete craft floor — spacing ladder, type scale, tabular numerals, alignment,
  states (§4), the banned generic-AI pattern list with named offenders (§5), the study
  procedure producing a 3-line design note (§6), and a UI review checklist (§7). Also wired
  it in: `AGENTS.md` §0 (new mandatory pre-UI read), §4 (UI conventions), §5 (file table),
  §7 (never-do); `system-architecture.md` §3 file tree + §8 conventions; `README.md`;
  `active-context.md`.
- **Result:** Grounded in the live sites, not recalled: fetched fotmob.com, flashscore.com,
  linear.app, vercel.com, raycast.com on 2026-10-12 and recorded real traits (FotMob league
  group headers + count badges, `FT`/`+1 day` muted micro-labels, and the honest empty state
  "No matches today / 4 matches start after midnight"; Flashscore `ENGLAND:`-style block
  labels, right-aligned numerics, `--` for missing values, plus its ad/gambling clutter as an
  anti-reference; Linear count-badged group headers and `·`-separated muted metadata; Vercel
  dark surface layering and one hero glow; Raycast label-pair typography). Flashscore visual
  reference: image search failed twice, so its notes come from fetched markup only —
  **needs a visual check** on the next UI task. No assets/screenshots copied into the repo;
  downloaded search images deleted, nothing binary committed.
- **Follow-ups:** First real UI task must run the §6 study procedure and write the design
  note before any markup/CSS. Flashscore needs a visual (not markup-only) look. Re-check
  reference sites when studying — they redesign.

## 2026-10-12 — Memory bank created

- **Task:** Create persistent memory so future sessions don't mix up project context:
  `AGENTS.md` + `.memory-bank/{product-context,active-context,system-architecture,progress}.md`.
- **Did:** Wrote all five files from scratch (repo previously held only a 16-byte
  `README.md`). Recorded: the read-before / write-after protocol, the integrity rules
  (immutable published picks, win/loss/void outcomes, no hidden losses), the frozen CSS
  token contract (`--bg`, `--card`, `--line`, `--ink`, `--mut`, `--gold`, `--green`,
  `--red`), the page structure, the data concepts/invariants, and the append-only log
  convention (newest first).
- **Result:** Files written to disk; contents reviewed for cross-file consistency
  (token names identical in `AGENTS.md` and `system-architecture.md`; no duplicated token
  values anywhere). No site code exists in this checkout, so nothing was run or rendered —
  the architecture sections for stack and file layout are explicitly marked unverified.
- **Follow-ups:** Open questions in `active-context.md` need user answers — card-day
  timezone, void/win-rate handling, real stack, where card & ledger data live, publish
  cutoff, and where the site source actually is.

## Backfilled — site features added before the memory bank existed

_Date not recorded: these were described by the user as recently added, before this
progress log existed. Dates must not be invented; correct with a dated entry if known.
Kept for continuity so future sessions don't re-add what already exists._

### "Today at a glance" summary card

- **Did:** Added a summary card at the top of the page showing the day's overview.
- **Rules set:** It is a **derived** view of the day's card/ledger data — never the only
  place a fact lives, and never maintained by hand alongside the detail sections.
- **Result / follow-ups:** Needs verification against `../AGENTS.md` §4 on the next UI task
  (which fields it shows, and that it stays in sync with the ledger).

### Collapsible sections

- **Did:** Wrapped long content (ledger/history/reasoning and similar) in collapsible
  sections.
- **Rules set:** Collapsed state keeps the title plus any count or pass/fail badge
  visible; expansion is presentational only and must never change what is published.
- **Result / follow-ups:** Confirm the implementation (`<details>/<summary>` vs JS toggle
  with `aria-expanded`) and record it in `system-architecture.md` §3/§9.
