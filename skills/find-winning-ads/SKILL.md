---
name: find-winning-ads
description: Find winning ads for inspiration — Meta ads that have been running the longest in an industry, or a brand's live ads straight from the Meta Ad Library, the TikTok ad library or the Google Ads Transparency Center — and save the best ones to a swipe file. Use when the user wants ad inspiration, winning ads or long-running ads in a niche, examples of creatives that work, or wants to build or browse their swipe file.
---

# Find winning Meta ads

Long delivery is the public proxy for a profitable ad: advertisers cut what does not pay. This skill finds those ads and stores the good ones.

## By industry (curated index)

1. Call `discovery_list_categories` to get the industry ids.
2. Call `discovery_search` with the `categoryId`, `sort: "longevity"` and `status: "active"` to get the longest-running ads still live. Use `sort: "recent"` to see new trends.
3. For each standout ad, explain why it likely works: hook, format, offer, angle and how long it has been running.

## For one brand, live

Call `adlibrary_search` with the brand name or Meta Ad Library URL (2 Créabase credits). For a brand's TikTok ads, pass `platform: "tiktok"` and a European `country` (default `FR`). For its Google ads (Search, Shopping, YouTube, Display), pass `platform: "google"`; the advertiser's domain (e.g. `decathlon.fr`) is the most reliable query. It returns the public total reported by Meta separately from the collected list, which can be truncated: say so when the list is shorter than the total. For a full strategic audit of that brand, switch to the `spy-meta-ads` skill.

## Save to the swipe file

- `library_list_folders` lists the user's folders.
- `library_save_ad` saves an ad by its Meta `adId`, optionally into a folder (1 credit; the media is re-hosted so it stays available after the ad stops).
- `library_list_ads` lists what is already saved.

Ask before saving: saving spends credits.

## Notes

- The industry index covers Meta ads; `adlibrary_search` covers Meta, TikTok and Google.
- Answer in the user's language.
