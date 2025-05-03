---
layout: default
title: Verifiable Agent Identification
parent: Use Cases
nav_order: 1
---
### Verifiable Agent Identification & Authentication

- **Scenario**: A Service Provider (SP), like a financial API or a content platform, receives an incoming request. It needs to reliably determine the nature of the requestor. Is it the legitimate human user? Is it Agent Instance #123 delegated by that user? Is it Agent Instance #456 from a different platform acting for the same user? Or is it a malicious bot spoofing an agent's identity? Applying correct permissions, policies, and logging requires knowing who is truly acting.
    
- **Solution Principle**: Agents require unique, verifiable digital identities, distinct from their delegating users. These identities must be cryptographically verifiable, allowing SPs to authenticate the specific agent instance making the request and differentiate it from other agents, users, or fraudulent actors.
    
- **Benefit**: Enables service providers to reliably distinguish agent traffic, prevent identity spoofing, apply agent-specific policies (like rate limits or access to specialized endpoints), and build foundational trust necessary for more advanced interactions.
    
- **Alternatives & Gaps:**
    

	- **User-Agent Strings**: Trivially easy to fake; provide no cryptographic verification; offer limited, non-standardized information. 
		- *Gap: No verifiability, no unique identity.*
    
	- **IP Addresses**: Unreliable identifiers (dynamic IPs, NAT, VPNs, shared cloud infrastructure); identifies network location, not the specific agent instance or its delegation context. 
		- *Gap: No specific identity, unreliable.*
    

	- **Shared User Credentials (Password, API Key):** Highly insecure; makes the agent indistinguishable from the user; grants excessive permissions; violates terms of service; prevents agent-specific control or audit. 
		- *Gap: Blurs identity, insecure, excessive privilege.*
