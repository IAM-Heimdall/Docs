---
layout: default
title: Differentiating from Abuse
parent: Use Cases
nav_order: 7
---
## Differentiating Legitimate Automated Access from Abuse

- **Scenario:** A popular e-commerce site or event ticketing platform is plagued by sophisticated bots scraping pricing data excessively or attempting to hoard limited inventory faster than human users can react. Blocking based on IP or simple CAPTCHAs is often ineffective against determined actors.
    
- **Solution Principle:** Implement policies that differentiate access based on verifiable agent identity. Legitimate agents (e.g., price comparison services authorized by users or the platform, personal shopping agents) present verifiable credentials. Unverifiable or anonymous automated traffic can be strictly rate-limited, challenged more aggressively (e.g., advanced CAPTCHA, proof-of-work), or blocked.
    
- **Benefit:** Allows SPs to welcome beneficial automation (e.g., authorized price comparisons, user-delegated shopping) while effectively mitigating abusive automation (scalping bots, excessive scraping). Protects platform integrity and ensures fairer access for human users.
    
- **Alternatives & Gaps:**
    

	- **Advanced Bot Detection (WAF Rules, Fingerprinting):** Can be effective but often results in an arms race; may block legitimate automation or inconvenience humans. 
		- *Gap: Focuses on blocking bad behavior, not enabling good automation.*
    
	- **Strict Rate Limiting:** Can throttle legitimate use cases along with abuse. 
		- *Gap: Indiscriminate.*
    

	- **Proof-of-Work/CAPTCHA:** Adds friction, potentially solvable by sophisticated bots. 
		- *Gap: Friction, potentially ineffective.*