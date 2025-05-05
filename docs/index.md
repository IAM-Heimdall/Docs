---
layout: home
title: IAM Heimdall
---

### Secure, Verifiable IAM for AI Agents
---

Heimdall provides a secure, verifiable Identity and Access Management (IAM) framework specifically designed for AI agents, enabling them to operate with proper authentication, authorization, and accountability across digital services.

<br>

## Table of Contents

1. [Introduction](#introduction)
2. [The Challenge: Identifying AI Agents](#thechallenge)
3. [Proposed Solution: A Dedicated Identity Layer](#proposedsolution)
4. [How it Works: Core Components](#corecomponents)
5. [Key Concepts in Action](#keyconcepts)
6. [Why IAM for AI Agents: Benefits](#benefits)
7. [Use Cases](#usecases)
   - [Verifiable Agent Identification](#agentidentification)
   - [Licensing & Compliance Enforcement](#complianceenforcement)
   - [Granular Authorization & Least Privilege](#authorization)
   - [Secure & Verifiable Delegation](#delegation)
   - [Transparent & Attributable Auditing](#auditing)
   - [Standardized Trust & Reputation Signals](#trustsignals)
   - [Differentiating Legitimate Access from Abuse](#botabuse)
   - [Secure Control of Physical Devices](#physicaldevices)
   - [Verifiable Identity in Communications](#communications)
   - [Secure Agent Lifecycle Management](#lifecyclemanagement)


<br>
### Quick Links

- [Visit Heimdall Website](https://iamheimdall.com)

---
## Introduction - The Need for Agent Identity {#introduction}

Artificial Intelligence (AI) agents are transitioning from tools to autonomous actors, operating across the digital landscape on behalf of users. This evolution demands a robust way to manage their identity, permissions, and actions. Today's methods—shared credentials, static API keys, or simple User-Agent strings—fall short, creating security risks and lacking the necessary control and accountability.

This Agent Identity Framework (AIF/Heimdall) addresses this gap by establishing a dedicated identity layer for AI agents. Built on proven standards like JWT and public-key cryptography, AIF provides a standardized, secure, and verifiable way for agents to identify themselves, prove their authorization, and interact responsibly with online services.

[Back to top](#tableofcontents)

---

## The Challenge - Identifying AI Agents {#thechallenge}

- **Authentication**: How does a service (website, API) know it's interacting with a legitimate AI agent versus a human, a simple bot, or a malicious actor? How can it verify the agent is acting with valid user consent?
    
- **Authorization**:How can users and services grant agents specific, limited permissions instead of broad access via shared credentials or overly permissive API keys?
    

- **Accountability**: How can actions taken by autonomous agents be reliably attributed back to the specific agent instance, its provider, and the delegating user for security and compliance?

- **Trust & Interoperability**: How can services make informed decisions about interacting with diverse agents from various providers in a standardized way?


Current methods – relying on User-Agent strings (easily spoofed), IP addresses (unreliable), or sharing user credentials/static API keys – are inadequate, insecure, and non-standardized for the complex interactions autonomous agents will undertake.

<br>

[Back to top](#tableofcontents)

---

## Solution - A Dedicated Identity Layer {#proposedsolution}

Heimdall is proposed as a standardized, secure, and verifiable identity layer specifically designed for AI agents, treating them as first-class digital entities. It aims to provide the foundational infrastructure for trust and accountability in the agent ecosystem.

**Core Goals:**

- **Verifiable Identity**: Provide a standard way to uniquely identify agent instances and their origins.  
- **Secure Delegation**: Enable users to securely grant specific, revocable permissions to agents.
- **Standardized Authorization**: Allow services to reliably verify agent permissions.
- **Transparent Accountability**: Facilitate clear audit trails for agent actions.

<br>

[Back to top](#tableofcontents)

---

## How it Works - Core Components {#corecomponents}

Heimdall integrates proven web standards (URIs, JWT, PKI) with agent-specific concepts:

- **(AID) Agent ID**: A structured URI (`aif://issuer/model/user-or-pseudo/instance`) uniquely identifying each agent instance and its context (who issued it, what model, who delegated). Supports pseudonymity for user privacy.
    
- **(ATK) Agent Token**: A short-lived, cryptographically signed JSON Web Token (JWT). The ATK acts as the agent's "digital passport," containing:
	- The agent's AID (*sub* claim).
	- The issuing entity (*iss* claim).
	- The intended audience/service (*aud* claim).
	- Explicit, granular permissions granted to the agent (actions + conditions).
	- The purpose of the delegation.
	- Verifiable trust_tags indicating issuer reputation, capabilities, user verification level, etc. This is optional.  
<br>
- **(REG) Registry Service**: A verification infrastructure (initially centralized/OSS, potentially federated later) where:
	- Services retrieve Issuing Entity public keys to verify ATK signatures.
	- Token revocation status can be checked.
	- Issuer legitimacy can be confirmed.
<br>    
- **(TRUST) Trust Mechanisms:** A phased approach starting with verifiable attributes (trust_tags in the ATK) allowing services to assess agent trustworthiness based on concrete data, evolving potentially towards dynamic scoring.
    

- **(SIG) Agent Signature:** Standard asymmetric cryptography (Ed25519/ECDSA) used by Issuing Entities to sign ATKs, ensuring authenticity and integrity.

<br>

[Back to top](#tableofcontents)

---

## Key Concepts in Action {#keyconcepts}


**Key Entities in the Ecosystem**

- **User**: The human principal delegating authority to an AI agent. 
- **Issuing Entity (IE)**: An organization authorized to issue AIDs and sign ATKs for agents (e.g., AI providers, agent application builders).    
- **AI/LLM Provider**: The entity providing the underlying AI model capabilities.
- **Service Provider (SP)**: Digital services, websites, or APIs that agents interact with.
- **Registry Operator**: Entity maintaining instances of the Registry Service (REG).
- **Agent Builder**: Developer or organization creating the agent application/service.

<br>
**Sample Workflow**

- **Delegation**: A User authorizes an Agent Platform (Issuing Entity) to act on their behalf for a specific purpose with defined permissions (e.g., via an enhanced OAuth/OIDC flow). This can be extended to multi layer delegation - agent to agent.
    
- **Issuance**: The Issuing Entity generates an AID and issues a signed ATK containing the AID, permissions, purpose, and trust tags.
    
- **Interaction**: The Agent presents its ATK (e.g., in an HTTP header) when interacting with a Service Provider.
    
- **Validation**: The Service Provider:
    

	1. Retrieves the Issuing Entity's public key from the REG service.
	2. Verifies the ATK's signature and standard claims (expiry, audience).
	3. Checks the token's revocation status via the REG.
	4. Evaluates the permissions claim against the requested action.
	5. Optionally uses trust_tags for risk assessment or policy decisions.
<br>

- **Accountability**: The Service Provider logs the action with the verified AID and claims from the ATK.

<a href="{{ site.baseurl }}/images/sequence-diagram.png" target="_blank">
  <img src="{{ site.baseurl }}/images/sequence-diagram.png" alt="AIF Verification Flow" style="max-width: 100%; height: auto;">
</a>

*Click image to view full size*

<br>

[Back to top](#tableofcontents)

---

## Benefits {#benefits}


- **For Service Providers:**

	- Enhanced Security: Reliably distinguish legitimate, authorized agents from spoofed/unauthorized ones. Mitigate risks from credential sharing.
	- Granular Control: Apply specific policies, rate limits, or access rules based on verifiable agent identity and permissions.
	- Improved Auditability: Create trustworthy logs of agent actions for compliance and security analysis.
	- Reduced Abuse: Identify and block misbehaving agents or those from untrusted sources.
	- Analytics: Standardized way to gather analytics on agent traffic.

<br>
- **For Agent Builders & AI Providers:**
    
	- Build Trust: Signal legitimacy and security posture to users and services.
	- Enable Access: Provide a standard way for agents to access services requiring verification.
	- Differentiation: Stand out based on verifiable attributes and responsible practices.

<br>

- **For Users:**
    
	- Better Security: Reduced need to share primary credentials.
	- Greater Control: Clearer understanding and management of permissions delegated to agents (via agent platforms).
	- Increased Confidence: Assurance that agents act within defined boundaries.

<br>

[Back to top](#tableofcontents)

---
