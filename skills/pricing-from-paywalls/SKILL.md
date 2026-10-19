---
name: pricing-from-paywalls
description: Set a price from what the niche actually charges, using captured paywall screens and revenue estimates. Use when someone asks what to charge, whether their price is too low, or how to structure their plans.
---

Use the Peekly MCP at `https://peekly.app/api/v1/mcp`. Read `tools/list` before using
the examples: respect its current parameter schema and cost. Keep calls bounded, read `_credits`, and stop on an access or quota refusal.

# Pricing from what people already pay

Pricing advice is usually a framework. This is not a framework: it is reading the prices
that apps earning six figures a month actually display, and placing yourself among them.

The difference matters. A framework tells you to "charge based on value". The paywall of an
app making $400k a month tells you the number.

## Work in this order

**1. Collect the prices in the niche, filtered by revenue.**

```
search_paywalls(search: "<niche>", min_revenue: 50000, limit: 10)
```

The `min_revenue` filter is what makes this exercise worth anything. A price from an app
earning $2k a month teaches you nothing; it may be why they earn $2k.

Images come back attached. Read the actual numbers off the screens.

**2. Build the ladder.**

Write down, for each app: the monthly price, the annual price, the implied discount, and
the trial length. You now have the range the market bears. The median is far more useful
than the leader: the leader may charge more because of a brand you do not have.

**3. Read the structure, not just the number.**

Which plan is preselected. How the other one is made to look worse. Whether the annual is
shown as a total or as a per-month equivalent. Whether the trial is 3, 7 or 14 days.

These choices are worth as much as the price. An annual preselected at a per-month
equivalent is the single most common pattern among apps that monetise well, and it is not
an accident.

**4. Follow one app through time.**

```
get_app_paywalls(app_id: "<id>")
```

Screens come back newest first with their capture dates. An app that raised its price and
kept climbing has told you the market bears more. An app that added or dropped a trial made
that call against its own data. Their experiments are free for you to read.

**5. Place yourself.**

Below the median if you are unknown and the niche has an obvious leader. At the median if
your product is comparable. Above only if you have something the others visibly do not,
and you can name it in one sentence on your own paywall.

## What to report

The range, the median, and the most common structure across the niche. Then a
recommendation written out as it would appear on screen: this monthly, this annual, this
trial, this preselection, this headline.

Say which apps you took each element from. A recommendation you cannot trace is a guess.

## Watch out

Prices are as captured on that date, in the store's currency, and may have changed. The
capture date sits on every screen; use it.

Price is one variable among several. The same paywall after a strong onboarding and after a
weak one produces very different numbers. What you are reading is the ceiling, not a
guaranteed outcome.
