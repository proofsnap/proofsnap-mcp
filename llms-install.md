# Installing the ProofSnap MCP server

ProofSnap is a hosted remote MCP server. Nothing needs to be installed, built or run locally, and no API key goes into the configuration.

## Configuration

Add this entry to the MCP settings (for Cline: `cline_mcp_settings.json`):

```json
{
  "mcpServers": {
    "proofsnap": {
      "type": "streamableHttp",
      "url": "https://mcp.getproofsnap.com/mcp"
    }
  }
}
```

## Sign-in

The server uses OAuth 2.1 with PKCE and Dynamic Client Registration. On the first connection, a ProofSnap sign-in page opens in the browser. The user signs in with a ProofSnap API account (created at https://app.getproofsnap.com/, separate from the ProofSnap browser extension), chooses "Read only" or "Read and create" and clicks Allow.

Every new account includes a sandbox of 50 watermarked test captures that are not billed.

## Check

After sign-in, the server lists its tools. Ask: "Which ProofSnap account are you connected to?" (tool `whoami`).

Documentation: https://getproofsnap.com/api/mcp.html
