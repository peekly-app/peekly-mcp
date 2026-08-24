---
name: creative-brief
description: Turn the ads that are already winning into a brief your designer or your video editor can shoot tomorrow. Use when someone needs to produce creatives, not just study them.
---

# From what works to what to shoot

Analysing ads is the easy part. This skill ends with something a person can actually
produce: a brief, with a hook written out, a format, a length, and a shot list.

The raw material is public and free to read: **how long a creative has been running**.
Nobody keeps paying to run an ad that loses money, so a creative live for two hundred days
is a creative that works.

## Work in this order

**1. Take only the survivors.**

```
search_ads(search: "<niche>", status: "active", min_days_running: 90, min_app_revenue: 30000)
```

Two filters carry this query. `min_days_running` removes every experiment and keeps what
survived. `min_app_revenue` removes apps whose ads may run long because nobody watches the
budget.

Images come back attached. For a video you get its thumbnail, which is the frame that stops
the scroll, and therefore the part that matters most.

**2. Take apart the first three seconds.**

For each survivor, write down what appears, whether a face is shown, whether the app's
interface is visible at all, and what claim is made. Read the on-image text separately from
the ad copy: they usually say different things on purpose.

**3. Separate the convention from the edge.**

After eight creatives, the convention is obvious: everyone opens the same way, everyone
promises the same outcome. Note it, because breaking a convention that every profitable app
follows is usually a mistake.

Then find the one that does it differently and still runs long. That one is worth more than
the other seven.

**4. Check the promise against the paywall.**

```
get_app_paywalls(app_id: "<id>")
```

An ad promises something, a paywall charges for it. When the words match tightly, you are
looking at a funnel someone built deliberately, and the brief should carry that promise all
the way through.

## The brief

Write it so a designer or an editor can work from it without asking questions:

**Format and length.** Video or static, and the duration, taken from what survives.

**The hook, written out.** The actual first line, not "a strong hook". Give two variants.

**The first shot.** What is on screen at second zero.

**The claim.** The exact promise, in the words the niche uses.

**The end frame.** What the last second shows, and the call to action.

**What to avoid.** The thing every ad in the niche does that stopped working, if you spotted
one dying.

## Watch out

Never propose reusing someone's actual asset. What is reusable is the structure: angle,
claim, format, length. The image itself is theirs.

Coverage is Meta creatives. Apple Search Ads, TikTok and influencer placements do not show
up here, so a quiet app is not necessarily an app that spends nothing.

Credits are charged per creative returned. Filter hard, then widen only if you come up
short.
