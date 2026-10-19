---
name: find-app-ideas
description: Find a proven app concept worth building, using Peekly's revenue estimates and chart movements. Use when someone asks what to build, which niche is growing, or whether an idea already makes money.
---

Use the Peekly MCP at `https://peekly.app/api/v1/mcp`. Read `tools/list` before using
the examples: respect its current parameter schema and cost. Keep calls bounded, read `_credits`, and stop on an access or quota refusal.

# Finding an app idea that already prints

The point is not to find an original idea. It is to find a concept **someone is
already being paid for**, then judge whether there is room for another player.

## Work in this order

**1. Size the niche before looking at any single app.**

```
search_apps(search: "<the niche>", sort: "revenue", limit: 15)
```

Read the spread, not the leader. Three apps above $200k a month and nothing under
means an entrenched market. A dozen apps between $20k and $80k means a niche where a
newcomer still lands. One app taking everything usually means a moat, a brand, or a
distribution deal you cannot replicate.

**2. Check whether the niche is growing or dying.**

```
list_rankings(country: "us", chart: "grossing", category: "<slug>")
```

Then `get_app_rankings` on two or three names. An app climbing from #340 to #40
in six weeks says the demand is moving now. A stable top ten says the market is
settled and you would be fighting for scraps.

**3. Look for the newcomer, not the leader.**

```
search_apps(search: "<niche>", sort: "reviews", limit: 25)
```

An app released under eighteen months ago already earning real money is the single
best signal in this whole exercise: it proves the market still lets someone in. Check
`releasedAt` on the results. The leaders tell you the ceiling; the newcomer tells you
the door is open.

**4. Read the money before falling in love with the idea.**

```
get_app(app_id: "<id>")
```

Look at revenue against downloads. High downloads and low revenue means a niche that
does not pay, however popular it looks. The inverse, modest downloads with strong
revenue, is where a small team can live comfortably.

## What to report

Name the two or three concepts that survived, and for each one: what it does in a
sentence, what the leader earns, what the most recent entrant earns, and the one
reason the market is or is not still open.

Say plainly when a niche fails the test. "Nothing here is worth building" is a useful
answer and saves months.

## Watch out

Revenue and download figures are **estimates**. Use them to compare apps and to judge
orders of magnitude, never as accounting.

Credits are charged per row. A limit is a maximum, not a bill: 15 returned items cost 15 credits.
Search narrow, then go deep on the few names that matter.
