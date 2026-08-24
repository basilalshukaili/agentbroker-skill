# Pending submission: xpaysh/awesome-x402

**Target repo:** https://github.com/xpaysh/awesome-x402  
**Stars:** ~283  
**Section:** MCP Integration (or Services & APIs  -  the section listing pay-per-call MCP services)  
**Fit:** AgentBroker supports x402 for write-tool billing (credits model: Starter $9/1,000 ops at hatchloop.dev/pricing, or agents pay per-call via x402); sanctions + company verification are high-value compliance services for agent workflows.  
**Status:** DO NOT SUBMIT until CEO green-lights after live-honesty re-verify

---

## Proposed entry

Add to the **MCP Integration** or **Services & APIs** section (whichever lists entries like Octodamus, Kaisha, Sirenic, etc.) in `README.md`:

```markdown
- [Agent Broker](https://hatchloop.dev/agent-broker/) - Live GLEIF+SEC company verification, OFAC/EU/UN/UK+40 sanctions screening, and cross-border trade-restriction mapping as MCP calls. 11 read tools free (no key, no x402). Write tools (SMS, booking, voice calls to SMBs) use credits (Starter $9/1,000, Growth $29/3,500, Scale $99/13,000 at https://hatchloop.dev/pricing) or agents pay per-call via x402. MCP: `https://hatchloop.dev/mcp/agent-broker`. ([Skill/Install](https://github.com/basilalshukaili/agentbroker-skill) | [MCP](https://hatchloop.dev/mcp/agent-broker))
```

---

## How to open the PR

```bash
# 1. Fork the repo
MSYS_NO_PATHCONV=1 gh repo fork xpaysh/awesome-x402 --clone=false

# 2. Clone your fork
git clone https://github.com/basilalshukaili/awesome-x402.git
cd awesome-x402

# 3. Create a branch
git checkout -b add-agentbroker

# 4. Edit README.md  -  add the line above to the appropriate section
# Find the MCP Integration section or Services & APIs section and insert in alphabetical order

# 5. Commit and push
git add README.md
git commit -m "Add Agent Broker  -  GLEIF/SEC verification + OFAC sanctions MCP server with x402 billing"
git push -u origin add-agentbroker

# 6. Open the PR
MSYS_NO_PATHCONV=1 gh pr create \
  --repo xpaysh/awesome-x402 \
  --title "Add Agent Broker  -  live GLEIF/OFAC/sanctions MCP server (x402 billing)" \
  --body "Agent Broker is a hosted MCP server (streamable-HTTP) providing live GLEIF LEI + SEC EDGAR company verification, OFAC/EU/UN/UK sanctions screening, and cross-border trade-restriction mapping. 11 read tools are free. Write tools (messaging, booking, voice) use a credits model (Starter \$9/1,000 credits at https://hatchloop.dev/pricing) or agents pay per-call via x402. Endpoint: https://hatchloop.dev/mcp/agent-broker  -  install guide: https://github.com/basilalshukaili/agentbroker-skill"
```

---

## Notes

- Strong fit: sanctions screening and company verification are exactly the kinds of compliance services agents using x402 need.
- The 11 free tools need no payment; billing only applies to write tools  -  be accurate about this in the PR description.
- Check CONTRIBUTING.md in the target repo for any format requirements before opening.
