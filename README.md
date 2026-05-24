# Method Press — Amazon ACoS Health Check

A **free, read-only** Amazon Sponsored Products diagnostic for Claude. Paste in (or pull via the Amazon Ads MCP) six numbers from a recent ad window, and it tells you — in about two minutes — whether your advertising is healthy, and if it isn't, *which* of five things is actually the problem.

When ACoS is bad, the instinct is to lower bids. About half the time that's the wrong move: the real cause is the listing, the price, or the review base, and cutting bids just slows the loss instead of fixing it. This skill runs the diagnostic the way it should be run — compute the numbers, then rule the five causes in or out one at a time — so you leave with a specific answer instead of "your ACoS is high."

## What it does

- Computes **ACoS, break-even ACoS, ROAS, CTR, CVR, and average CPC** from a single snapshot
- Rates the account 🟢 Healthy / 🟡 Watch / 🔴 Bleeding against *your* break-even, not a generic benchmark
- Walks a **five-cause diagnostic** — targeting, bid, price, reviews, listing — and names the one that's actually responsible
- Built around the key tell: **healthy CTR + collapsed CVR = the listing is the problem, not the campaign** (and it'll say so plainly)
- **Read-only.** It never changes anything in Amazon Ads or Seller Central. It computes and diagnoses; you act.
- **Dual-mode.** Pulls the numbers automatically when the Amazon Ads MCP Server is connected, or takes them pasted in.

## Install

```
/plugin marketplace add <your-github-username>/<your-repo-name>
/plugin install method-press-acos-health-check@method-press
```

Then open the skill's `SKILL.md`, fill in your per-unit economics once (retail price, unit cost, FBA fees), and run it. Full setup and usage notes are in [`skills/amazon-acos-health-check/README.md`](skills/amazon-acos-health-check/README.md).

## The full picture

This skill diagnoses one snapshot — it tells you *which* lever is the problem. What to actually do about each one (fixing a listing-conversion problem, restructuring keywords, sequencing a relaunch), the eight-task launch sequence, the operating cadence, and a real case study with the numbers behind a live launch are in the **Amazon Brand Launch Bundle** at [methodpress.ai](https://methodpress.ai).

---

*A free tool from David Hart / Method Press.*
