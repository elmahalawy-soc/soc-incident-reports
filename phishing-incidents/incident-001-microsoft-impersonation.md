# Incident 001 — Microsoft Impersonation Phishing Email (Credential Harvesting Attempt)

## Summary
A phishing email impersonating Microsoft was delivered to a user. The message claimed unusual sign-in activity and attempted to lure the user to a fake login page to capture credentials. No malware attachment was present. The priority was to validate user interaction and confirm there was no account compromise.

## Alert Context
- **Category:** Phishing / Credential Harvesting
- **Initial Source:** Email Security Alert
- **Direction:** Inbound
- **User Targeted:** c.allen@thetrydaily.thm
- **Sender:** no-reply@m1crosoftsupport.co (look-alike domain)
- **Subject:** Unusual Sign-In Activity on Your Microsoft Account
- **Embedded Link:** https://m1crosoftsupport.co/login

## Key Indicators (Why Suspicious)
- Look-alike domain using character substitution (e.g., "m1crosoft" vs "microsoft")
- Urgent language pushing immediate action (“secure your account immediately”)
- External login link not associated with an official Microsoft domain
- Social engineering theme referencing foreign login activity

## Investigation Steps (Tier-1 SOC Workflow)
1. Reviewed email headers/content for impersonation and social engineering indicators.
2. Identified the sender domain as look-alike (typosquatting) and treated the embedded login URL as suspicious.
3. Recommended correlation with:
   - **Web proxy / firewall logs** to confirm whether the link was accessed
   - **Authentication logs** to identify any successful or suspicious sign-in activity around the alert timeframe

## Severity Assessment
- **Severity:** Medium  
**Rationale:** The attempt is malicious, but no confirmed user click or account compromise was observed in the alert context. Severity would increase to High if log review confirmed credential entry or unauthorized access.

## Containment / Remediation Recommendations
- Block the sender domain and embedded URL at email/web controls
- Validate whether the user accessed the link via proxy/firewall logs
- Review authentication logs for suspicious sign-ins (unexpected geo/IP, impossible travel, repeated failures)
- User awareness: advise user not to interact with security-themed emails containing external login links; use official portals instead
- Continue monitoring for related sign-in attempts

## Escalation Decision
- **Escalation Required:** No  
**Rationale:** At this stage there is no confirmed compromise or impact. Escalation would be required if evidence showed credentials were submitted, MFA prompts occurred unexpectedly, or unauthorized login was successful.

## Lessons Learned
- Security-themed phishing is effective because it creates urgency and fear.
- Look-alike domains and external login links are high-signal indicators for credential harvesting.
