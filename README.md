# Bounty Radar — Public Data Feed + Paid REST API

Live JSON + RSS feed of open ZK / AI bounties across 11 ecosystems (Algora, GitHub labels, Drips Wave, Code4rena, Bountycaster, Midnight, Aleo, Noir, Aztec, Stacks, Starknet, Mina, risc0).

## Free endpoints (no key required)

- HTML index: <https://battam1111.github.io/bounty-radar-data/>
- JSON feed (top 200): <https://battam1111.github.io/bounty-radar-data/feed.json>
- JSON free tier (top 20): <https://battam1111.github.io/bounty-radar-data/feed-free.json>
- RSS / Atom: <https://battam1111.github.io/bounty-radar-data/feed.xml>
- Per-ecosystem feeds: `/noir.json`, `/aleo.json`, `/aztec.json`, etc.

## Paid REST API (per-filter feeds, 5-min refresh)

Buy a Polar subscription, activate with `bounty radar-api activate <license_key>`, and we publish a JSON feed scoped to YOUR filter at a per-license URL:

```
https://battam1111.github.io/bounty-radar-data/api/<prefix>_<license_key>/feed.json?sig=...&exp=...
```

| Tier         | Price       | Filters       | Prefix |
|--------------|-------------|---------------|--------|
| **Hobbyist** | $19/mo      | 1 constraint  | `h_`   |
| **Pro**      | $97/mo      | 5 constraints | `p_`   |
| **Team**     | $497/mo     | unlimited     | `t_`   |

Filter shape: `{"ecosystem":"noir","min_reward_usd":250}` — see [docs/RADAR_API.md](https://github.com/Battam1111/bounty-agent/blob/main/docs/RADAR_API.md) in bounty-agent for the full reference.

Buy at <https://polar.sh/Battam1111> — checkout URLs are pinned in the storefront.

### How it works

1. Polar issues you a license key on purchase.
2. `bounty radar-api activate <key> --filter '<json>'` validates the key against Polar and stores your filter on the mini.
3. Every 5 minutes, the refresh job regenerates your filtered `feed.json` and pushes this repo. GitHub Pages serves it.
4. The URL is HMAC-signed with your license key so you can self-verify it came from us.

### Why static instead of a live server?

The mini's network has a transparent TLS proxy that MITMs strict-TLS clients (Tailscale failed for this reason). Until we route outbound through a token-auth CDN, static export to GitHub Pages is the only stable hosting option that doesn't cost extra per month.

## License

MIT — see LICENSE.
