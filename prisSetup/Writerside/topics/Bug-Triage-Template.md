# \# Bug Triage Template

# 

# \## ✅ Expected Behavior

# > \_What should have happened instead? Describe in both technical and business terms.\_

# 

# Example:  

# “System should reapply endorsement and trigger a manual task if validation fails.  

# The policy should not silently revert to a bad state.”

# 

# ---

# 

# \## 🖼️ Production Example(s)

# > \_Any real-world policies, jobs, or logs related to the issue.\_

# 

# \- Policy #: `PA0123456-03`

# \- Job Type: `Endorsement / Cancellation / IVANS Export`

# \- Date Observed: `MM/DD/YYYY`

# \- Attached Evidence:

# &nbsp;   - \[✔] Logs

# &nbsp;   - \[✔] Screenshots

# &nbsp;   - \[ ] PolicyBean dump

# 

# ---

# 

# \## 🔄 Impacted Workflows

# > \_What system flows and business teams are affected?\_

# 

# \- \[ ] Billing

# \- \[ ] Underwriting

# \- \[ ] Claims

# \- \[ ] IVANS / Producers

# \- \[ ] Agent Portal

# \- \[ ] UI Routing

# \- \[ ] Other: \_\_\_\_\_\_\_\_\_\_\_

# 

# ---

# 

# \## 🧠 Notes or Linked Work

# > \_Spikes, related tickets, or prior bugs that connect to this issue.\_

# 

# \- Related Jira: `\[GW-XXXX]`, `\[GW-YYYY]`

# \- Spike: `\[GW-AAAA]`

# \- Confluence Docs: `\[Link]`

# \- Known workaround? \*\*Yes / No\*\*

# 

# ---

# 

# \## 🧪 Test Coverage / AC Mapping

# > \_If applicable, note which tests validate this and how the AC is written.\_

# 

# \- Regression Impacted: \*\*Yes / No\*\*

# \- Test Case ID (if automated): `TC-1234-REAPPLY`

# \- AC from ticket:

# &nbsp; ```text

# &nbsp; “When reapply fails, system triggers PolicyTask0005 and assigns to %LicensedProduct%.”



