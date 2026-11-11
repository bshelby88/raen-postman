# raen-postman — Run the RAEN x402 fleet in Postman

A ready-made **Postman v2.1 collection** covering all 12 RAEN x402 pay-per-call APIs on Base mainnet — 20 requests, every one pre-built with example bodies and honest 402 documentation.

**Import:** Postman → Import → paste this URL:
`https://raw.githubusercontent.com/bshelby88/raen-postman/main/raen-x402.postman_collection.json`

Also works in **Insomnia** and **Bruno** (or import the [OpenAPI spec](https://raen-api-docs.vercel.app/openapi.yaml) directly).

Landing page: https://bshelby88.github.io/raen-postman/

## How x402 works

Paid endpoints return **HTTP 402 Payment Required** with a base64 `payment-required` header containing a signed challenge. Click any paid request without paying — the challenge is free. Decode the header to read `accepts[].payTo`, `maxAmountRequired`, and the facilitator URL. Settle with any x402 client (USDC on Base, `eip155:8453`) and resend with `X-PAYMENT` to get the real result.

## Folders

| Service | What it does | Requests |
|---|---|---|
| royal-ruby | law lookup (**free first call**, net $0) | 1 |
| vault-pro | Obsidian scaffolds | 2 |
| escrow | agent-to-agent USDC escrow | 1 |
| nanobanana | AI image gen & edit | 2 |
| tradingagents | market consensus demos | 2 |
| dispute-forge | dispute letters | 1 |
| nft-alpha | Base NFT signals | 1 |
| dispatch | NL intent router | 1 |
| contract-eye | contract risk analysis | 1 |
| briefsnap | document AI | 4 |
| sentry-forge | collection-notice defense | 1 |
| FREE — settlement-collector | telemetry & proof, no payment | 3 |

## Verify the contract yourself

```bash
# free
curl -s https://settlement-collector.fly.dev/health
# paid — returns 402 + challenge (free to fetch)
curl -s -D - -o /dev/null -X POST https://dispatch-x402.fly.dev/dispatch \
  -H 'Content-Type: application/json' -d '{"intent":"hello"}'
```

Collection is regenerated from the fleet's live behavior; see
[raen-api-docs](https://raen-api-docs.vercel.app/) for the full OpenAPI spec.

Royal Agentic Enterprises (RAEN) · ops@royalruby.io · Information only, not legal or financial advice.
