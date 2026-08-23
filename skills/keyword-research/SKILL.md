---
name: keyword-research
description: Pick App Store keywords you can realistically rank for, using Peekly's popularity and difficulty scores. Use when someone asks what keywords to target, how to write their app title and subtitle, or why they are not being found.
---

# Choosing keywords you can actually win

Two numbers decide everything. **Popularity** is how many people search a term.
**Difficulty** is how hard it is to reach the top for it. A keyword is worth targeting
when the first is high enough to matter and the second is low enough to reach.

Ranking third for a term nobody searches is worth nothing. So is ranking fortieth for
the biggest term in the category.

## Work in this order

**1. Never start with the obvious term.**

The head term of any category is owned by apps with years of history and a budget.
Check it anyway, once, to calibrate what "hard" looks like:

```
get_keyword_difficulty(keyword: "<the obvious one>")
```

Note the difficulty. Everything else gets judged against it.

**2. Go where the intent is specific.**

The keywords that convert describe a situation, not a category. Not "notes" but "scan
handwriting to text". Not "fitness" but "workout without equipment at home".

Longer phrases have lower popularity and much lower difficulty, and the person typing
them knows exactly what they want. Ten of those beat one head term you will never
reach.

**3. Read the whole answer, not just the two scores.**

Each result carries related keywords and who currently ranks. The related list is
where the real finds are: terms you would not have thought of, already proven to be
searched. The ranking apps tell you who you would have to displace, and running
`get_app` on one of them tells you whether that is remotely realistic.

**4. Check the competitors are beatable.**

If the top three for a keyword all earn six figures a month, difficulty is
understating the problem: they can outspend you on everything. If the top three are
small apps with old last-update dates, that keyword is available whatever its score
says.

**5. Turn the list into actual metadata.**

The title carries the strongest weight, then the subtitle, then the keyword field.
Put the single most valuable winnable term in the title, next two in the subtitle,
and never repeat a word across the three — repetition wastes a slot without adding
weight.

## What to report

A ranked shortlist, each line with its popularity, its difficulty, and one sentence on
why it is reachable. Then a proposed title and subtitle, written out, using them.

Say clearly which terms to give up on, and why. That is often the most useful part.

## Watch out

`get_keyword_difficulty` costs **10 credits per keyword**, more than any other tool,
because that data is bought from an external provider. Think before running twenty
terms: pick candidates first, then measure.

Scores describe the App Store. Google Play ranks on different signals and these
numbers do not transfer.
