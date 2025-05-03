---
layout: default
title: Granular Authorisation 
parent: Use Cases
nav_order: 3
---
## Granular Agent Authorization & Least Privilege

- **Scenario**: A user asks an agent to book a specific flight for them. The agent might use the user's main travel account credentials. If these credentials also allow cancelling all trips or changing account details, the agent has far more power than needed for its task, increasing the risk of accidental or malicious misuse. It might not also be practically possible for the travel account platform (SP) to provide granular tokens that map to desired capabilities of each agent instance. 
    
- **Solution Principle**: Agents must operate under the principle of least privilege. Authorization mechanisms must allow users (or organizations) to grant agents specific, limited permissions sufficient only for the delegated task and context, separate from the delegator's full entitlements.
    
- **Benefit:** Minimizes the potential damage if an agent is compromised or behaves incorrectly. Enables safer automation of sensitive functions by strictly scoping agent capabilities. Allows service providers to enforce fine-grained access control tailored to the agent's specific role.
    
- **Alternatives & Gaps:**
    

	- **Shared User Credentials**: Agent inherits all user permissions. Fails least privilege entirely. 
		- *Gap: No granularity.*
    
	- **Static API Keys with Broad Permissions**: Often grants wide access (e.g., read/write to a whole data category). Managing numerous keys for very fine-grained access becomes complex. 
		- *Gap: Often lacks task-specific granularity, management overhead.*
    

	- **Standard OAuth Scopes:** While better and closest to the best we have, scopes are often coarse-grained (e.g., email, profile, files.readwrite) and defined by the SP, lacking the context of the specific agent task. They don't easily express complex conditions (e.g., "transaction_limit:$50"). 
		- *Gap: Often lacks fine granularity and conditionality needed for agents.*