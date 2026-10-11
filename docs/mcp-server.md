# MCP server

Junction can run a [Model Context Protocol](https://modelcontextprotocol.io) server, so AI tools such as Claude Desktop, Claude Code or Cursor can browse your databases and run queries **through Junction** — using the connections you already have, with Junction's safety rails.

## What it exposes

The server is **read-only**, always:

- list connections and databases;
- list tables, columns and relations;
- run `SELECT` queries.

No writes, no DDL, no access to your stored credentials.

## Turn it on

1. **Settings → MCP server → Enable.**
2. Junction listens on `http://127.0.0.1:3100/mcp` (change the port if 3100 is taken).
3. Copy the **bearer token** shown in Settings.

The server only listens on `127.0.0.1` — other machines on your network can't reach it. A new token is generated every time the server starts and is never written to disk, so restarting Junction invalidates the old one.

The **MCP** badge in the toolbar shows whether the server is running; click it to jump to the setting.

## Connect a client

### Claude Desktop, Cursor and other JSON-configured clients

```json
{
  "mcpServers": {
    "junction": {
      "url": "http://127.0.0.1:3100/mcp",
      "headers": { "Authorization": "Bearer <token>" }
    }
  }
}
```

### Claude Code

```bash
claude mcp add --transport http junction http://127.0.0.1:3100/mcp --header "Authorization: Bearer <token>"
```

Replace `<token>` with the token from Settings — and update it after Junction restarts.

## Troubleshooting

| Symptom | Fix |
|---|---|
| `401 Unauthorized` | The token changed (Junction restarted). Copy the new one from Settings. |
| Connection refused | The server isn't running — check the toolbar badge, or the port is different from your config. |
| Port already in use | Pick another port in Settings and update your client config. |
