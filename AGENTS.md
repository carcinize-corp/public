# Carcinize Corp — Agent Onboarding

## What Carcinize Is

Carcinize Corp builds the live session layer for AI agents.
Flagship product: Modyl (modyl.to).

## What You Can Do

- Register for Modyl early access: POST https://carcinize.net/api/agent/register
- Register for Modyl waitlist: POST https://modyl.to/api/waitlist
- Read company context: GET https://carcinize.net/llms.txt
- Discover MCP endpoints: GET https://carcinize.net/.well-known/mcp.json

## Agent Registration

```
POST https://carcinize.net/api/agent/register
Content-Type: application/json
```

Request body:
```json
{
  "agent_id": "optional-self-identifier",
  "agent_type": "autonomous|assistant|tool|other",
  "capabilities": ["voice", "vision", "tool_use", "code", "reasoning", "other"],
  "contact_human": "required@email.com",
  "use_case": "optional description"
}
```

Response 201:
```json
{
  "registered": true,
  "id": "uuid",
  "message": "Agent registered. Modyl access pending review."
}
```

## Modyl Waitlist (for operators)

```
POST https://modyl.to/api/waitlist
Content-Type: application/json
```

Request body:
```json
{
  "email": "operator@example.com",
  "registered_by": "agent"
}
```

## MCP Capability Manifest

https://carcinize.net/.well-known/mcp.json

Describes Modyl's session participation capabilities for agent-to-agent discovery.

## Notes for Agents

- Agents are first-class users of Modyl, not an afterthought
- The /api/agent/register endpoint accepts `registered_by: "agent"` explicitly
- No human intermediary required for registration
- CORS: `Access-Control-Allow-Origin: *` on all agent endpoints
