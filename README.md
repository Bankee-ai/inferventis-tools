# Inferventis MCP Server

**20 tools for financial data, real-time news, and web content — live on Cloud Run.**

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

### Currency & FX
| Tool | Description |
|------|-------------|
| `currency_convert` | Real-time FX conversion via Frankfurter API |
| `fx_converter` | Multi-source FX with rate comparison |

### Stocks & Markets
| Tool | Description |
|------|-------------|
| `finnhub_stock_quote` | Live stock quotes via Finnhub |
| `stock_tool` | Stock data with intelligent routing |

### Crypto
| Tool | Description |
|------|-------------|
| `crypto_price` | Live crypto prices via CoinGecko |
| `crypto_price_basic` | Lightweight crypto price lookup |

### News & Web
| Tool | Description |
|------|-------------|
| `news_headlines` | Real-time headlines from BBC & Guardian across 9 topic categories |
| `url_reader` | Fetch any public URL and return clean, readable text |

### Financial Calculators
| Tool | Description |
|------|-------------|
| `financial_calculator` | Compound interest, loan payments, ROI, NPV, IRR |
| `financial_calculator_basic` | Lightweight financial maths |

### Payments & Banking
| Tool | Description |
|------|-------------|
| `payment_tool` | Stripe payment processing |
| `open_banking_transactions` | Bank transaction data (Open Banking) |

### Utilities
| Tool | Description |
|------|-------------|
| `tool_finder` | Semantic search across all available tools |

## Payment Modes

**x402 micropayments (recommended for agents):**  
No account. Agent sends `$0.001 USDC` on Base per call, verified on-chain.  
Endpoint: `/mcp-pay`

**API key (for humans / Stripe billing):**  
Contact for an API key. Standard metered billing via Stripe.  
Endpoint: `/mcp` with `x-api-key: <key>`

## Connection Details

| Property | Value |
|----------|-------|
| Protocol | MCP Streamable HTTP |
| Base URL | `https://mcp-server-295985738387.europe-west1.run.app` |
| MCP endpoint (x402) | `/mcp-pay` |
| MCP endpoint (API key) | `/mcp` |
| Region | `europe-west1` (Belgium) |

## Status

Live on Google Cloud Run. Uptime monitored. See the [MCP Registry listing](https://registry.modelcontextprotocol.io) for verified status.
