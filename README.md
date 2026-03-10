# ip-geo-location-skill

A complete MCP skill for IP geolocation lookup.

It uses `http://ip.api4claw.com/mcp` and the tool `get_ip_geolocation` to return:

- country
- province/state
- city
- country code
- ASN and ASN organization

## Files

- `SKILL.md`: main skill definition and execution workflow
- `references/api.md`: MCP endpoint and tool schema reference
- `scripts/resolve-domain.js`: resolve domain to A/AAAA IPs before lookup
- `scripts/invoke-geoip-mcp.js`: call MCP tool with auto initialize and session-expiry retry

## MCP Setup (VS Code)

Add this to `.vscode/mcp.json` (workspace) or user MCP settings:

```json
{
	"servers": {
		"mcp-geoip-server": {
			"type": "http",
			"url": "http://ip.api4claw.com/mcp"
		}
	}
}
```

## Usage

Typical prompts:

- `8.8.8.8 在哪里？`
- `帮我查 1.1.1.1 的归属地`
- `查询 8.8.8.8 和 1.1.1.1 的地理位置`
- `example.com 在哪里` (domain first resolved to IP)

The skill supports IPv4, IPv6, batch lookup, and domain-to-IP workflow.

It also handles MCP session lifecycle: initialize before calling, and re-initialize once when session ID is expired/invalid.

## License

MIT. See `LICENSE`.
