# First Monday MCP server

First Monday lists remote, English-language jobs and says, for each of 21 countries, whether a job can hire someone living there: open, probably open (with the reason) or not, quoting the words it stands on.

This repository holds the connection config and the MCP Registry entry for First Monday's **hosted** MCP server. The server itself is a hosted service and its source is not public. Use this repository's issues to report problems with the MCP server.

- **Server address:** `https://mcp.firstmonday.ai/mcp` (remote, Streamable HTTP)
- **Sign-in:** OAuth 2.1, with a free First Monday account created at the sign-in prompt (Google or a code by email). No API key.
- **Limit:** 100 tool calls a day per account.
- **Tools (all read-only):**
  - `search_jobs`: jobs open to one country, by words in the title or company, kind of work, pay, recency and other filters.
  - `get_job`: one job's requirements, reporting line, pay by country, and each country's verdict and words.
  - `list_countries`: the countries covered.
- It cannot apply for jobs or change anything.
- **Countries:** US, Canada, UK, Ireland, Germany, Netherlands, Belgium, Austria, Switzerland, Sweden, Denmark, Norway, Finland, Poland, Spain, Portugal, Australia, New Zealand, Mexico, Brazil, India.
- **MCP Registry:** `ai.firstmonday/jobs`

## Connect

Setup for each app is at https://docs.firstmonday.ai/mcp.

**Claude:** listed in Claude's connector directory (search for "First Monday" under Connectors).

**Claude Code**
```bash
claude mcp add --transport http first-monday https://mcp.firstmonday.ai/mcp
```

**Cursor** (`~/.cursor/mcp.json`) — see [`mcp.json`](mcp.json)
```json
{ "mcpServers": { "first-monday": { "url": "https://mcp.firstmonday.ai/mcp" } } }
```

**VS Code**
```bash
code --add-mcp '{"name":"first-monday","type":"http","url":"https://mcp.firstmonday.ai/mcp"}'
```

**Other apps:** add a remote MCP server with the address above. The app finds the sign-in by itself.

## Try asking
- Remote customer success jobs I can do from Canada, posted this week.
- Engineering jobs open to people in Germany that pay $150k a year or more.
- Does GitLab have a job I could do from the UK?

## Links
- Privacy: https://firstmonday.ai/privacy-policy
- Terms: https://firstmonday.ai/terms-and-conditions
- Security: https://firstmonday.ai/.well-known/security.txt
- Contact: contact@firstmonday.ai
- Weekly lists: https://github.com/firstmonday-ai/100-weekly-remote-jobs-by-country

The files in this repository are under the MIT license. The First Monday service is under its own terms.
