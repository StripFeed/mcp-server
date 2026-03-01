# StripFeed MCP Server

MCP server for [StripFeed](https://www.stripfeed.dev) - convert any URL to clean, token-efficient Markdown.

Works with Claude Code, Cursor, Windsurf, and any MCP-compatible client.

<a href="https://glama.ai/mcp/servers/@StripFeed/stripfeed-mcp-server">
  <img width="380" height="200" src="https://glama.ai/mcp/servers/@StripFeed/stripfeed-mcp-server/badge" alt="stripfeed-mcp-server MCP server" />
</a>

## Setup

### 1. Get your API key

Sign up at [stripfeed.dev](https://www.stripfeed.dev/dashboard/keys) and create an API key.

### 2. Install

#### Claude Code

```bash
claude mcp add stripfeed -- npx -y @stripfeed/mcp-server
```

Then set your API key:

```bash
export STRIPFEED_API_KEY=sf_live_your_key
```

Or add it to your shell profile (`~/.zshrc`, `~/.bashrc`).

#### Cursor / VS Code

Add to your MCP settings (`.cursor/mcp.json` or VS Code MCP config):

```json
{
  "mcpServers": {
    "stripfeed": {
      "command": "npx",
      "args": ["-y", "@stripfeed/mcp-server"],
      "env": {
        "STRIPFEED_API_KEY": "sf_live_your_key"
      }
    }
  }
}
```

#### Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "stripfeed": {
      "command": "npx",
      "args": ["-y", "@stripfeed/mcp-server"],
      "env": {
        "STRIPFEED_API_KEY": "sf_live_your_key"
      }
    }
  }
}
```

## Tools

### `fetch_url`

Convert a single URL to clean Markdown.

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| url | string | Yes | URL to fetch and convert |
| selector | string | No | CSS selector to extract specific elements |
| model | string | No | AI model ID for cost tracking |
| cache | boolean | No | Set to false to bypass cache |
| ttl | number | No | Cache TTL in seconds (default 3600, max 86400) |

**Example usage in Claude Code:**

> "Fetch https://react.dev/learn and summarize the key concepts"

> "Get the pricing table from https://stripe.com/pricing using selector '.pricing-table'"

### `batch_fetch`

Fetch multiple URLs in parallel (up to 10).

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| urls | string[] | Yes | Array of URLs to fetch (1-10) |
| model | string | No | AI model ID for cost tracking |

**Example usage in Claude Code:**

> "Fetch the React, Vue, and Svelte docs and compare their approaches to state management"

## Pricing

The MCP server uses your StripFeed API key. Usage counts toward your plan limits:

- **Free:** 200 requests/month, 1 API key
- **Pro:** 100K requests/month, unlimited keys ($19/mo)
- **Enterprise:** Unlimited

## Links

- [API Docs](https://www.stripfeed.dev/docs)
- [TypeScript SDK](https://www.npmjs.com/package/stripfeed)
- [Python SDK](https://pypi.org/project/stripfeed/)
- [GitHub](https://github.com/StripFeed/mcp-server)

## License

MIT