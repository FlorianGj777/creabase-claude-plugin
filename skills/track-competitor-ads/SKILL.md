---
name: track-competitor-ads
description: Track competitors' Meta ads over time and report what changed — new ads launched, ads cut, ads crossing 30 days of delivery, launch acceleration and shifts in format, CTA or landing pages. Use when the user wants to monitor or follow competitor brands, asks what is new in their competitors' ads this week, or wants a weekly competitive ads digest.
---

# Track competitors' Meta ads

Uses the Créabase Veille: tracked brands are re-scanned automatically every day.

## Add a brand to tracking

1. Call `veille_list_brands` to see what is already tracked.
2. Call `veille_track_brand` with `query` (brand name or Meta Ad Library URL). It costs 5 Créabase credits and scrapes a baseline.
   - If several pages match, show the candidates and call again with the chosen `pageId`.
   - The number of tracked brands depends on the user's plan (Free 1, Pro 10, Agency unlimited). If the limit is reached, the tool says which plan to take: relay it, do not retry.

## Weekly digest: "what's new at my competitors?"

1. Call `veille_feed` (free). Use `brandId` to focus on one brand and `newOnly: true` for unseen ads only.
2. The dashboard always covers every tracked ad; `limit` only bounds the `ads` list. Do not raise it to "get everything".
3. Report by brand, most important first:
   - **Inflections this week**: acceleration in launches, waves of cut ads, ads crossing 30 days of delivery (new winners).
   - **New ads worth looking at**: hook, format and offer of each.
   - **Strategy shifts**: share of video, CTAs, landing pages.
   - **Survival**: median ad lifespan and survival rate by launch month.
4. Give each brand's `reportUrl` (hosted dashboard with the ad visuals).

## Notes

- For a deep one-off teardown of a single brand, use the `spy-meta-ads` skill instead.
- Answer in the user's language.
