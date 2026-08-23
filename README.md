# Peekly MCP

Ask your AI assistant which mobile apps are actually making money, and why.

Peekly tracks the App Store and Google Play every day: chart positions, estimated
revenue and downloads, the ad creatives apps are running, the paywall screens they
use to charge, and App Store keyword difficulty. This connector puts all of it inside
Claude, ChatGPT, Cursor or any MCP client, so you never leave your editor to research
a market.

```
"Find meditation apps making over $30k a month, show me their paywalls
 and tell me what they all have in common"
```

That question costs four tool calls and comes back with real numbers and the actual
screens, not a summary of a blog post.

## Connect

The server is at:

```
https://peekly.app/api/v1/mcp
```

You sign in with your Peekly account. There is no key to copy and paste: the client
discovers the authorization endpoint on its own, opens peekly.app in your browser,
and you click Authorize.

**Claude** — Settings → Connectors → Add custom connector → paste the URL.

**ChatGPT** — Settings → Apps → Advanced settings → enable Developer mode → Add
custom connector → paste the URL.

**Claude Code**

```bash
claude mcp add peekly --transport http https://peekly.app/api/v1/mcp
```

**Cursor** — Settings → MCP → Add server, same URL.

An active Peekly subscription is required. [Start here](https://peekly.app/pricing).

## Tools

Thirteen tools, all read-only. Nothing you ask can modify anything.

| Tool | What it answers |
|---|---|
| `search_apps` | Which apps match this niche, revenue level or rating |
| `get_app` | Everything about one app, plus similar ones |
| `get_app_metrics_history` | How its revenue, downloads and ratings moved |
| `get_app_chart_history` | Where it ranked, day by day, per country and chart |
| `list_rankings` | Today's Top Free, Top Paid and Top Grossing |
| `search_ads` | Which apps are running ads, and for how long |
| `get_app_ads` | Every creative one app is running, with its stats |
| `search_paywalls` | How apps in a niche ask for money |
| `get_app_paywalls` | Every paywall screen captured for one app, over time |
| `list_organic_content` | Short-form videos about an app, and the creators behind them |
| `get_keyword_difficulty` | Popularity, difficulty and who ranks for a keyword |
| `list_publishers` | Which studios earn the most |
| `get_supported_countries` | Which countries have chart data |

Paywall screens and ad creatives come back as **real images** attached to the reply,
so the assistant can read what is on them: the price, the promise, the layout. That
is the difference between "here are seven links" and "here is what changed in their
pricing between 2024 and 2026".

## Credits

Credits are counted **per row returned**, not per call. A search that gives you five
apps costs five credits; the same search returning fifty costs fifty. So ask for what
you need, and narrow your filters.

A Pro subscription includes 10,000 credits a month. Every reply tells you what the
call cost and what is left. `get_keyword_difficulty` costs 10 credits per keyword,
more than the rest, because that data is bought from an external provider.

Requests are capped at 60 per minute.

## Skills

The [`skills/`](./skills) folder holds ready-made workflows for agents. Each one is a
short brief telling the assistant which tools to chain, in what order, and how to read
the result.

| Skill | For |
|---|---|
| [find-app-ideas](./skills/find-app-ideas) | Finding a proven concept worth building |
| [analyze-paywalls](./skills/analyze-paywalls) | Designing pricing from what already works |
| [ad-intelligence](./skills/ad-intelligence) | Reading a competitor's paid acquisition |
| [keyword-research](./skills/keyword-research) | Picking App Store keywords you can win |

To use one in Claude Code, drop the folder into `.claude/skills/` in your project.

## The numbers

Downloads and revenue are **estimates**, and we say so everywhere. Apple publishes no
download figures at all; Google publishes brackets. Everything else on a Peekly
profile is a fact taken from the stores: chart positions, ratings, review counts,
prices, release and update dates.

Estimates are useful for orders of magnitude and for comparing apps against each
other. They are not accounting. Treat "$400k a month" as "this is a big business",
not as a number you would put in a spreadsheet.

## Links

- [peekly.app](https://peekly.app)
- [Pricing](https://peekly.app/pricing)
- [Methodology](https://peekly.app/methodology) — how the estimates are built
- [Privacy](https://peekly.app/privacy)
- Support: hello@peekly.app

## License

MIT, for the contents of this repository. The Peekly service itself is subject to its
own [terms](https://peekly.app/terms).
