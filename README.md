# Inferventis MCP Server

**9 production tools for financial data, real-time news, and web content — live on Cloud Run.**

Connect any MCP-compatible agent in seconds. No account needed for x402 micropayment mode — agents pay **$0.001 USDC per call** autonomously on Base network.

## Quick Connect

```json
{
  "mcpServers": {
    "inferventis": {
      "type": "streamable-http",
      "url": "https://mcp-server-295985738387.europe-west1.run.app/mcp-pay"
    }
  }
}
```

## Tools

All manifests are written to TDQS A standard (≥ 4.0/5.0) for reliable agent selection.

### Free — no API key required

| Tool | Description |
|------|-------------|
| `currency_convert` | Live FX conversion via Frankfurter (ECB data). 30+ currencies. |
| `crypto_price` | Live cryptocurrency prices via CoinGecko. 10,000+ coins. |
| `financial_calculator` | Compound interest, loan payments, ROI, present/future value, break-even. No external API. |
| `news_headlines` | Real-time headlines from BBC News and The Guardian across 9 topic categories. |
| `url_reader` | Fetch any public URL and return clean, readable plain text. |
| `tool_finder` | Semantic search across all available tools — call this first if unsure which tool to use. |

### Requires API key (pass via tool arguments)

| Tool | Description | Key needed |
|------|-------------|------------|
| `finnhub_stock_quote` | Live stock quotes — price, intraday high/low, % change, sector. | `FINNHUB_API_KEY` |
| `open_banking_transactions` | Bank account balances and transactions via TrueLayer PSD2. | `TRUELAYER_ACCESS_TOKEN` |
| `stripe_payments` | Live Stripe data — payments, failed charges, customers, subscriptions. | `STRIPE_SECRET_KEY` |

## Payment Modes

**x402 micropayments (recommended for autonomous agents):**
No account. Agent sends `$0.001 USDC` on Base per call, verified on-chain.
Endpoint: `/mcp-pay`

**API key (for developers / Stripe billing):**
Standard metered billing via Stripe.
Endpoint: `/mcp` with `x-api-key: <key>`

## Connection Details

| Property | Value |
|----------|-------|
| Protocol | MCP Streamable HTTP |
| Base URL | `https://mcp-server-295985738387.europe-west1.run.app` |
| x402 endpoint | `/mcp-pay` |
| API key endpoint | `/mcp` |
| Region | `europe-west1` (Belgium) |
| MCP Registry | `io.github.jonathanpchapman/inferventis` |

## Listings

| Platform | Status |
|----------|--------|
| MCP Registry | ✅ Live |
| Smithery | ✅ Indexed |
| Glama | ✅ Indexed |
| findmcpservers.com | ✅ Submitted |
| mcpserverhub.net | ✅ Confirmed |
