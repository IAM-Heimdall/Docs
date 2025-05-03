---
layout: default
title: Physical Devices and IOT
parent: Benefits and Use Cases
nav_order: 8
---
#### Secure Control of Physical Devices & IoT Interactions

- **Scenario:** A user wants their AI assistant agent to control smart home devices (lights, thermostat, locks) via the device manufacturer's cloud API. The API needs assurance that the command originates from an entity genuinely authorized by the homeowner.
    
- **Solution Principle:** The agent authenticates to the IoT platform's API using a verifiable identity token  that proves it was delegated by the registered homeowner (sub contains user link) with specific permissions (permissions: e.g., {"action": "set_thermostat", "device_id": "thermo123", "conditions": {"min_temp": 18, "max_temp": 25}}).
    
- **Benefit:** Enables secure, delegated control of physical systems via AI agents, preventing unauthorized access or manipulation while providing an audit trail tied to the specific agent and user delegation.
    
- **Alternatives & Gaps:**
    

	- **Shared API Keys per User:** If the key leaks from one agent/app, all devices are compromised. Lacks granularity. 
		- *Gap: Security risk, no granular control.*
    

	- **Standard OAuth per Device/Platform:** Better, but the SP still only sees the "Agent Platform" client ID, not the specific agent instance or task purpose. 
		- *Gap: Lacks agent-specific identity and context.*