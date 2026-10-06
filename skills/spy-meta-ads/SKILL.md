---
name: spy-meta-ads
description: Spy on a competitor's Meta ads (Facebook and Instagram Ad Library) and turn them into a creative strategy audit — estimated monthly budget, winning ads that have run longest, most-shown ads, hooks, angles, personas, formats, CTAs and landing pages. Use when the user names a brand or pastes a facebook.com/ads/library link and asks what ads a competitor runs, what is working for them, how much they spend, or wants a competitor ad teardown.
---

# Spy on a competitor's Meta ads

Uses the Créabase connector to scrape every active Meta ad of one brand and return a complete audit.

## Steps

1. **Check past audits first.** Call `espion_history`. If the brand was audited recently, call `espion_report` with its id instead of starting a new one: it is free.
2. **Run the audit.** Call `espion_run` with:
   - `query`: the brand name or the Meta Ad Library URL the user gave;
   - `country`: the market the user cares about (two-letter code, default `FR`).
   It costs 25 Créabase credits and takes from one to several minutes. Tell the user before launching it.
3. **Ambiguous brand name.** If the tool returns several candidate pages instead of a report, show them to the user (name, page, ad volume), let them pick, then call `espion_run` again with the chosen `pageId`.
4. **Scan still running.** If the response has `status: "scanning"` and `ready: false`, it holds no data yet. Do not present anything. Wait the delay it gives, then call `espion_report` with the `auditId` (free) until the report is ready.
5. **Present the report.**

## How to present the report

Lead with what a media buyer can act on, in this order:

1. **Winning ads**: the ads running for more than 30 days and the share they represent. Longevity is the strongest public signal that an ad is profitable.
2. **Scale**: estimated monthly budget and launch rhythm (new ads per week).
3. **Creative strategy**: the angles, concepts and personas from the AI analysis; recurring hooks and messages; brand vs UGC; video vs static.
4. **Funnel**: CTAs, products pushed and landing pages.
5. **Audience**: age, gender and countries reached.
6. **Next moves**: three concrete creative ideas the user could test, each tied to an ad from the report.

Always give the `reportUrl`: it is the hosted report page with the ad visuals and opens in any browser.

## Notes

- The AI analysis may be missing from `espion_report` when it was never generated (`analysisNote` explains why). The rest of the report is complete; do not re-run `espion_run` to get it.
- Answer in the user's language.
- Data comes from the public Meta Ad Library. Spend and reach are estimates; say so when quoting them.
