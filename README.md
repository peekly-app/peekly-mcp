# Peekly MCP

Ask your AI assistant which mobile apps are actually making money, and why.

Peekly tracks the App Store and Google Play every day: chart positions, estimated
revenue and downloads, the ad creatives apps are running, the paywall and onboarding
screens they use to convert, the TikTok, Reels and Shorts videos that talk about them,
their store reviews and App Store keywords. This connector puts all of it inside
Claude, ChatGPT, Cursor or any MCP client, so you never leave your editor to research
a market.

```
"Find meditation apps making over $30k a month, show me their paywalls
 and tell me what they all have in common"
```

That question costs a few tool calls and comes back with real numbers and the actual
screens, not a summary of a blog post.

## Connect

The server is at:

```
https://peekly.app/api/v1/mcp
```

You sign in with your Peekly account. There is no key to copy and paste: the client
discovers the authorization endpoint on its own, opens peekly.app in your browser,
and you click Authorize.

**Claude**: Settings, Connectors, Add custom connector, then paste the URL.

**ChatGPT**: Settings, Apps, Advanced settings, enable Developer mode, Add custom
connector, then paste the URL.

**Claude Code**

```bash
claude mcp add --transport http peekly https://peekly.app/api/v1/mcp
```

Then run `/mcp` inside Claude Code and choose peekly to sign in.

**Codex**

```bash
codex mcp add peekly --url https://peekly.app/api/v1/mcp
codex mcp login peekly
```

**Cursor**: Settings, MCP, Add server, same URL.

An active Peekly subscription is required. [Start here](https://peekly.app/pricing).

## What you see

In clients that support MCP Apps (Claude, ChatGPT), the final answer comes with
**cards** for exactly what it presents: an app profile with its screenshots and revenue,
charts, rankings, ad creatives, paywall and onboarding screens, videos, creators and
studios. The research steps before it stay quiet, so you get one clean set of cards,
not a card for every search. Other clients receive the same data as text.

Paywall screens, onboarding screens and video thumbnails are also attached as **real
images**, so the assistant can read what is on them: the price, the promise, the
layout. That is the difference between "here are seven links" and "here is how their
pricing screen changed between 2024 and 2026".

## Tools

48 tools. They read Peekly data and never change anything in your account. One
exception: give `get_app` a store link for an app Peekly does not track yet, and it
returns the public store profile and registers the app for analysis.

### Apps and charts

| Tool | What it answers | Cost |
|---|---|---|
| `search_apps` | Search and filter apps by niche, revenue, downloads, rating and marketing signals | 1 credit / app |
| `get_app` | The full profile of one app, even one Peekly doesn't track yet, from its store link | 1 credit, +1 / public review |
| `get_app_metrics` | Its key figures, records and how it ranks against its category | 1 credit |
| `get_app_history` | Revenue, downloads, reviews and rank, day by day | 1 credit / observation |
| `get_app_events` | Updates, price changes and other events for the app | 1 credit / event |
| `get_app_rankings` | Its position day by day, per country and per chart | 1 credit / observation |
| `list_rankings` | Today's Top Free, Top Paid and Top Grossing, per country and category | 1 credit / app |
| `compare_apps` | Up to three apps side by side, curves included | 1 credit / observation |
| `get_similar_apps` | The apps competing on the same ground | 1 credit / app |
| `get_app_reviews` | Recent store reviews, filterable by stars and country | 1 credit / review |

### Studios

| Tool | What it answers | Cost |
|---|---|---|
| `list_publishers` | Studios ranked by estimated revenue | 1 credit / studio |
| `get_publisher` | One studio's profile and its best apps | 1 credit |
| `list_publisher_apps` | Every app from one studio | 1 credit / app |
| `get_publisher_history` | A studio's recent trajectory | 1 credit / day |

### Ads

| Tool | What it answers | Cost |
|---|---|---|
| `search_ads` | The Meta creatives running now, with how long each has been live | 1 credit / ad |
| `get_app_ads` | Every ad from one app, newest first | 1 credit / ad |
| `get_ad` | One ad in detail: copy, dates, countries, media | 1 credit |
| `get_app_ad_metrics` | Active ad count and estimated spend over time | 1 credit / day |
| `get_app_ad_countries` | The countries and languages its ads run in | 1 credit / country |

### Paywalls and onboardings

| Tool | What it answers | Cost |
|---|---|---|
| `search_paywalls` | How apps in a niche ask for money, screens included | 1 credit / screen |
| `get_app_paywalls` | Every paywall captured for one app | 1 credit / screen |
| `search_onboardings` | The onboarding journeys of apps that convert | 1 credit / journey |
| `get_app_onboarding` | One app's onboarding, screen by screen | 1 credit / screen |
| `get_onboarding` | One specific journey, with its video and chapters | 1 credit / screen |

### Videos and creators

| Tool | What it answers | Cost |
|---|---|---|
| `list_organic_content` | The TikTok, Reels and Shorts videos about an app | 1 credit / video |
| `get_organic_video` | One video in detail and the apps it features | 1 credit |
| `search_creators` | The creators talking about apps, with their audience | 1 credit / creator |
| `get_creator` | One creator's profile | 1 credit |
| `list_creator_videos` | One creator's videos | 1 credit / video |
| `get_feed` | The feed of ads and videos that work | 1 credit / video |

### Keywords

| Tool | What it answers | Cost |
|---|---|---|
| `get_keyword_difficulty` | Popularity, difficulty, related keywords and who ranks | 10 credits |
| `get_keyword_rankings` | The apps ranking for a keyword | 1 credit / app |
| `get_keyword_history` | How a keyword's ranking has moved | 1 credit / point |
| `list_related_keywords` | Nearby keywords worth exploring | 1 credit / keyword |
| `get_app_keywords` | The keywords an app ranks for | 1 credit / keyword |

### Reports

| Tool | What it answers | Cost |
|---|---|---|
| `list_reports` | The reports available | free |
| `get_report` | One public report: top earners, growth, categories | 1 credit / row |

### Your account

| Tool | What it answers | Cost |
|---|---|---|
| `get_account` | Your account and subscription | free |
| `get_usage` | Your remaining credits this month | free |
| `list_tracked_apps` | The apps you track | 1 credit / app |
| `get_tracker_events` | What changed on the apps you track | 1 credit / event |
| `list_favorite_folders` | Your favorite folders | 1 credit / folder |
| `list_favorites` | Your favorites: apps, ads, paywalls, videos, keywords, onboarding screens | 1 credit / favorite |
| `get_notifications` | Your latest notifications | 1 credit / notification |
| `get_notification_preferences` | Your notification settings | 1 credit / setting |

### Display

| Tool | What it answers | Cost |
|---|---|---|
| `show_results` | Shows the cards for the apps, ads, paywalls, onboardings, videos, creators, studios and keywords in the final answer, up to 24 | 1 credit / item shown |

### Reference

| Tool | What it answers | Cost |
|---|---|---|
| `get_supported_countries` | The countries available | free |
| `get_supported_filters` | The categories, stores and filters available | free |

## Prompts

The server also ships six ready-made prompts, which appear in clients that support
them: find an app idea, niche verdict, competitor analysis, ad analysis, growth report
and review analysis. Opening a prompt costs nothing; the tools it then calls cost
their usual credits.

## Credits

Credits are counted **per row returned**, not per call. A search that gives you five
apps costs five credits; the same search returning fifty costs fifty. So ask for what
you need, and narrow your filters.

A Pro subscription includes 10,000 credits a month. Every reply tells you what the
call cost and what is left. `get_keyword_difficulty` costs 10 credits per keyword,
more than the rest. Account and reference tools are free.

Requests are capped at 60 per minute.

## Skills

The [`skills/`](./skills) folder holds ready-made workflows for agents. Each one is a
short brief telling the assistant which tools to chain, in what order, and how to read
the result.

| Skill | For |
|---|---|
| [find-app-ideas](./skills/find-app-ideas) | Finding a proven concept worth building |
| [niche-verdict](./skills/niche-verdict) | Deciding go or no-go, and saying it plainly |
| [analyze-paywalls](./skills/analyze-paywalls) | Reading the screens that convert |
| [pricing-from-paywalls](./skills/pricing-from-paywalls) | Setting your price from what the niche charges |
| [ad-intelligence](./skills/ad-intelligence) | Reading a competitor's paid acquisition |
| [creative-brief](./skills/creative-brief) | Turning winning ads into a brief you can shoot |
| [competitor-watch](./skills/competitor-watch) | Reporting what changed, not what is |
| [launch-window](./skills/launch-window) | Planning a launch against what actually happened |
| [keyword-research](./skills/keyword-research) | Picking App Store keywords you can win |
| [metadata-optimization](./skills/metadata-optimization) | Writing three store title, subtitle and keyword sets |
| [review-analysis](./skills/review-analysis) | Turning store reviews into complaints, requests and priorities |

To use one in Claude Code, drop the folder into `.claude/skills/` in your project.

## The numbers

Downloads and revenue are **estimates**, and we say so everywhere. Apple publishes no
download figures at all; Google publishes brackets. Everything else on a Peekly
profile is a fact taken from the stores: chart positions, ratings, review counts,
prices, release and update dates.

Estimates are useful for orders of magnitude and for comparing apps against each
other. They are not accounting. Treat "$400k a month" as "this is a big business",
not as a number you would put in a spreadsheet. A value shown as "< $5k" means below
$5,000 a month, not zero.

## Links

- [peekly.app](https://peekly.app)
- [Pricing](https://peekly.app/pricing)
- [Methodology](https://peekly.app/methodology): how the estimates are built
- [Privacy](https://peekly.app/privacy)
- Support: hello@peekly.app

## License

MIT, for the contents of this repository. The Peekly service itself is subject to its
own [terms](https://peekly.app/terms).
