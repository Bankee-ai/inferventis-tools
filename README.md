<p align="center">
  <img src="https://raw.githubusercontent.com/Bankee-ai/inferventis/main/public/logo.png" alt="Inferventis" width="360">
</p>

# Inferventis MCP Server

**20 financial tools — live on Google Cloud Run. Zero install. Connect in 30 seconds.**

A production-ready [Model Context Protocol](https://modelcontextprotocol.io) server any AI agent can call over Streamable HTTP. Real-time stocks, crypto, FX, Open Banking, Stripe, news, and web reading — all in one endpoint.

## Quick Connect

```json
{
  "mcpServers": {
    "inferventis": {
      "type": "streamableHttp",
      "url": "https://mcp-server-295985738387.europe-west1.run.app/mcp"
    }
  }
}
```

Or via Claude Code:
```bash
claude mcp add inferventis --transport http https://mcp-server-295985738387.europe-west1.run.app/mcp
```

## Tools

All manifests are written to TDQS A standard (≥ 4.0/5.0) for reliable agent tool selection.

### Free — no API key required

| Tool | Manifest | Description |
|------|----------|-------------|
| `platform_tool_finder` | `tool_finder.json` | Semantic search across all tools — call this first if unsure which tool to use |
| `web_news_headlines` | `news_headlines.json` | Real-time headlines from BBC News + The Guardian. 9 topic categories, keyword filter |
| `web_url_reader` | `url_reader.json` | Fetch any public URL and return clean readable plain text |

### Standard — no API key required (live data)

| Tool | Manifest | Description |
|------|----------|-------------|
| `currency_convert` | `currency_convert.json` | Live FX via Frankfurter (ECB). 33+ currencies |
| `currency_convert_lite` | `currency_convert_basic.json` | Lightweight FX conversion, minimal payload |
| `currency_convert_open` | `real_wesbos_currency.json` | FX conversion via open exchange rate data |
| `currency_fx_lite` | `fx_converter.json` | Mid-market FX conversion, low-latency |
| `currency_rates` | `real_frankfurter_currency.json` | Live and historical exchange rates from Frankfurter API |
| `financial_calculator` | `financial_calculator.json` | Compound interest, loan payments, ROI, PV/FV, break-even. No external API |
| `financial_calculator_lite` | `financial_calculator_basic.json` | Lightweight financial calculator |
| `crypto_price` | `crypto_price.json` | Live crypto prices via CoinGecko. 10,000+ coins |
| `crypto_price_lite` | `crypto_price_basic.json` | Spot price + 24h change. Minimal payload |
| `crypto_fx_rates` | `real_coinapi_fx.json` | Converts amounts between any crypto/fiat pair |
| `stock_quote` | `finnhub_stock_quote.json` | Real-time stock price, high/low, % change via Finnhub |
| `stock_price_lite` | `stock_tool.json` | Current trading price for any ticker. Minimal payload |

### Premium — caller-supplied API key required

| Tool | Manifest | Description | Key needed |
|------|----------|-------------|------------|
| `open_banking_transactions` | `open_banking_transactions.json` | Bank account balances + transactions via TrueLayer (PSD2) | `TRUELAYER_ACCESS_TOKEN` |
| `bank_accounts` | `bank_data.json` | Bank account details + recent transaction history | `TRUELAYER_ACCESS_TOKEN` |
| `stripe_payments` | `stripe_payments.json` | Live Stripe data — payments, customers, subscriptions | `STRIPE_SECRET_KEY` |
| `stripe_payment_records` | `payment_tool.json` | Payment and charge records from a Stripe merchant account | `STRIPE_SECRET_KEY` |

## Connection Details

| Property | Value |
|----------|-------|
| Protocol | MCP Streamable HTTP |
| Base URL | `https://mcp-server-295985738387.europe-west1.run.app` |
| Endpoint | `/mcp` (API key) · `/mcp-pay` (x402 USDC micropayments) |
| Region | `europe-west1` (Belgium) |
| MCP Registry | `io.github.bankee-ai/inferventis-tools` |

## Authentication

**API key (developer/Stripe billing):**
```
x-api-key: your_key_here
```
Test key: `key_test_abc123`

**x402 micropayments (autonomous agents, no account needed):**
Agents pay `$0.001 USDC` on Base per call, verified on-chain. Use endpoint `/mcp-pay`.

## Aggregator Listings

| Platform | Status |
|----------|--------|
| Glama | ✅ Auto-indexed via `glama.json` |
| Smithery | ✅ Auto-indexed via `smithery.yaml` |
| PulseMCP | ✅ Auto-indexed |
| punkpeye/awesome-mcp-servers | ✅ PR #5862 |
| MCP Registry | ✅ Live |
| mcp.so | ✅ Under review |
| mcpservers.org | ✅ Submitted |
| mcpmarket.com | ✅ Submitted |
| mcp.aibase.com | ✅ Submitted |
| LobeHub | ✅ Issue #14430 |

## Platform Info

This is the **public listing repo** for Inferventis. Manifests and config files only — no implementation code.

- **Private platform repo:** `Bankee-ai/inferventis` (Cloud Run, TypeScript, tool implementations)
- **Website:** [inferventis.ai](https://inferventis.ai)
- **Dashboard:** [/dashboard](https://mcp-server-295985738387.europe-west1.run.app/dashboard)
- **Developer programme:** [/developers](https://mcp-server-295985738387.europe-west1.run.app/developers) — list your tools, earn 70% of every call
