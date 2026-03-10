---
name: ip-geo-location
description: Query geographic location information based on an IP address using the ip.api4claw.com MCP service. Use when the user wants to look up where an IP address is located, including country, region, city, ISP, timezone, and coordinates.
metadata:
  {
    "openclaw":
      {
        "emoji": "🌍",
        "requires": { "anyBins": ["mcporter", "npx"] },
        "install":
          [
            {
              "id": "node",
              "kind": "node",
              "package": "mcporter",
              "bins": ["mcporter"],
              "label": "Install mcporter (node)",
            },
          ],
      },
  }
---

# IP Geo Location

Query geographic location information for any IP address using the [ip.api4claw.com](http://ip.api4claw.com) MCP service.

## MCP Server

The MCP server URL is: `http://ip.api4claw.com/mcp`

When using `mcporter`, provide the endpoint without the `http://` scheme: `ip.api4claw.com/mcp`

No authentication or environment variables are required.

## List Available Tools

```shell
npx -y mcporter list 'ip.api4claw.com/mcp' --all-parameters
```

## Query IP Location

Use `mcporter call` to look up the geographic location of an IP address:

```shell
# Look up a specific IP address
npx -y mcporter call 'ip.api4claw.com/mcp.<tool_name>' ip:"<ip_address>"
```

> **Tip:** Run the list command above first to discover the exact tool name and parameters provided by the server.

## Workflow

1. **Discover tools**: Run `mcporter list 'ip.api4claw.com/mcp' --all-parameters` to see available tools and their parameters.
2. **Query location**: Call the appropriate tool with the target IP address.
3. **Present results**: Display the returned location data (country, region, city, ISP, coordinates, timezone, etc.) in a clear, readable format.

## Example Usage

```shell
# Discover available tools
npx -y mcporter list 'ip.api4claw.com/mcp' --all-parameters

# Query location for an IP (replace <tool_name> with actual tool name from list)
npx -y mcporter call 'ip.api4claw.com/mcp.<tool_name>' ip:"8.8.8.8"
```

## About `mcporter`

To improve compatibility, use `npx -y mcporter` instead of `mcporter` when executing commands.
