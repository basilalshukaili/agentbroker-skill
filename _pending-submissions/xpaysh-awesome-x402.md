<!-- Draft, not a submission. Status changed twice; both changes are on the
     record below so nobody re-derives the reasoning from scratch. -->

# Draft - viable again, awaiting the founder's go-ahead to submit

**2026-08-27: CANCELLED.** This directory lists services that accept x402
crypto payment. We did not. The rail was built and proven on Base mainnet and
was switched OFF: no VASP licence available in Oman, the CBO warns against
crypto, and the company registers under an Omani CR. Submitting would have
advertised a capability we had deliberately disabled, in the one directory
where that is the whole point of being listed.

**2026-08-29: REVERSED by founder decision.** The crypto-advertising ban was
lifted. x402 is live and advertised on the running service - an unauthenticated
write call returns "attach a signed x402 payment as params._meta['x402/payment']
... USDC on Base" as its no-signup option, verified against production
2026-08-30. So the reason this submission was cancelled no longer holds.

The entry below has been corrected to match what we actually serve. It is
still a DRAFT: listing us in a public directory is an outward-facing action
and needs the founder's word before anyone submits it.

Residual risk (unchanged, recorded in memory `oman-legal-compliance`): the
contracting party is Omani.

---

<details><summary>Proposed entry (corrected 2026-08-30)</summary>

# Pending submission: xpaysh/awesome-x402

**Target repo:** https://github.com/xpaysh/awesome-x402  
**Stars:** ~283  
**Section:** MCP Integration (or Services & APIs  -  the section listing pay-per-call MCP services)  
**Fit:** AgentBroker supports x402 for write-tool billing (credits model: Starter $9/1,000 ops at hatchloop.dev/pricing, or x402 pay-per-call in USDC on Base with no signup); sanctions + company verification are high-value compliance services for agent workflows.  
**Status:** claims re-verified against production 2026-08-30; awaiting founder go-ahead to submit

---

## Proposed entry

Add to the **MCP Integration** or **Services & APIs** section (whichever lists entries like Octodamus, Kaisha, Sirenic, etc.) in `README.md`:

```markdown
- [Agent Broker](https://hatchloop.dev/agent-broker/) - Live GLEIF+SEC company verification, OFAC/EU/UK sanctions screening, and cross-border trade-restriction mapping as MCP calls. 12 of 20 tools need no key. Write tools (SMS, booking, voice calls to SMBs) use credits (Starter $9/1,000, Growth $29/3,500, Scale $99/13,000 at https://hatchloop.dev/pricing) or x402 pay-per-call (USDC on Base, no signup). MCP: `https://hatchloop.dev/mcp/agent-broker`. ([Skill/Install](https://github.com/basilalshukaili/agentbroker-skill) | [MCP](https://hatchloop.dev/mcp/agent-broker))
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
  --body "Agent Broker is a hosted MCP server (streamable-HTTP) providing live GLEIF LEI + SEC EDGAR company verification, OFAC/EU/UK sanctions screening, and cross-border trade-restriction mapping. 12 of 20 tools need no key. Write tools (messaging, booking, voice) use a credits model (Starter \$9/1,000 credits at https://hatchloop.dev/pricing) or x402 pay-per-call (USDC on Base, no signup). Endpoint: https://hatchloop.dev/mcp/agent-broker  -  install guide: https://github.com/basilalshukaili/agentbroker-skill"
```

---

## Notes

- Strong fit: sanctions screening and company verification are exactly the kinds of compliance services agents using x402 need.
- The 11 free tools need no payment; billing only applies to write tools  -  be accurate about this in the PR description.
- Check CONTRIBUTING.md in the target repo for any format requirements before opening.

</details>
