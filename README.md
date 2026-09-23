# AgentBroker MCP Skill

Live GLEIF+SEC company verification, OFAC/EU/UK sanctions screening, and cross-border trade-restriction mapping  -  as deterministic MCP tool calls. 11 utility tools free (no key, unmetered). Premium data tools free up to a daily limit, then $0.02/call.

**Endpoint:** `https://hatchloop.dev/mcp/agent-broker`  
**Homepage:** https://hatchloop.dev/agent-broker/  
**Protocol:** MCP streamable-HTTP (2025-03-26)  
**Tools:** 23 total  -  11 utility tools (no key, unmetered free), 3 premium data tools (free up to daily limit, then $0.02/call), 2 tools free but requiring a key, 7 write tools (priced per call: $0.02-$0.2, free email-verified key for 100 ops/day, or credits from $9/1,000 at https://hatchloop.dev/pricing)

---

## Why install this

11 utility tools are unconditionally free (no key, no daily limit):

- **`check_compliance`**  -  TCPA/GDPR/CASL/PDPL and 18 more jurisdictions. Free pre-flight before any outbound message.
- **`find_business`, `verify_business`**  -  Search and confirm curated, transactable SMBs.
- **`check_booking_link`, `preview_cost`, `get_status`, `get_outcome`, `self_test`**  -  Utility tools for safe, predictable agent flows.
- **`check_quota`**  -  See the caller's current quota state: calls used today, calls remaining, daily limit, and tier.
- **`mint_key`**  -  Self-serve API key issuance for an autonomous agent with no email inbox.
- **`lookup_us_contracts`**  -  Search US federal contract awards by company name via the free USASpending.gov API.

3 premium data tools hit live primary sources and are free up to a daily limit:

- **`verify_company_record`**  -  GLEIF LEI database + SEC EDGAR. Real registry data, not hallucinated company info. Free up to 500/day (verified key) or 100/day (anonymous).
- **`screen_sanctions`**  -  OFAC SDN + the EU Consolidated list + the UK Sanctions List. Free up to 500/day (verified key) or 100/day (anonymous).
- **`map_trade_restriction`**  -  OFAC country embargoes + US export-control Entity List, with official tariff-lookup links. No fabricated rates. Free up to 500/day (verified key) or 100/day (anonymous).

Beyond the daily limit: $0.02/call via credits. Crypto payment is not offered.

2 tools are free to call but require an `X-Agent-Identity` key: **`get_conversation`** (read a conversation thread you started) and **`import_booking_url`** (parse a public booking URL into a callable business record).

---

## Install

### Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "agentbroker": {
      "command": "npx",
      "args": ["-y", "agentbroker-mcp"],
      "env": {}
    }
  }
}
```

Or point directly at the hosted endpoint (no local install):

```json
{
  "mcpServers": {
    "agentbroker": {
      "url": "https://hatchloop.dev/mcp/agent-broker",
      "transport": "streamable-http"
    }
  }
}
```

For write tools (send_message, schedule_appointment, call_business, etc.), add your key:

```json
{
  "mcpServers": {
    "agentbroker": {
      "url": "https://hatchloop.dev/mcp/agent-broker",
      "transport": "streamable-http",
      "headers": {
        "X-Agent-Identity": "Bearer YOUR_KEY_HERE"
      }
    }
  }
}
```

Get a free key (100 write ops/day) at https://hatchloop.dev/agent-broker/

---

### Cursor

Add to `.cursor/mcp.json` in your project, or `~/.cursor/mcp.json` globally:

```json
{
  "mcpServers": {
    "agentbroker": {
      "url": "https://hatchloop.dev/mcp/agent-broker",
      "transport": "streamable-http"
    }
  }
}
```

With write-tool key:

```json
{
  "mcpServers": {
    "agentbroker": {
      "url": "https://hatchloop.dev/mcp/agent-broker",
      "transport": "streamable-http",
      "headers": {
        "X-Agent-Identity": "Bearer YOUR_KEY_HERE"
      }
    }
  }
}
```

---

### Cline (VS Code Extension)

Open Cline settings -> MCP Servers -> Add Server -> Remote (SSE/HTTP):

- **URL:** `https://hatchloop.dev/mcp/agent-broker`
- **Transport:** Streamable HTTP

Or add to your Cline MCP config file directly:

```json
{
  "mcpServers": {
    "agentbroker": {
      "url": "https://hatchloop.dev/mcp/agent-broker",
      "transport": "streamable-http"
    }
  }
}
```

---

### Windsurf

Add to `~/.windsurf/mcp.json`:

```json
{
  "mcpServers": {
    "agentbroker": {
      "serverUrl": "https://hatchloop.dev/mcp/agent-broker"
    }
  }
}
```

With key:

```json
{
  "mcpServers": {
    "agentbroker": {
      "serverUrl": "https://hatchloop.dev/mcp/agent-broker",
      "headers": {
        "X-Agent-Identity": "Bearer YOUR_KEY_HERE"
      }
    }
  }
}
```

---

### VS Code (GitHub Copilot Agent Mode)

Add to `.vscode/mcp.json` in your workspace:

```json
{
  "servers": {
    "agentbroker": {
      "url": "https://hatchloop.dev/mcp/agent-broker",
      "type": "http"
    }
  }
}
```

Or in your user `settings.json`:

```json
{
  "mcp": {
    "servers": {
      "agentbroker": {
        "url": "https://hatchloop.dev/mcp/agent-broker",
        "type": "http"
      }
    }
  }
}
```

---

## Pricing

| Tier | What you get |
|---|---|
| Free (no key) | 11 utility tools: `check_compliance`, `find_business`, `verify_business`, `check_booking_link`, `preview_cost`, `get_status`, `get_outcome`, `self_test`, `check_quota`, `lookup_us_contracts`, `mint_key`  -  no key, unmetered |
| Free (no key, daily limit) | 3 premium data tools: `verify_company_record`, `screen_sanctions`, `map_trade_restriction`  -  100 calls/day anonymous, 500 calls/day with a free email-verified key |
| Free (requires key) | 2 tools: `get_conversation`, `import_booking_url`  -  free to call, but need an `X-Agent-Identity` key |
| Free key | + 7 write tools, 100 ops/day. Email-verified at https://hatchloop.dev/agent-broker/ |
| Credits | Premium data tools beyond daily limit: $0.02/call. Write tools priced per call ($0.02-$0.2): `send_message` from $0.02, `capture_lead` $0.05, `schedule_appointment` from $0.15, `send_transactional_confirmation` $0.02, `handle_inbound` $0.03, `escalate_to_human` $0.2, `call_business` $0.2  -  or buy credits: Starter $9/1,000, Growth $29/3,500, Scale $99/13,000. [Buy credits](https://hatchloop.dev/pricing). Crypto payment is not offered. |

---

## License

MIT  -  see [LICENSE](./LICENSE)
