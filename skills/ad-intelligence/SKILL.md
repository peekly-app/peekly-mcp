---
name: ad-intelligence
description: Read a competitor's paid acquisition from the creatives they actually run, using Peekly's ad library. Use when someone asks how an app gets users, what ads work in a niche, or what to test in their own campaigns.
---

# Reading the ads that are still running

Nobody keeps paying to run an ad that loses money. **How long a creative has been
live is the closest thing to a public performance metric** that exists in paid
acquisition, and it costs nothing to read.

An ad running for two hundred days is an ad that pays for itself. An ad live for four
days is an experiment, and you have no idea yet whether it worked.

## Work in this order

**1. Find who is actually spending.**

```
search_ads(search: "<niche>", status: "active", min_days_running: 90, min_app_revenue: 30000)
```

Two filters carry this query. `min_days_running` removes every experiment and leaves
only what survived. `min_app_revenue` removes apps whose ads may be running long
simply because nobody is watching the budget.

**2. Look at the creatives themselves.**

Images come back attached. For a video ad you get its thumbnail, which is the frame
that stops the scroll and the most important part anyway.

Read the first three seconds: what appears, what claim is made, whether a face is
shown, whether the app's interface is visible at all. Read the on-image text
separately from the ad copy.

**3. Separate what everyone does from what the winner does.**

```
get_app_ads(app_id: "<id>")
```

The stats tell you the shape of their strategy. Many active creatives means constant
testing and a real budget. Three creatives running for a year means they found
something and stopped touching it. The video-versus-image mix tells you which format
their money is on.

Sort by how long each has been live. The oldest survivors are their control. Everything
newer is them trying to beat it — and what they are trying tells you what they think
matters.

**4. Cross-check against the paywall.**

An ad promises something; the paywall charges for it. Run `get_app_paywalls` on the
same app and check that the promise in the creative matches the promise on the paying
screen. When they match tightly, you are looking at a funnel someone built on purpose.

## What to report

The three or four creatives worth copying, with what makes each one work: the hook,
the claim, the format. Then the pattern across the niche, and one thing nobody in it
is doing.

Never suggest reusing someone's actual asset. What is reusable is the structure: the
angle, the claim, the format, the length.

## Watch out

Coverage is Meta creatives. An app can also buy Apple Search Ads, TikTok or influencer
placements, none of which show up here. Absence of ads is not proof of no paid
acquisition.

Credits are charged per creative returned. Filter hard before widening.
