---
name: track-competitor-ads
description: Track competitors' ads over time on Meta, TikTok, Google, LinkedIn or Snapchat and report what changed — new ads launched, ads cut, ads crossing 30 days of delivery, launch acceleration and shifts in format, CTA or landing pages. Use when the user wants to monitor or follow competitor brands, asks what is new in their competitors' ads this week, wants a weekly competitive ads digest, or asks about a competitor's TikTok, LinkedIn or Snapchat ads.
---

# Track competitors' ads

Uses the Créabase Veille: tracked brands are re-scanned automatically every day.

## Add a brand to tracking

1. Call `veille_list_brands` to see what is already tracked.
2. Call `veille_track_brand` with `query` (brand name or Meta Ad Library URL) and `platform`:
   - `meta` (default): Facebook and Instagram;
   - `tiktok`: the TikTok ad library, which only covers European countries; pass `country`;
   - `google`: the Google Ads Transparency Center; the advertiser's domain (e.g. `maif.fr`) is the most reliable query; pass `country`;
   - `linkedin`: the LinkedIn Ad Library; the company name as it appears on its ads; pass `country`;
   - `snapchat`: the Snap Ads Gallery, EU countries and Turkey only (`ALL` covers all of Europe); the name of the advertiser paying for the ads; pass `country`.
   It costs 5 Créabase credits and scrapes a baseline. For TikTok, Google, LinkedIn and Snapchat, `baselinePending: true` means the last 30 days are still being fetched: tell the user the dashboard fills in within a few minutes.
   - If several pages match, show the candidates and call again with the chosen `pageId` (the exact name for LinkedIn and Snapchat).
   - Snapchat: "active" only means "not paused" at Snap. Créabase judges real delivery from impressions growing from one day to the next, so the ads found on day one count as active provisionally until the next daily scan. Snap publishes no end dates: all launches of the last 30 days are known, but the active-ads curve starts on the day tracking begins.
   - The number of tracked brands depends on the user's plan (Free 1, Pro 10, Agency unlimited). If the limit is reached, the tool says which plan to take: relay it, do not retry.

## Weekly digest: "what's new at my competitors?"

1. Call `veille_feed` (free). Use `brandId` to focus on one brand and `newOnly: true` for unseen ads only.
2. The dashboard always covers every tracked ad; `limit` only bounds the `ads` list. Do not raise it to "get everything".
3. Report by brand, most important first:
   - **Inflections this week**: acceleration in launches, waves of cut ads, ads crossing 30 days of delivery (new winners).
   - **New ads worth looking at**: hook, format and offer of each, with the platform it runs on.
   - **Strategy shifts**: share of video, CTAs, landing pages.
   - **Survival**: median ad lifespan and survival rate by launch month.
4. Give each brand's `reportUrl` (hosted dashboard with the ad visuals).

## Notes

- For a deep one-off teardown of a single brand, use the `spy-meta-ads` skill instead.
- Answer in the user's language.
