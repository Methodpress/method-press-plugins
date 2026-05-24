# amazon-acos-health-check — Install & Usage Guide

**What it does:** Diagnoses the health of your Amazon Sponsored Products advertising from a single snapshot of numbers. It calculates your ACoS, break-even ACoS, ROAS, CTR, CVR, and CPC, then walks a five-cause diagnostic — targeting, bid, price, reviews, or the listing itself — and tells you which one is actually the problem. Free. Read-only. Takes about two minutes.

---

## Why this exists

When ACoS is bad, the instinct is to lower bids. About half the time that's the wrong move — the real problem is the listing, the price, or the review base, and cutting bids just slows the loss instead of fixing the cause. This skill runs the diagnostic the way it should be run: compute the numbers, then rule the five possible causes in or out one at a time. You leave with a specific answer, not a vague "your ACoS is high."

It's a focused free tool. It tells you *which* lever is the problem. The full methodology — what to actually do about each one, the eight-task launch sequence, the operating cadence, a real case study — is the [Amazon Brand Launch Bundle](https://methodpress.ai).

---

## Install

1. Install this plugin from the Claude Plugin Marketplace, or copy the `amazon-acos-health-check/` folder into your Cowork skills directory.
2. Open `SKILL.md` and fill in the Parameters block — your per-unit economics (retail price, unit cost, FBA fees). These don't change run-to-run, so you set them once.
3. That's it. The skill prompts you for the rest at run time.

---

## Parameters — what to fill in

| Parameter | What to enter |
|---|---|
| `retail_price` | What one unit sells for on Amazon |
| `unit_cost` | Cost of goods per unit — manufacturing plus inbound freight |
| `fba_fees` | Amazon referral + FBA fulfilment fees per unit |
| `prefer_mcp` | `true` to let the skill pull campaign numbers via the Amazon Ads MCP Server when it's connected; `false` to always paste numbers manually |

**If you don't know your exact per-unit economics:** estimate. The break-even ACoS will be approximate, but the health rating and the diagnostic still work. A rough break-even is far more useful than no break-even — most sellers run ads without knowing this number at all, which is why they can't tell a profitable 30% ACoS from a bleeding one.

---

## What you need to run it

Six numbers, covering a recent window (the last 7–14 days works best):

- Ad spend, ad sales, clicks, impressions, and ad-attributed orders — all readable off your Amazon Ads campaign manager dashboard
- Your current review count and average star rating — from the product detail page

If you have the Amazon Ads MCP Server connected and `prefer_mcp` is `true`, the skill will offer to pull the first five automatically. The review numbers always come from you — reviews live on the product page, which the Ads MCP doesn't cover.

---

## What you get

A short report: the six computed metrics in a table, a health rating (🟢 Healthy / 🟡 Watch / 🔴 Bleeding) judged against your break-even ACoS, and — if the advertising is losing money — a specific diagnosis naming which of the five causes is responsible, with the numbers that point to it.

The diagnostic key the skill is built around: **healthy CTR plus collapsed CVR means the listing is the problem, not the campaign.** When that pattern shows up, the skill will tell you plainly that lowering bids is the wrong fix.

---

## What it won't do

- It won't change anything in your Amazon account. It's read-only — it computes and diagnoses, you act.
- It won't guess missing numbers. If something's missing, it asks.
- It won't give you a step-by-step fix. It names the problem and the direction of the solution. The full how-to is the bundle.
- It won't hedge across all five causes. You get one primary diagnosis, with a contributing cause noted if there is one.

---

## Troubleshooting

**"I don't know my FBA fees"** — Amazon's Revenue Calculator (free, in Seller Central) gives you the per-unit referral and fulfilment fees for any ASIN. Or estimate: for most products in the £15–40 range, FBA fees land somewhere around 25–35% of retail. An estimate is fine.

**The break-even ACoS looks wrong** — check that `unit_cost` and `fba_fees` are per-unit, not totals, and that all three economics figures are in the same currency. Break-even ACoS below 20% or above 70% is unusual; if you're seeing that, re-check the inputs.

**The skill pulled MCP numbers that don't match my dashboard** — Amazon's ad reporting has a 12–48 hour attribution lag, and the MCP reads from the same backend. The most recent day or two will under-report. Pull a window that ends 2+ days ago for the most stable read.

---

## Version

v1.0 — a free diagnostic tool from Method Press. Pairs with the Amazon Brand Launch Bundle at methodpress.ai, which covers the full methodology behind this diagnostic.
