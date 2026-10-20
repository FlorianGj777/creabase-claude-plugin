---
name: spy-meta-ads
description: Spy on a competitor's ads on Meta (Facebook and Instagram Ad Library), TikTok (TikTok ad library, European countries), Google (Ads Transparency Center), LinkedIn (LinkedIn Ad Library) or Snapchat (Snap Ads Gallery, EU and Turkey) and turn them into a creative strategy audit — estimated monthly budget, winning ads that have run longest, most-shown ads, hooks, angles, personas, formats, CTAs and landing pages. Use when the user names a brand, a website domain or pastes a facebook.com/ads/library or adsgallery.snap.com link and asks what ads a competitor runs, what is working for them, how much they spend, or wants a competitor ad teardown.
---

# Spy on a competitor's ads

Uses the Créabase connector to scrape every active ad of one brand, on Meta, TikTok, Google, LinkedIn or Snapchat, and return a complete audit.

## Steps

1. **Check past audits first.** Call `espion_history`. If the brand was audited recently, call `espion_report` with its id instead of starting a new one: it is free.
2. **Run the audit.** Call `espion_run` with:
   - `query`: the brand name or the Meta Ad Library URL the user gave. For Google, the advertiser's domain (e.g. `decathlon.fr`) is the most reliable query. For LinkedIn, the company name as it appears on its ads. For Snapchat, the name of the advertiser paying for the ads, or an adsgallery.snap.com link;
   - `platform`: `meta` (default), `tiktok`, `google`, `linkedin` or `snapchat`. Use `tiktok` when the user asks about TikTok ads (European countries only), `google` when they ask about Google, Search, YouTube, Shopping or Display ads, `linkedin` for LinkedIn ads (B2B, recruitment), `snapchat` for Snapchat ads (EU countries and Turkey only; `ALL` covers all of Europe);
   - `country`: the market the user cares about (two-letter code, default `FR`).
   It costs 25 Créabase credits and takes from one to several minutes. Tell the user before launching it.
3. **Ambiguous brand name.** If the tool returns several candidates instead of a report, show them to the user (name, page or advertiser, ad volume), let them pick, then call `espion_run` again with the chosen `pageId` (the advertiser id for TikTok and Google, the exact name for LinkedIn and Snapchat).
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

Platform specifics:

- **Only Meta publishes the data behind a budget estimate**: TikTok, Google, LinkedIn and Snapchat publish no spend, so there is no budget for them; say so instead of guessing.
- **LinkedIn** publishes impressions as ranges and the targeting on each ad's detail page, but no age or gender.
- **Snapchat** publishes exact impressions by country, the targeting (age, gender) and the advertiser's internal ad names, which often reveal campaign, audience and product. On Snapchat, "active" only means "not paused": ads that stopped gaining impressions since an earlier scan are excluded from the report. On the first scan of a brand this cannot be checked yet; the report says so, and re-running the audit a day later removes the ads that stopped.

## Notes

- The AI analysis may be missing from `espion_report` when it was never generated (`analysisNote` explains why). The rest of the report is complete; do not re-run `espion_run` to get it.
- Answer in the user's language.
- Data comes from the public ad libraries (Meta Ad Library, TikTok ad library, Google Ads Transparency Center, LinkedIn Ad Library, Snap Ads Gallery). Spend and reach are estimates; say so when quoting them.
- If a library temporarily limits searches, the tool says so: tell the user to retry in a few minutes. No credits are spent.
