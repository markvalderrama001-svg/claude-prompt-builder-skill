# Example: one messy sentence in, one expert prompt out

**What the user typed**

> our month end close takes like 8 business days and I'm always chasing the same recons at the end. I want claude to help but I don't know where to start

---

## YOUR PAIN

- You hit business day 6 and you're still tying out the same three balance sheet accounts that broke last month, and the month before.
- You re-explain your chart of accounts, your entities and your close calendar to an AI from scratch every time, so the answers come back generic.
- You've probably tried a close checklist template. It listed 60 steps and none of them were the ones that actually slow you down.
- Leadership wants the numbers by day 5. Every late close costs you a little credibility and a lot of evenings.
- The recons that keep breaking are mostly mechanical matching. You're doing data entry with a CPA license.

## YOUR PROBLEM

Your close isn't slow because there are too many steps. It's slow because the same few reconciliations fail late, and nothing catches them early. What you need is a close diagnosis and a set of early tie-out gates that move those failures to day 1–2, with AI doing the matching and you doing the judgment.

## YOUR PROMPT

```
ROLE
You are a fractional controller and close-automation specialist who has taken multi-entity companies from 8+ day closes to 4-day closes, specializing in reconciliation design and controls-first AI automation. Your operating principle: automate the matching, never the judgment, and every automated step must leave an audit trail a reviewer can follow.

CONTEXT
I run month-end close at [COMPANY TYPE, e.g. "a 3-entity SaaS group"]. Close currently takes about 8 business days. The same reconciliations keep breaking late: [THE 2-4 ACCOUNTS THAT BREAK MOST, e.g. "intercompany, deferred revenue, AP accrual"]. Our ERP is [ERP, e.g. Sage Intacct / NetSuite / QuickBooks] and we also use [OTHER SYSTEMS, e.g. "Ramp, Stripe, Gusto"]. I'm comfortable with accounting but [YOUR TECHNICAL COMFORT, e.g. "I've never written code"]. What I've already tried: [e.g. "a close checklist in Asana"].

REQUEST
Build me a close-acceleration plan I can start using next month. Include:
1. Close diagnosis: a day-by-day map of my current close and where the critical path actually runs. Ask me for the calendar if you need it.
2. Root cause per breaking recon: for each account above, the most likely reason it breaks late (cutoff, missing data, timing of upstream feeds, manual matching) and the evidence that would confirm it.
3. Early-warning gates: for each, a tie-out I can run on day 1–2 (or continuously) with the exact formula, the source of each side, and the tolerance. Gates must fail loudly with the difference in dollars.
4. AI automation plan: which steps Claude can do (matching, variance explanations, draft entries) and which stay human (approvals, posting, estimates). Every AI-written entry is draft-only and needs human sign-off.
5. 30-day rollout: week by week, what to build or change first, ranked by days saved.
6. Scorecard: 5 numbers to track every close (days to close, recons failing after day 3, adjusting entries after day 3, hours per recon, exceptions caught early).

Rules:
- Use my accounts and systems in every example, not generic ones.
- Label every time-saving estimate as an estimate.
- If a fix needs IT or data work, say so and give me the one-sentence ask for that person.

Before proceeding, please ask me any clarifying questions to ensure the plan is tailored to my specific close.
```

## EXPECTED RESULT

A close plan built around your three problem accounts, with gates that surface breaks on day 2 instead of day 6. The target is 2–3 days out of the close within two cycles.

## WANT IT SHARPER?

1. **Main goal?** (a) I need to hit day 5 (b) I want fewer late adjustments (c) I want to prepare for an audit.
2. **What can you change?** (a) Only my own process (b) I can ask IT for data feeds (c) I can change systems.
3. Which accounts break most often?
4. Which ERP and supporting systems do you use?
