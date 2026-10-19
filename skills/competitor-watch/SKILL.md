---
name: competitor-watch
description: Report what actually changed across a set of competitors since last time, instead of describing them again. Use for a weekly or monthly check-in on apps someone already knows.
---

Use the Peekly MCP at `https://peekly.app/api/v1/mcp`. Read `tools/list` before using
the examples: respect its current parameter schema and cost. Keep calls bounded, read `_credits`, and stop on an access or quota refusal.

# Reporting the change, not the state

A competitor report that describes an app is useless the second time you read it: nothing
in it has moved. What is worth reading is **what changed**, and what that change probably
means.

So this skill produces a changelog, not a profile. If nothing moved, say that in one line
and stop. A short honest report beats a long one padded with last week's facts.

## Work in this order

**1. Movement in the charts.**

```
get_app_rankings(app_id: "<id>", country: "us", chart: "grossing", days: 30)
```

Always pass a country and a chart. Without them you get every country and category at once,
which is expensive and unreadable.

Look for the break in the line, not the level. An app steady at #40 tells you nothing new.
An app that went from #180 to #45 in nine days did something, and the rest of this report
is about finding out what.

**2. New ads, and dead ones.**

```
get_app_ads(app_id: "<id>")
```

Sort by how long each creative has been live. Anything under two weeks is new: that is
their current test. A creative that ran for months and is now inactive is a control they
gave up on, which is just as informative.

A jump in the number of active creatives usually means a budget increase, and it often
lands a few days before a chart move.

**3. A changed paywall.**

```
get_app_paywalls(app_id: "<id>")
```

Compare the most recent capture with the one before. A new price, a new trial length, a
reordered plan list. These are the changes with the most direct effect on revenue, and the
ones a competitor never announces.

**4. Line the dates up.**

This is the whole point of the exercise. New creatives on the 3rd, a paywall change on the
5th, a chart climb starting on the 8th is a story. The same three events scattered across
two months are noise.

## What to report

One block per app, and only for apps where something moved:

- What changed, with its date.
- What it probably means, in one sentence, marked as a hypothesis.
- Whether it deserves a reaction from you, yes or no.

End with the single thing worth watching next week.

## Watch out

Correlation is not causation, and you will be tempted every time. A chart climb the week
after a new creative may be the creative, or a feature in the store, or a seasonal effect.
Say "probably", and say what would confirm it.

Coverage is Meta creatives. An app can also buy Apple Search Ads or influencer placements,
which will not show up here. Silence on the ads side is not proof of no spending.
