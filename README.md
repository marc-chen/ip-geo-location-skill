# ip-geo-location-skill

> Release note (2026-03-11): MCP endpoint upgraded to `https://ip.api4claw.com/mcp`.

## English

A production-ready MCP skill for IP geolocation lookup.

- Endpoint: `https://ip.api4claw.com/mcp`
- Tool: `get_ip_geolocation`
- Supports: IPv4, IPv6, batch lookup, and domain-to-IP resolution
- Session handling: auto `initialize`, and auto re-initialize + retry when `Mcp-Session-Id` expires

### Security Notes

- This skill sends queried IP addresses to an external MCP endpoint.
- Current default endpoint is `https://ip.api4claw.com/mcp` (encrypted in transit).
- Script implementation is pinned to this HTTPS endpoint and does not allow arbitrary endpoint override.
- Private/internal IP ranges are blocked and will not be forwarded to the external endpoint.
- Script timeout is fixed at 15s (no runtime env override).

### Install

```bash
npx skills add marc-chen/ip-geo-location-skill
```

### Verify

Try prompts like:

- `Where is 8.8.8.8?`
- `Lookup geolocation for 8.8.8.8 and 1.1.1.1`
- `Where is example.com?`

## 中文说明 | Chinese

一个用于 IP 地理位置查询的 MCP Skill，适用于中文用户场景。

- MCP 接口地址: `https://ip.api4claw.com/mcp`
- 调用工具: `get_ip_geolocation`
- 支持能力: IPv4、IPv6、批量查询、域名转 IP 后查询
- 会话机制: 自动 `initialize` 获取会话 ID；当 `Mcp-Session-Id` 过期/失效时自动重新初始化并重试

### 安全提示 | Security Notes

- 查询的 IP 会发送到外部 MCP 服务。
- 当前默认端点为 `https://ip.api4claw.com/mcp`（传输加密）。
- 脚本实现固定使用该 HTTPS 端点，不允许任意地址覆盖。
- 私有/内网 IP 段会被拦截，不会转发到外部服务。
- 脚本超时固定为 15 秒（不使用运行时环境变量覆盖）。

### 安装 | Install

#### 方式一：skills.sh

```bash
npx skills add marc-chen/ip-geo-location-skill
```

#### 方式二：手动安装

克隆本仓库后，将该 Skill 目录放到你的 Agent skills 目录中。

### 入口文件 | Skill Entry

- `SKILL.md`

### 脚本说明 | Scripts

- `scripts/invoke-geoip-mcp.js`: MCP 调用封装（含会话初始化与会话过期自动重试）
- `scripts/resolve-domain.js`: 域名解析为 A/AAAA 记录

### 使用示例 | Examples

- `8.8.8.8 在哪里？`
- `查询 8.8.8.8 和 1.1.1.1 的地理位置`
- `example.com 在哪里`

## License

MIT. See `LICENSE`.
