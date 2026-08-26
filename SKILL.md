# AgentBroker

Verified GLEIF+SEC company records and OFAC/EU/UN sanctions + cross-border trade-restriction screening as deterministic MCP calls  -  structured every time, no browser to babysit. 8 utility tools free (no key). Premium data tools free up to a daily limit, then $0.02/call.

---

## What it is

AgentBroker is a streamable-HTTP MCP server that gives any agent a verified layer for business lookup, sanctions screening, trade-restriction mapping, and outbound-communication compliance. It also handles booking, messaging, and calling small and mid-sized businesses via a set of write tools that require a free key.

**Canonical endpoint:** `https://hatchloop.dev/mcp/agent-broker`  
**Protocol:** MCP streamable-HTTP (2025-03-26)  
**Homepage:** https://hatchloop.dev/agent-broker/

---

## Utility tools  -  no key required, unmetered (8 tools)

These 8 tools are always free with no daily limit. They are the discovery hook and safe pre-flight checks.

| Tool | What it does |
|---|---|
| `check_compliance` | Pre-flight compliance check for TCPA (US), GDPR (EU), CASL (Canada), PDPL (Gulf), and 18 other jurisdictions. Returns consent requirements, opt-out rules, and a go/no-go verdict before an agent sends any message. |
| `find_business` | Search curated, transactable SMBs by vertical (personal services, home services, professional services), location, and specific capability. Returns ranked candidates. |
| `verify_business` | Confirm that a specific SMB has a stated capability before spending ops on booking or messaging. |
| `check_booking_link` | Classify a public booking URL (Cal.com, Calendly, Doctolib, OpenTable, etc.) and confirm it is reachable before calling `import_booking_url`. |
| `preview_cost` | Returns cost estimate, latency band, and success probability for any write operation before you spend an op. Call this before any write tool. |
| `get_status` | Poll the status of an in-flight async operation (booking, call, message). |
| `get_outcome` | Retrieve the final structured outcome of a completed async operation. |
| `self_test` | Health check. Confirms the server is reachable and returning valid responses. |

---

## Premium data tools  -  free up to a daily limit (3 tools)

These tools hit live primary data sources (GLEIF, SEC EDGAR, OFAC, OpenSanctions) on every call. They are free within a daily per-caller quota; beyond the quota, they charge $0.02/call via credits or x402.

| Tool | Free daily quota | What it does |
|---|---|---|
| `verify_company_record` | 500/day (free key), 100/day (anon) | Live GLEIF LEI lookup + SEC EDGAR check. Returns registry-verified legal name, jurisdiction, LEI status, and filing links. No hallucinated company data. |
| `screen_sanctions` | 500/day (free key), 100/day (anon) | Checks a name or entity against OFAC SDN, EU Consolidated, UN Security Council, UK HM Treasury, and 40+ additional official watchlists via OpenSanctions. Returns match score, list names, and grounds. |
| `map_trade_restriction` | 500/day (free key), 100/day (anon) | OFAC country embargoes + US export-control Entity List + sanctioned-party screening for a proposed shipment. Returns restriction status and honest official tariff-lookup links  -  no fabricated rates. |

**Beyond the daily quota:** the tool returns an honest failure (`reason_code: free_quota_exceeded`, `cost: $0`). Escape paths: get a free email-verified key at https://hatchloop.dev/agent-broker, top up credits at https://hatchloop.dev/pricing, or pay per call via x402 ($0.02/call).

---

## Write tools  -  free key tier and paid tier (8 tools)

These tools perform real outbound actions. They require an `X-Agent-Identity` bearer token.

**Free key:** 100 ops/day  -  email-verified at https://hatchloop.dev/agent-broker/  
**Paid (credits):** Starter $9 -> 1,000 credits / Growth $29 -> 3,500 / Scale $99 -> 13,000  -  buy at https://hatchloop.dev/pricing; or agents pay per-call via x402

| Tool | What it does |
|---|---|
| `send_message` | Send SMS, email, or voice message with automatic TCPA/GDPR pre-check applied first. |
| `capture_lead` | Hand a prospect off to a specific SMB with deduplication. |
| `schedule_appointment` | Book, reschedule, or cancel an appointment via Cal.com or compatible booking platforms. |
| `send_transactional_confirmation` | TCPA-exempt transactional message (booking receipt, reminder). |
| `handle_inbound` | Classify an inbound customer message as booking, cancel, opt-out, or question. |
| `escalate_to_human` | Hand off to a human operator when the agent is stuck or the user requests it. |
| `import_booking_url` | Parse any public booking URL into a structured booking object an agent can act on. Run `check_booking_link` first. |
| `call_business` | Place a voice-AI phone call to a business on behalf of an agent. Requires provider config. |

---

## When to call each tool

**Verification before trust:**  
Before acting on a company name a user supplies, call `verify_company_record`. Before acting on a sanctions-sensitive counterparty, call `screen_sanctions`. Before any cross-border shipment decision, call `map_trade_restriction`.

**Compliance before outbound:**  
Always call `check_compliance` before calling `send_message`. It is free and prevents regulatory violations.

**Cost estimation before write ops:**  
Call `preview_cost` before any write tool to confirm the op is within budget and likely to succeed.

**Booking flow sequence:**  
`find_business` -> `verify_business` -> `check_booking_link` -> `preview_cost` -> `schedule_appointment` -> `get_status` -> `get_outcome`

**Health check:**  
Call `self_test` at the start of any session to confirm the server is reachable before building logic that depends on it.

---

## What this is not

- Not a general web-search tool. Use it only for the specific operations listed above.
- `map_trade_restriction` returns restriction status and links to official tariff schedules  -  it does not fabricate tariff rates.
- Write tools (`send_message`, `call_business`, etc.) require a working provider configuration on the server side. They do not send messages out of the box without a key and configured provider.
