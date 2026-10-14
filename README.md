# Agent Memory plugin for Claude Code

Connects Claude Code to [Agent Memory](https://memory.empecta.com), a persistent,
multi-tenant memory layer for AI agents, over MCP. Your agent gets tools to remember
decisions, corrections and approved patterns, and to recall them in later sessions:
`add_memory`, `search_memory`, `get_memory`, `consolidate`, `curate_block` and
`list_procedures`.

## Install

In Claude Code:

```
/plugin marketplace add erkansezgin/agentmemory-claude-plugin
/plugin install agentmemory@agentmemory
```

Then set your API key (create one in the Agent Memory console) and restart Claude Code:

```bash
export AGENT_MEMORY_API_KEY=YOUR_API_KEY
```

## Configuration

| Variable | Required | Default |
|---|---|---|
| `AGENT_MEMORY_API_KEY` | yes | — |
| `AGENT_MEMORY_URL` | no | `https://memory.empecta.com/v1/mcp` |

Set `AGENT_MEMORY_URL` only when you run your own Agent Memory deployment, e.g.
`https://memory.example.internal/v1/mcp`.

## Without the plugin

The same server can be added directly:

```bash
claude mcp add --transport http agent-memory https://memory.empecta.com/v1/mcp \
  --header "Authorization: Bearer YOUR_API_KEY"
```

## Repository layout

```
.claude-plugin/marketplace.json        marketplace entry (name: agentmemory)
plugins/agentmemory/.claude-plugin/    plugin manifest
plugins/agentmemory/.mcp.json          MCP server definition
```
