---
layout: default
title: Agent-Initiated Communication
parent: Use Cases
nav_order: 9
---
## Verifiable Identity in Agent-Initiated Communication

- **Scenario**: An agent initiates a phone call or sends an email/chat message on behalf of a user (e.g., appointment scheduling, customer service inquiry). The recipient needs to know if the communication is genuinely from an authorized agent representing that user or if it's spam/phishing attempting to impersonate them.
    
- **Solution Principle:** The communication protocol incorporates or references a verifiable agent credential. For calls, this could be integrated via STIR/SHAKEN extensions or call setup protocols. For email/chat, headers or embedded tokens could carry the verifiable assertion linkable back to the user.
    
- **Benefit:** Allows recipients (human or automated systems) to verify the legitimacy of agent-initiated communications, filter spam/impersonation attempts, prioritize trusted interactions, and access relevant context about the agent's purpose. Enables "Caller ID for Agents".
    
- **Alternatives & Gaps:**
    

	- **No Verification**: Recipient relies on heuristics, caller ID number (spoofable), email headers (spoofable), or content analysis. Prone to spam and phishing. 
		- *Gap: No reliable verification.*
    

	- **Proprietary Platform Markers:** E.g., Google Duplex identifying itself verbally. Not standardized, not cryptographically verifiable, limited to specific platforms. 
		- *Gap: Not standard, not verifiable.*