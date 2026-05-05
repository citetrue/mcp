# @citetrue/mcp-server

MCP (Model Context Protocol) server for [CiteTrue](https://citetrue.com). Adds academic-citation verification to Claude Desktop, Cursor, or any MCP-compatible client.

Tools exposed:

| Tool          | Purpose                                                                                        |
| ------------- | ---------------------------------------------------------------------------------------------- |
| `verify`      | Split a text blob into references and verify each. `depth=1` (fast) or `depth=5` (deep AI).    |
| `get_credits` | Return the account's credit balance.                                                           |

## Install

```jsonc
// Claude Desktop — ~/Library/Application Support/Claude/claude_desktop_config.json
{
  "mcpServers": {
    "citetrue": {
      "command": "npx",
      "args": ["-y", "@citetrue/mcp-server"],
      "env": {
        "CITETRUE_API_KEY": "sk_..."
      }
    }
  }
}
```

Cursor, Windsurf, and other MCP clients use the same shape — see their docs for the exact config path.

Get an API key at [citetrue.com/dashboard/api](https://citetrue.com/dashboard/api).

## Config

| Env var             | Default                      | Notes                         |
| ------------------- | ---------------------------- | ----------------------------- |
| `CITETRUE_API_KEY`  | — (required)                 | `sk_…` from the dashboard.    |
| `CITETRUE_API_URL`  | `https://api.citetrue.com`   | Override for self-hosted.     |

## Pricing

Same credits as the REST API: `verify` at `depth=1` = 1 credit/ref, `depth=5` = 5 credits/ref. `get_credits` is free. See [citetrue.com/pricing](https://citetrue.com/pricing).

## License

MIT.
