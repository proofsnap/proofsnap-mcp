<p align="center"><img src="assets/logo.png" alt="ProofSnap" width="96" height="96"></p>

# ProofSnap MCP server

Preserve public web pages as signed, timestamped evidence packages from your AI assistant, then verify them, compare versions and monitor pages for changes.

ProofSnap is a hosted remote MCP server. ProofSnap's own servers load the page, not the assistant, and seal a full-page screenshot, the HTML, the page text, metadata and a chain of custody into a signed manifest of SHA-256 hashes with an OpenTimestamps (Bitcoin) proof. On request, an eIDAS qualified timestamp from Disig a.s., a qualified trust service provider on the EU Trusted List, is added.

- **Server URL:** `https://mcp.getproofsnap.com/mcp` (Streamable HTTP)
- **Sign-in:** OAuth 2.1 with PKCE, Client ID Metadata Documents and Dynamic Client Registration
- **Documentation and setup for every app:** https://getproofsnap.com/api/mcp.html
- **Official MCP Registry:** `com.getproofsnap/proofsnap`

A second public server, `com.getproofsnap/proofsnap-verify` at `https://mcp.getproofsnap.com/verify/mcp`, needs no sign-in and checks, by the SHA-256 of its manifest.json, whether ProofSnap's API or dashboard issued an evidence package.

This repository holds the connection files for the directories and apps listed below. The server itself is a hosted service; its code is not part of this repository.

## What you can do

- Capture one page, or up to 10 pages at once, as evidence
- List, open and verify stored captures
- Quote the sealed page text, with its hash checked against the signed manifest
- Compare two captures of the same page and seal the result as its own package
- Certify a file by its SHA-256 (the file stays on your device)
- Monitor a page at an interval, on a cron or when it changes
- On the Legal plans, create matters, add captures and export a matter as one ZIP with a chain of custody report

Example: *"Capture https://example.com as evidence."*

The connector cannot delete anything, change billing or API keys, or see your password.

## What you need

A ProofSnap API account with a confirmed email address, created at https://app.getproofsnap.com/. It is separate from the ProofSnap browser extension. Every new account includes a sandbox of 50 watermarked test captures that are not billed. Live captures count toward your plan; schedules need a paid plan; matters need a Legal plan; an eIDAS timestamp costs $1.99 per stamp. Before a costly request, ProofSnap returns the cost first and runs the request only after you confirm it. Plans: https://getproofsnap.com/api/index.html#pricing

## Connect

When you connect, sign in with your ProofSnap account and choose **Read only** or **Read and create**.

| App | How |
| --- | --- |
| Claude (web, desktop, mobile) | Settings > Connectors > Add custom connector, URL `https://mcp.getproofsnap.com/mcp` |
| Claude Code | `claude mcp add --transport http proofsnap https://mcp.getproofsnap.com/mcp` |
| ChatGPT | Settings > Apps & Connectors, add a custom app with the server URL (on some plans turn on developer mode under Advanced settings first) |
| Cursor | [Add to Cursor](https://cursor.com/en/install-mcp?name=proofsnap&config=eyJ1cmwiOiJodHRwczovL21jcC5nZXRwcm9vZnNuYXAuY29tL21jcCJ9) or use `mcp.json` from this repository |
| VS Code with GitHub Copilot | [Install in VS Code](https://vscode.dev/redirect/mcp/install?name=proofsnap&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.getproofsnap.com%2Fmcp%22%7D) or add to `.vscode/mcp.json` in your workspace: `{"servers":{"proofsnap":{"type":"http","url":"https://mcp.getproofsnap.com/mcp"}}}` |
| Codex CLI | `codex mcp add proofsnap --url https://mcp.getproofsnap.com/mcp` then `codex mcp login proofsnap` |
| Gemini CLI | `gemini extensions install https://github.com/proofsnap/proofsnap-mcp` or `gemini mcp add --transport http proofsnap https://mcp.getproofsnap.com/mcp` |
| Grok | grok.com/connectors > New Connector > Custom, URL `https://mcp.getproofsnap.com/mcp` |
| Mistral Vibe, Perplexity, n8n and other MCP apps | see https://getproofsnap.com/api/mcp.html |

Step-by-step instructions for each app: https://getproofsnap.com/api/mcp.html

## Files in this repository

| File | For |
| --- | --- |
| `server.json` | Official MCP Registry entry |
| `mcp.json`, `.cursor-plugin/plugin.json` | Cursor |
| `.mcp.json`, `.claude-plugin/plugin.json` | Claude Code plugin |
| `gemini-extension.json` | Gemini CLI extension |

## Support and security

- Support: support@getproofsnap.com
- Security reports: https://getproofsnap.com/.well-known/security.txt
- Privacy policy: https://getproofsnap.com/privacy.html
- Terms: https://getproofsnap.com/terms.html

## License

The files in this repository are released under the MIT License. The ProofSnap service is provided under its own terms.
