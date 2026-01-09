# Incident 002 – Firewall Blocked Malicious URL Access

## Summary
A firewall alert was generated after an internal endpoint attempted to access an external URL that was listed in threat intelligence and blacklist feeds.  
The connection was successfully blocked by the firewall, preventing potential compromise.

## Alert Details
- **Incident Type:** Malicious URL Access Attempt
- **Detection Source:** Firewall
- **Action Taken:** Blocked
- **Direction:** Outbound
- **Source IP:** Internal workstation
- **Destination Port:** 80 (HTTP)
- **Application:** Web Browsing
- **Threat Category:** Known Malicious Domain

## Indicators of Suspicion
- Shortened URL commonly used in phishing campaigns
- Destination IP associated with known malicious activity
- URL accessed shortly after a phishing email was delivered
- Threat intelligence match on destination domain

## Investigation Steps
1. Reviewed firewall logs to confirm the outbound connection attempt.
2. Verified that the destination URL was present in blacklist and threat intelligence feeds.
3. Confirmed that the firewall successfully blocked the request.
4. Correlated the event with recent phishing email alerts.
5. Checked for additional connection attempts from the same source.

## Impact Assessment
- **User Interaction:** Link click attempted
- **Malware Execution:** None observed
- **Data Exfiltration:** None
- **Severity Level:** Medium

## Containment and Mitigation
- Firewall rule successfully prevented the connection
- Destination URL and IP remain blocked
- Endpoint monitoring recommended for follow-up activity
- User awareness reminder suggested

## Escalation Decision
- **Escalation Required:** No  
The threat was contained automatically, and no further malicious activity was detected.

## Lessons Learned
Firewall and threat intelligence integration is critical for preventing phishing-related attacks.  
Shortened URLs remain a common technique used to obscure malicious destinations.
