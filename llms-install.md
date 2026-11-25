# Installing the Mappu MCP server

Mappu's MCP server is hosted. There is nothing to download, build or run locally, and it needs no API key or account.

- **Endpoint:** `https://api.mappu.ai/mcp`
- **Transport:** Streamable HTTP
- **Authentication:** none

## Cline

Add this to `cline_mcp_settings.json` (MCP Servers → Configure → Configure MCP Servers):

```json
{
  "mcpServers": {
    "mappu": {
      "type": "streamableHttp",
      "url": "https://api.mappu.ai/mcp",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

Set `"type": "streamableHttp"` explicitly; without it, Cline falls back to the legacy SSE transport.

## Other MCP clients

Any client that supports remote Streamable HTTP servers can use the same URL, for example:

```json
{
  "mcpServers": {
    "mappu": { "url": "https://api.mappu.ai/mcp" }
  }
}
```

## Check that it works

Ask: "Find a free Mappu audio guide for the Colosseum." The client should call `mappu_get_audio_guide` or `mappu_search_public_travel` and return a link to the guide on www.mappu.ai.

All tools except `mappu_save_trip_plan` are read-only. Saving a plan creates a draft itinerary the traveler can open in Mappu.
