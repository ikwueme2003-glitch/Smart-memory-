# Active context — VigDecoded

> Read this file in full **before** every task, and update it **after** every task
> (see `../AGENTS.md` §0). Keep it short and current — this is working state, not history.

## Current focus

Standing up the project's persistent memory. The design standard is now recorded
(`design-references.md`) — no site code has been written or reviewed in this checkout yet.

## Repo state

- Branch in use: `arena/beaaebdc-smart-memory` (based on `main` @ `751fe40 Initial commit`).
- Tracked files: `README.md` (16 bytes), plus the memory bank just added:
  `AGENTS.md`, `.memory-bank/product-context.md`, `.memory-bank/active-context.md`,
  `.memory-bank/system-architecture.md`, `.memory-bank/design-references.md`,
  `.memory-bank/progress.md`.
- **No site source code is present in this snapshot.** `system-architecture.md` §2–§3 is
  therefore marked unverified; correct it the first time real code is available.

## Known product facts (from the user, verified)

- Daily football predictions site named **VigDecoded**.
- **One honest card per day.**
- **Public ledger of wins and losses.**
- Dark theme via CSS variables: `--bg`, `--card`, `--line`, `--ink`, `--mut`, `--gold`,
  `--green`, `--red` (names frozen — see `../AGENTS.md` §3).
- Recently added: **"Today at a glance"** summary card and **collapsible sections**.

## Decisions locked

- Memory bank lives at `.memory-bank/` with the five files above; paths must not change.
- `progress.md` is append-only and **newest entry first**.
- Token names are frozen; values live only in the single `:root` block.
- Integrity rules in `../AGENTS.md` §2 outrank feature requests.
- **UI standard is set by `design-references.md`** (FotMob, Flashscore, Linear, Vercel,
  Raycast). Before any UI work: study those sites, write the 3-line design note, match their
  polish/spacing/hierarchy, avoid the banned generic-AI patterns. Craft principles only —
  never copy their assets, logos or trade dress.

## Open questions / blockers

1. **Card day timezone** — which kickoffs count as "today"? Unset; using UTC for now.
2. **Void handling** — do voids break streaks / enter the win-rate denominator?
3. **Stack unknown** — is the site plain static HTML/CSS/JS, or a framework app?
4. **Data storage** — where do cards, picks and ledger rows live?
5. **Publish cutoff** — is there a fixed time before the first kickoff when the card freezes?
6. Where does the site code actually live (this repo, or another one to be pushed here)?

Raise unresolved questions with the user; once answered, move the answer into
`product-context.md` / `system-architecture.md` and remove it from this list.

## Next steps

1. Get the site source into this repo (or a pointer to it), then fill in the unknowns in
   `system-architecture.md` §2, §3 and §9.
2. Confirm the card-day timezone and record it in `system-architecture.md` §6.
3. Confirm void/stake/odds rules and write them into `product-context.md`.
4. Verify "Today at a glance" and collapsible sections against the UI conventions in
   `../AGENTS.md` §4 (badge visible when collapsed; summary derived, not duplicated).
5. First UI task: run the design-references study procedure (§6 of that file) and write the
   design note before touching markup or CSS.

---

**Last updated:** 2026-10-12 — added `design-references.md` (five reference sites, per-site
takeaways, craft floor, banned generic-AI patterns, study procedure) and wired it into
`AGENTS.md` §0/§4/§5/§7 as mandatory pre-UI reading.
