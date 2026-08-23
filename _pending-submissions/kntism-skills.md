# Pending submission: kntism/skills

**Target repo:** https://github.com/kntism/skills  
**Description:** "Awesome Claude Agent Skills" — curated collection of installable agent skills  
**Stars:** ~1 (early, but directly on-format for what we've built)  
**Section:** Business & Compliance (new section if one does not exist), or Data & Research  
**Fit:** We have built a SKILL.md-format skill package in exactly the pattern this list curates.  
**Status:** DO NOT SUBMIT until CEO green-lights after live-honesty re-verify

---

## Proposed entry

Add to the **Business & Compliance** section (create if absent) in `README.md`:

```markdown
### 🏢 Business & Compliance
- **[agentbroker](https://github.com/basilalshukaili/agentbroker-skill)** - Live GLEIF+SEC company verification, OFAC/EU/UN/UK sanctions screening, and cross-border trade-restriction mapping. 11 read tools free (no key). Write tools for SMS, booking, and voice calls need a free email key. MCP endpoint: `https://hatchloop.dev/mcp/agent-broker`
```

If adding to an existing section (Data & Research or similar), use:

```markdown
- **[agentbroker](https://github.com/basilalshukaili/agentbroker-skill)** - Live GLEIF+SEC company verification, OFAC/EU/UN/UK sanctions screening, and cross-border trade-restriction mapping. 11 read tools free. [MCP](https://hatchloop.dev/mcp/agent-broker)
```

---

## How to open the PR

```bash
# 1. Fork the repo
MSYS_NO_PATHCONV=1 gh repo fork kntism/skills --clone=false

# 2. Clone your fork
git clone https://github.com/basilalshukaili/skills.git
cd skills

# 3. Create a branch
git checkout -b add-agentbroker-skill

# 4. Edit README.md — add the entry above
# If a "Business & Compliance" section does not exist, create it after the last existing category section

# 5. Commit and push
git add README.md
git commit -m "Add agentbroker skill — live GLEIF/OFAC sanctions + compliance MCP tools"
git push -u origin add-agentbroker-skill

# 6. Open the PR
MSYS_NO_PATHCONV=1 gh pr create \
  --repo kntism/skills \
  --title "Add agentbroker — live GLEIF/OFAC sanctions + company verification agent skill" \
  --body "agentbroker is a SKILL.md-format agent skill that installs a hosted MCP server (streamable-HTTP) providing: live GLEIF LEI + SEC EDGAR company verification, OFAC/EU/UN/UK+40 sanctions screening, cross-border trade-restriction mapping, TCPA/GDPR/CASL compliance pre-flight (22 jurisdictions), SMB search/verify, booking link checks, and async op tracking. 11 tools free, no key. Write tools (SMS, booking, voice) need a free email-verified key. Skill repo: https://github.com/basilalshukaili/agentbroker-skill"
```

---

## Notes

- This list follows the kntism/skills pattern: a SKILL.md per skill, listed in README by category.
- Our skill package already follows that exact pattern.
- The repo is small and early — this may move to a larger audience list in the future.
- Check if the repo has a CONTRIBUTING.md with specific submission instructions before opening the PR.
