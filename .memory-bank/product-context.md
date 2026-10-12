# Product context — VigDecoded

**One-liner:** A daily football (soccer) predictions website that publishes **one honest
card per day** and keeps a **public ledger** of every win and loss.

_Last reviewed: 2026-10-12 (memory bank created)._

---

## The promise

VigDecoded is built on the opposite instinct to tipster hype:

1. **One card per day, not a wall of picks.** A single card, published on the day, with the
   reasoning and an honest confidence level. Nothing added after kickoff.
2. **The ledger is public.** Every published pick is settled in public and the running
   record — including losing days — is visible to anyone. Losses are never quietly dropped.
3. **Honest over exciting.** "No card today" and "this is a coin flip" are valid outputs.
   The product's credibility comes from the record matching reality.

## Who it is for

People who want a small number of considered football predictions plus an unfiltered
record of how those predictions actually did — and who are put off by sites that only
advertise the winners.

## Core features

| Feature | What it does | Notes |
| --- | --- | --- |
| **Today's card** | The single documented set of picks for the current card day | Frozen once published |
| **"Today at a glance"** | Summary card at the top of the page: card date, pick count, headline state | Recently added; a summary only, never the sole source of a fact |
| **Collapsible sections** | Long content (ledger, history, reasoning, about) wrapped in expandable sections | Recently added; collapsed state keeps title + count/badge visible |
| **Public ledger** | Append-only record of every pick and its settlement | Wins, losses and voids all shown; totals include everything |
| **Archive / history** | Past cards and past ledger rows | Read-only once a day is settled |

## Non-goals

- Not a tipster marketplace, subscription funnel or affiliate-driven "locks" page.
- No guaranteed-profit language, no proof-of-winnings marketing, no selective screenshots.
- No live in-play betting feed or account/wallet functionality.
- No engagement farming: no infinite pick lists to inflate page views.

## Rules the product must never break

1. A published pick is immutable; corrections are appended, never edited in place.
2. Every pick has an outcome: **win / loss / void** (void = postponed, abandoned or
   ungradeable — never counted as a win).
3. The ledger totals include all settled picks; a losing row is never deleted or hidden.
4. Settlement rules and card-day boundaries are written down, not applied by feel.
5. Predictions-only framing, disclaimer intact, no certainty claims.

(Enforcement details and the full integrity list: `../AGENTS.md` §2.)

## Open product questions

- **Card day timezone** — which timezone decides which kickoffs belong to "today"? Unset;
  currently using UTC. Must be decided and recorded in `system-architecture.md`.
- **Void handling in the record** — does a void break a win streak / count in the
  win-rate denominator? Rules must be explicit and applied consistently.
- **Card publishing deadline** — is there a fixed cutoff time before the first kickoff?
- **Multi-sport / multi-league scope** — which leagues are in scope, and is there a
  minimum pick count per day, or is "no card" allowed?
- **Odds/decimal format** — whether odds are stored at all, and in what format.
