# Pending submission: punkpeye/awesome-mcp-servers

**Target repo:** https://github.com/punkpeye/awesome-mcp-servers  
**Stars:** ~92k  
**Section:** Business & Automation (or Finance  -  see note below)  
**Status:** DO NOT SUBMIT until CEO green-lights after live-honesty re-verify

---

## Proposed entry

Add the following line to the **Business & Automation** section of `README.md`.
If no such section exists, use the **Finance** section, or the closest section covering compliance/legal/verification.

```markdown
- [Agent Broker](https://github.com/basilalshukaili/agentbroker-skill) - Live GLEIF+SEC company verification, OFAC/EU/UN/UK sanctions screening, and cross-border trade-restriction mapping. 11 read tools free (no key); write tools (SMS, booking, voice calls) use credits: free email key (100 ops/day) or packages from $9/1,000 credits at https://hatchloop.dev/pricing. [MCP endpoint](https://hatchloop.dev/mcp/agent-broker)
```

---

## How to open the PR

```bash
# 1. Fork the repo
MSYS_NO_PATHCONV=1 gh repo fork punkpeye/awesome-mcp-servers --clone=false

# 2. Clone your fork
git clone https://github.com/basilalshukaili/awesome-mcp-servers.git
cd awesome-mcp-servers

# 3. Create a branch
git checkout -b add-agentbroker

# 4. Edit README.md  -  add the line above to the Business & Automation section
# (Open README.md, find the section, insert the line in alphabetical order by product name)

# 5. Commit and push
git add README.md
git commit -m "Add Agent Broker MCP server (GLEIF/SEC verification, OFAC sanctions, trade restrictions)"
git push -u origin add-agentbroker

# 6. Open the PR
MSYS_NO_PATHCONV=1 gh pr create \
  --repo punkpeye/awesome-mcp-servers \
  --title "Add Agent Broker  -  live GLEIF/SEC verification + OFAC sanctions + trade restriction MCP server" \
  --body "Agent Broker is a hosted streamable-HTTP MCP server with 20 tools for company verification (GLEIF LEI + SEC EDGAR), live sanctions screening (OFAC SDN + EU + UN + UK + 40+ lists), cross-border trade-restriction mapping, and outbound-communication compliance (TCPA/GDPR/CASL across 22 jurisdictions). 11 read tools are free with no key. Write tools (SMS, booking, voice calls) need a free email-verified key or paid plan. Endpoint: https://hatchloop.dev/mcp/agent-broker"
```

---

## Notes

- Insert the entry in alphabetical order within the section.
- The entry links to the skill repo (basilalshukaili/agentbroker-skill) as the install surface, not the server source repo.
- Confirm the tool list against the live endpoint before submitting: `curl -s -X POST https://hatchloop.dev/mcp/agent-broker -H "Content-Type: application/json" -d '{"jsonrpc":"2.0","method":"tools/list","id":1}'`
