# Créabase for Claude

![Créabase](icon.png)

Spy on your competitors' Meta ads from Claude. Créabase reads the public Meta Ad Library (Facebook and Instagram) and turns a brand's ads into a creative strategy audit: estimated monthly budget, the winning ads that have run longest, the most-shown ads, hooks, angles, personas, formats, CTAs and landing pages. It also tracks competitor brands every day and keeps a curated index of long-running ads by industry.

Built for media buyers, e-commerce brands and agencies running Meta Ads.

## What's inside

| Skill | Use it to |
| --- | --- |
| `spy-meta-ads` | Audit one competitor's Meta ads: budget, winning ads, angles, personas, landing pages. |
| `track-competitor-ads` | Follow competitor brands and get a digest of what changed: new ads, cut ads, new winners. |
| `find-winning-ads` | Find the longest-running ads in an industry or for a brand, and save them to a swipe file. |

The plugin connects Claude to the Créabase MCP server at `https://www.creabase.app/api/mcp/directory`.

## Getting started

1. Install the plugin.
2. When Claude first calls a Créabase tool, sign in to your Créabase account (OAuth). No API key to paste. A free account works: [create one here](https://www.creabase.app).
3. Ask, for example:
   - "Spy on Gymshark's Meta ads in France."
   - "What's new in my competitors' ads this week?"
   - "Show me the longest-running ads in the beauty industry."

## Credits and plans

Reading reports, tracked-brand feeds, the industry index and your swipe file is free. Live actions use Créabase credits: a full competitor audit (`espion_run`) costs 25 credits, a live Ad Library search 2, adding a brand to tracking 5, saving an ad 1. Plan limits and pricing: [creabase.app/pricing](https://www.creabase.app/pricing).

## What the plugin sends and stores

- The plugin itself runs no code on your machine. It only declares the Créabase MCP server and the skills above.
- Tool calls go to `www.creabase.app` over HTTPS, authenticated with your Créabase account. They contain the brand names, Ad Library links, countries and ids you ask about.
- Créabase stores the audits, tracked brands and saved ads in your account so you can reopen them in the Créabase app. Ad data comes from the public Meta Ad Library.
- Créabase does not read or store your Claude conversations.

## Privacy policy

[creabase.app/confidentialite](https://www.creabase.app/confidentialite)

## Support

support@creabase.app — documentation: [creabase.app/connecter-ia](https://www.creabase.app/connecter-ia)

## License

MIT
