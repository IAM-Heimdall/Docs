---
layout: page
title: IAM Heimdall
permalink: /use-cases/auditing/
---
## Transparent & Attributable Agent Auditing

- **Scenario:** A configuration change is made via API, causing an outage. Investigation reveals the change originated from an IP address associated with an Agent Builder platform. Was it Agent X acting for User A, Agent Y for User B (using the same platform), a rogue employee at the platform, or a compromised platform credential? Logs based only on IP, client ID, or generic API key lack sufficient granularity.
    
- **Solution Principle:** Interactions involving agents must generate secure, detailed audit logs containing verifiable, unique identifiers that reliably attribute each action to the specific agent instance, its issuing platform/provider, the delegating principal (user/org, potentially pseudonymized), and ideally the task purpose.
    
- **Benefit:** Enables accurate security forensics, incident response, performance analysis, compliance reporting, and dispute resolution by providing a clear, trustworthy record of "who did what, acting for whom, and why".
    
- **Alternatives & Gaps:**
    

	- **Standard Web/API Logs (IP, User-Agent):** Grossly insufficient for attributing actions to specific agents or delegations. 
		- *Gap: Lacks verifiable agent/delegation identity.*
    
	- **OAuth Client ID Logging:** Identifies the Agent Platform, but not the specific agent instance or user delegation behind the action. 
		- *Gap: Insufficient granularity.*
    

	- **Proprietary Platform Logging:** Each Agent Builder might have internal logs, but the Service Provider needs its own verifiable logs based on the credentials presented to it, using a standardized format for consistency across different agent sources. 
		- *Gap: Not standardized, not available/verifiable by SP.*




<br><br><br><br>

### More Use Cases
- [Verifiable Agent Identification](./use-cases/IDandAuth.md)
- [Licensing & Compliance Enforcement](./use-cases/ComplianceEnforcement.md)
- [Granular Authorization & Least Privilege](./use-cases/AuthandLeastPrivilege.md)
- [Secure & Verifiable Delegation](./use-cases/delegationofauthority.md)
- [Standardized Trust & Reputation Signals](/use-cases/trust-signals)
- [Differentiating Legitimate Access from Abuse](./use-cases/BotAbuse.md)
- [Secure Control of Physical Devices](./use-cases/PhysicalDevices.md)
- [Verifiable Identity in Communications](./use-cases/VoiceVerification.md)
- [Secure Agent Lifecycle Management](./use-cases/LifecycleManagement.md)

