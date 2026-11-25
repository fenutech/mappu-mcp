# Mappu MCP server

<img src="logo.png" alt="Mappu" width="96" align="right">

[Mappu](https://www.mappu.ai) is a travel app: an AI trip planner that puts every day of a trip on a map, more than 1,000 free audio guides to landmarks in eight languages, and self-guided walks. This repository holds the public configuration for Mappu's remote **MCP server**, so assistants and agents can use Mappu directly.

- **Endpoint:** `https://api.mappu.ai/mcp`
- **Transport:** Streamable HTTP
- **Authentication:** none. No account, no API key.
- **Registry:** listed in the official MCP Registry as `ai.mappu/public-travel`.
- **Languages:** English, Spanish, French, German, Italian, Portuguese, Japanese and Traditional Chinese.

The Mappu service itself is a Fenutech product and isn't open source. This repository only contains configuration and documentation.

## Tools

| Tool | What it does | Read-only |
|---|---|---|
| `mappu_search_public_travel` | Search published Mappu pages by topic and language: audio guides, walking tours, example itineraries, planning guides | yes |
| `mappu_read_public_page` | Read the text of a published Mappu page (an audio guide or a walk) in bounded windows | yes |
| `mappu_find_walks` | Find self-guided Mappu walking tours for a city, neighbourhood or landmark | yes |
| `mappu_get_audio_guide` | Look up a published Mappu audio guide to a landmark or place | yes |
| `mappu_get_walk_links` | Get the links for taking a Mappu walk, for a walk or for the walks at a city or landmark | yes |
| `mappu_get_trip_planning_guide` | Reference for the format of a plan saved with `mappu_save_trip_plan` | yes |
| `mappu_save_trip_plan` | Save a trip plan made with the traveler into Mappu as a day-by-day itinerary on a map, which they can open and keep | no |

## Connect

**Claude Code**

```bash
claude mcp add --transport http mappu https://api.mappu.ai/mcp
```

**Claude (web and desktop):** add a custom connector with the URL `https://api.mappu.ai/mcp`. A ready-made plugin, with skills for trip handoff, walks and public travel content, is in [`claude-plugin/`](claude-plugin/).

**ChatGPT:** add Mappu from its listing; current steps are at <https://www.mappu.ai/assistants>.

**Gemini CLI**

```bash
gemini extensions install https://github.com/fenutech/mappu-mcp
```

**Cline:** see [`llms-install.md`](llms-install.md) (use `"type": "streamableHttp"`).

**Cursor, VS Code and other MCP clients**

```json
{
  "mcpServers": {
    "mappu": { "url": "https://api.mappu.ai/mcp" }
  }
}
```

## Files

- [`server.json`](server.json): the MCP Registry entry (`ai.mappu/public-travel`).
- [`gemini-extension.json`](gemini-extension.json): the Gemini CLI extension manifest.
- [`claude-plugin/`](claude-plugin/): the Claude plugin, with its MCP config and skills.

## Privacy and terms

All tools except `mappu_save_trip_plan` only read public Mappu pages. Saving a plan creates an itinerary the traveler can open in Mappu.

- Privacy policy: <https://www.mappu.ai/privacy>
- Terms: <https://www.mappu.ai/terms>
- More about Mappu in assistants: <https://www.mappu.ai/assistants>

## Licence

The configuration and documentation in this repository are MIT-licensed. Mappu and the Mappu service are © Fenutech.
