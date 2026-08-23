---
name: analyze-paywalls
description: Design pricing and paywall screens from what already converts, using Peekly's captured paywall library. Use when someone asks how to charge, what to put on a paywall, what to price, or how a competitor monetises.
---

# Reading the paywalls that already convert

A paywall is the only screen in an app whose job is to take money. The ones belonging
to apps earning six figures a month have been tested against millions of users. You
can read them.

Peekly captures these screens over time, so you can see not just what an app charges
today but **what it changed and when**.

## Work in this order

**1. Gather the winners in the niche.**

```
search_paywalls(search: "<niche>", min_revenue: 50000, limit: 8)
```

The `min_revenue` filter is what makes this exercise worth anything. A paywall from an
app earning $2k a month teaches you nothing; it may be the reason they earn $2k.

Images come back attached to the reply. Look at them properly before writing a word.

**2. Read each screen for the same five things.**

The price and the billing period. Which plan is pre-selected and how the others are
made to look worse. Whether there is a free trial and how long. What the headline
promises, in their exact words. How many taps stand between opening the app and this
screen.

**3. Find the pattern, then find the outlier.**

Once you have eight screens, the convention becomes obvious: everyone offers annual
pre-selected with a trial, everyone promises the same outcome. Note it, because
breaking a convention that every profitable app follows is usually a mistake.

Then look at whoever does it differently and still earns well. That is the one worth
studying.

**4. Follow one app through time.**

```
get_app_paywalls(app_id: "<id>")
```

Screens come back newest first, each with its capture date. An app that raised its
price and kept climbing the grossing chart has told you the market bears the higher
price. An app that added a trial, or dropped one, made that choice against its own
data. Their experiments are free for you to read.

## What to report

Describe what you actually see on the screens, quoting the headline copy. Give the
price range across the niche and the most common structure. Then give a concrete
recommendation: this price, this billing period, this trial length, this promise,
because these five apps at this revenue level all do it.

Attach or link the two or three screens that best support the recommendation.

## Watch out

Prices are as captured on that date, in the store's currency, and may have changed
since. The capture date is on every screen; use it.

A paywall works with the funnel in front of it. The same screen after a great
onboarding and after a bad one produce very different numbers. What you are reading
is the ceiling of what is possible, not a guaranteed result.
