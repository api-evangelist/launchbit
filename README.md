# Launchbit

LaunchBit was an email-newsletter advertising startup founded in 2012 and incubated through 500 Startups,
co-founded and led by CEO Elizabeth Yin. It began as an email ad network for B2B/SaaS advertisers and
pivoted in March 2014 toward a customer-acquisition and lead-generation platform for SaaS companies.

**Acquired by [BuySellAds](https://buysellads.com) in September 2014** (terms undisclosed) —
[TechCrunch, 2014-09-17](https://techcrunch.com/2014/09/17/buysellads-acquires-launchbit/).

Backed by: 500-global

## Status: historical / acquired — no API surface

LaunchBit never published a public API, developer portal, or SDKs, and it no longer operates
independently. This repo is retained as a historical record, not an active API provider profile.

## Enrichment notes (2026-07-19)

Re-runs of the enrichment pipeline should be aware of the following, so nothing is recorded falsely:

- `launchbit.com` still resolves (Cloudflare NS) but **serves the BuySellAds corporate homepage for
  every path**. It is a wildcard catch-all.
- **Every probed path returns HTTP 200 with BuySellAds homepage HTML** — including
  `/.well-known/security.txt`, `/.well-known/openid-configuration`,
  `/.well-known/oauth-authorization-server`, `/.well-known/api-catalog`,
  `/.well-known/ai-plugin.json`, and `/llms.txt`. These are **soft 404s, not real artifacts**.
  Verified by requesting a nonsense path (`/this-path-does-not-exist-zzz123`), which also returns 200
  with the same HTML. Do **not** harvest these as WellKnown / SecurityTxt / LLMsTxt artifacts.
- Security-program probe found no vulnerability-disclosure program and no trust center for this domain.
- BuySellAds' own developer/legal/blog pages belong to **BuySellAds**, a separate company. They must not
  be wired into this profile — doing so would misattribute another company's assets to LaunchBit.

Only artifact produced: `security/launchbit-domain-security.yml` (live DNS/TLS probe of the domain as it
stands today).
