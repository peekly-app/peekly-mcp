---
name: launch-window
description: Read how apps in a category actually break through, so a launch is planned against evidence rather than hope. Use when someone asks when to launch, what a good first month looks like, or why their launch stalled.
---

Use the Peekly MCP at `https://peekly.app/api/v1/mcp`. Read `tools/list` before using
the examples: respect its current parameter schema and cost. Keep calls bounded, read `_credits`, and stop on an access or quota refusal.

# What a real breakthrough looks like

Almost every launch plan is built on a story someone read once. This skill replaces the
story with the actual shape of the apps that got in: how long they took, what they did on
the way, and what the numbers looked like at each step.

It is also the fastest way to settle an argument. "We should be top 50 by week two" either
matches what happened to the last five entrants, or it does not.

## Work in this order

**1. Find the recent entrants, not the leaders.**

```
search_apps(search: "<category>", sort: "reviews", limit: 25)
```

Read `releasedAt`. The apps released in the last eighteen months that now earn real money
are your reference group. The leaders are useless here: they launched into a different
market, often years ago.

**2. Read their climb, day by day.**

```
get_app_rankings(app_id: "<id>", country: "us", chart: "grossing", days: 180)
```

Pass a country and a chart, always. Then look for the shape:

A slow steady climb means the category rewards accumulation, and your first month will feel
like nothing is happening. That is normal there, and quitting at week six is the mistake.

A flat line then a sudden break means someone lit a fuse: a campaign, a feature, a video
that took off. Find the date of the break and go look at what happened around it.

**3. Find what happened at the break.**

```
get_app_ads(app_id: "<id>")
```

Line the creative start dates up against the break in the chart. Ads that started a week
before a climb is the most common explanation, and the easiest to reproduce.

If nothing started, the push came from somewhere we do not see: organic video, press, a
store feature. Say so rather than inventing a cause.

**4. Turn it into expectations.**

From the reference group, write down: the median time from release to their first real
revenue, the chart position where the money started, and whether they paid to get there.

That is your plan's yardstick. A launch that misses it by a week is fine. A launch built on
a shape that has never happened in this category is not a launch plan.

## What to report

The shape the category rewards, in one sentence. The median time to traction across the
reference group. What the ones who broke through did at the break. And the honest version
of what month one should look like, including how boring it will be.

## Watch out

Chart history is per country and per chart. A US grossing climb and a French free-chart
climb are different phenomena; do not mix them in the same reading.

Survivor bias is built into this exercise: you are only looking at the apps that made it.
The ones that launched the same way and died are not in the data, so treat what you find as
necessary, not sufficient.
