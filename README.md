# getwowlink MCP server

Check how your links look when shared — on X, LinkedIn, Facebook, Telegram, WhatsApp and Slack — right from your
coding agent, and see exactly which Open Graph and Twitter card tags to fix. Checking is free, no account. Your agent
can also have branded OG images designed for every page (free getwowlink account).

**Address:** `https://mcp.getwowlink.com` (Streamable HTTP)
**Page:** https://www.getwowlink.com/mcp

## Install

**Claude Code**

```bash
claude mcp add --transport http getwowlink https://mcp.getwowlink.com
```

**Cursor** — `~/.cursor/mcp.json`

```json
{ "mcpServers": { "getwowlink": { "url": "https://mcp.getwowlink.com" } } }
```

**Codex** — `~/.codex/config.toml`

```toml
[mcp_servers.getwowlink]
url = "https://mcp.getwowlink.com"
```

**VS Code**

```bash
code --add-mcp '{"name":"getwowlink","type":"http","url":"https://mcp.getwowlink.com"}'
```

**Clients that only run local servers** (stdio):

```json
{ "mcpServers": { "getwowlink": { "command": "npx", "args": ["-y", "mcp-remote", "https://mcp.getwowlink.com"] } } }
```

## Tools

| Tool | What it does |
| --- | --- |
| `check_link_preview` | Scores how a page looks when shared on X, LinkedIn, Facebook, Telegram, WhatsApp and Slack, and lists the og: and twitter: tags to fix. |
| `check_site_previews` | Checks up to 50 pages from the sitemap: which have no image, share one image, or are broken. Call again with `check_id` until it's done. |
| `create_previews` | Creates branded Open Graph image designs for a site with AI and returns a link where the person picks one, tweaks it and publishes. Needs a free getwowlink account. |
| `wait_for_design` | Waits until the person has picked and published a design, then says what to install. |
| `get_install_instructions` | The og:image and twitter:image tags for every page, with the image URL pattern for this site. |
| `verify_install` | Checks live pages: exactly one og:image, served by getwowlink, and whether crawlers already fetch the images. |

Every result links a visual report on getwowlink.com. Limits: 30 page checks per 10 minutes and 5 site checks per hour
per client.

## Sign-in

The design tools need a free getwowlink account: your client opens a browser to sign in and allow access the first time
(OAuth). Checking previews needs no account.

## Agent Skill

[`skills/og-previews/SKILL.md`](skills/og-previews/SKILL.md) teaches an agent when to check link previews, how to fix
the tags by hand, and how to use these tools. It works without the MCP server too (it falls back to the public API).

Install it into Claude Code, Cursor, Codex and other agents:

```bash
npx skills add getwowlink/mcp
```

## Branded OG images for every page

getwowlink also designs an Open Graph image template from your site's colors and logo and renders an image for every
page: https://www.getwowlink.com
