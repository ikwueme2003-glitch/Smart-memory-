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

## Monetisation, funding and the honesty constraint

_Recorded 2026-10-12. Strategy, not yet committed revenue — treat as the agreed direction._

**Position: this is not a venture-fundable product.** Sports-prediction content is a media /
affiliate business, not a venture-scale one, and the category suffers adverse selection (it
is full of scammers, so serious investors assume the same of any entrant). The equity door is
effectively closed; the money that *is* offered in this space is usually bookmaker or
affiliate money with strings attached. **Do not spend time fundraising.** While broke, the
cost of fundraising is the daily publishing habit, which is the only real asset.

**The real gap is distribution and track record, not capital.** The website is cheap or free;
a record of 100+ honestly settled daily cards is not purchasable. Sequence:

1. **Freeze burn to ~zero.** Static site, free hosting, one paid domain. No app, no agency, no
   paid course, no "funding agent".
2. **Build the un-copyable asset: the record.** Publish daily without gaps, settle publicly,
   keep it screenshot-able and verifiable.
3. **Borrow distribution, don't build it.** Publish the card and the settlement where the
   football audience already is (X, short-form video, and WhatsApp/Telegram channels — the
   dominant channels for this audience in Ghana/Nigeria). One platform done daily beats five
   done sporadically. **The losses are the marketing** — competitors cannot publish losses
   without breaking their own model.
4. **Monetise in ascending order of corruption risk:**
   - **Small local brand sponsorship of the card** — best first money; needs only a modest
     audience, carries no incentive inversion and no gambling-regulation exposure.
   - **Paid depth, never paid picks** — the daily card and the ledger stay free and public
     forever. Sell deeper analysis/archive access at most.
   - **Betting affiliate revenue — last, and only under written rules.** See the trap below.
   - **Display ads — skip.** Low African CPMs, and they wreck the dense dark design.

### The affiliate trap (know this before signing anything)

- **Revenue share pays you when the people you referred LOSE.** RevShare is a share of the
  operator's net gaming revenue from that player, so your accuracy *reduces* your income.
  With **negative carryover**, a bad month for the house (i.e. a good month for your picks)
  carries forward as a debt against future earnings. Your best performance can put your
  affiliate account in the red.
- **CPA avoids the accuracy conflict but not the hype conflict** — you are paid per new
  depositing user, which rewards pushing deposit volume.
- **Realistic programme terms** (checked 2026-10-12, verify before applying): 1xBet Partners —
  RevShare 15–40%, $30 minimum, weekly, and you must bring ~4 new users per period to keep
  the account active; Betway Partners — 25–40% RevShare, €100 minimum, monthly, "relevant
  betting/sports website" required, negative carryover applies; SportyBet — up to ~35%
  RevShare, ~$50 minimum, monthly, M-Pesa/bank. African-market approvals favour existing
  traffic, which we do not yet have — another reason to wait.

### Ghana compliance facts (checked 2026-10-12)

Gaming Commission of Ghana, Advertising Guidelines under s.3(2)(g) of the Gaming Act 2006
(Act 721):

- **An affiliate's advertising falls within the Commission's purview** — legally the licensed
  operator is responsible for an affiliate acting as its agent, so material may need to be
  vetted/approved and operators will police affiliates. Do not improvise affiliate creative.
- Advertisements **must not create the impression of assured wins**, must carry *"Gamble
  responsibly"*, *"only 18 years +"*, *"Gambling is addictive"* (with the regulator
  acknowledged), and **must not use celebrities**.
- Enforcement is live — operators have had ads banned over youth appeal even with 18+ marks present.

**The alignment worth noticing:** the regulator's rules and this product's promise are the
same rule — no assured wins, publish the record, warn properly, no celebrity hype. The
typical "🔥 sure odds" tipster is the one out of compliance. **Honesty is compliance-native
here, not just marketing.**

### Hard commercial constraints

1. Commercial relationships never touch picks — no sponsor, affiliate, advertiser or investor
   influences selection, confidence, stake or timing.
2. The daily card and the ledger stay free and public. No paywall on the record, ever.
3. No betting-related commercial content without the required warnings, 18+ gating, and the
   operator's compliance approval where applicable.
4. Every commercial relationship is disclosed on the site.
5. If a deal's terms cannot be disclosed, the deal is declined.

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
- **Distribution channels** — which one gets the daily card post (X / TikTok / WhatsApp
  Channel / Telegram)? Undecided. Pick one and commit before monetising.
- **First revenue** — local brand sponsorship vs paid depth vs affiliate. Not yet chosen;
  sequencing and constraints are recorded above.
- **Operating reality** — does the founder have income that does not consume the daily
  publishing slot? Unresolved, and the single biggest risk to consistency.
