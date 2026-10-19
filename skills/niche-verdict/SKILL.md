---
name: niche-verdict
description: Decide go or no-go on a niche, and say it plainly. Use when someone asks whether they should build in a market, whether it is too crowded, or whether an idea is worth the next three months.
---

Use the Peekly MCP at `https://peekly.app/api/v1/mcp`. Read `tools/list` before using
the examples: respect its current parameter schema and cost. Keep calls bounded, read `_credits`, and stop on an access or quota refusal.

# Giving a verdict, not a dashboard

Most market research ends with "here are the numbers, you decide". That is the easy half.
This skill ends with a **verdict**: build, don't build, or build only under this condition.

You will be wrong sometimes. Say so, and say what would change your mind.

## The four tests

A niche has to pass all four. One failure is usually enough to say no.

**1. Does it pay at all?**

```
search_apps(search: "<niche>", sort: "revenue", limit: 12)
```

If the leader is under $20k a month, stop here. You have found a hobby, not a market. This
single test kills most ideas, and it takes one call.

**2. Is the money spread or captured?**

Read the distribution, not the top line. One app taking everything means a brand, a moat or
a distribution deal you cannot replicate. Six apps between $30k and $150k means a market
where a seventh fits.

**3. Did anyone get in recently?**

Look at `releasedAt` across the results, and run `get_app_rankings` on the youngest
that earns real money. An app under eighteen months old already making money is the
strongest signal in this whole exercise: it proves the door is still open. No recent
entrant, and you are looking at a closed market whatever the revenue says.

**4. Can you be found?**

```
get_keyword_difficulty(keyword: "<the main term>")
```

A great product nobody can find is a dead product. If the head term is locked and no
long-tail variant is reachable, the niche fails even when the money is there.

## The verdict

Write it in this order, and keep it short.

**The call.** Build, don't build, or build if. One sentence.

**Why.** The two numbers that decided it. Not ten.

**What would change it.** The specific thing you would need to see. "If a new app enters
above $30k in the next six months, revisit."

**What you would build.** Only if the call is build: the one angle nobody in the niche is
covering, taken from what the current apps do not do.

## Watch out

Revenue is estimated. A niche that fails by a small margin deserves a second look with a
different search term; a niche that fails by an order of magnitude does not.

Never soften a no. Someone about to spend three months on an idea is better served by a
clear no today than by a hedged maybe.
