# Active context — VigDecoded

> Read this file in full **before** every task, and update it **after** every task
> (see `../AGENTS.md` §0). Keep it short and current — this is working state, not history.

## Current focus

Standing up the project's persistent memory. No site code has been written or reviewed in
this checkout yet.

## Repo state

- Branch in use: `arena/beaaebdc-smart-memory` (based on `main` @ `751fe40 Initial commit`).
- Tracked files: `README.md` (16 bytes), plus the memory bank just added:
  `AGENTS.md`, `.memory-bank/product-context.md`, `.memory-bank/active-context.md`,
  `.memory-bank/system-architecture.md`, `.memory-bank/progress.md`.
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

- Memory bank lives at `.memory-bank/` with the four files above; paths must not change.
- `progress.md` is append-only and **newest entry first**.
- Token names are frozen; values live only in the single `:root` block.
- Integrity rules in `../AGENTS.md` §2 outrank feature requests.

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

---

**Last updated:** 2026-10-12 — created the memory bank (`AGENTS.md` + four
`.memory-bank/` files) for VigDecoded; recorded the frozen token contract, the integrity
rules, and the open questions above.
