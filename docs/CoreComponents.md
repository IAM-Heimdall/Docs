---
layout: page
title: IAM Heimdall
permalink: /components/
---
## How it Works - Core Components

Heimdall integrates proven web standards (URIs, JWT, PKI) with agent-specific concepts:

- **(AID) Agent ID**: A structured URI (`aif://issuer/model/user-or-pseudo/instance`) uniquely identifying each agent instance and its context (who issued it, what model, who delegated). Supports pseudonymity for user privacy.
    
- **(ATK) Agent Token**: A short-lived, cryptographically signed JSON Web Token (JWT). The ATK acts as the agent's "digital passport," containing:
	- The agent's AID (*sub* claim).
	- The issuing entity (*iss* claim).
	- The intended audience/service (*aud* claim).
	- Explicit, granular permissions granted to the agent (actions + conditions).
	- The purpose of the delegation.
	- Verifiable trust_tags indicating issuer reputation, capabilities, user verification level, etc. This is optional.
    

- **(REG) Registry Service**: A verification infrastructure (initially centralized/OSS, potentially federated later) where:
	- Services retrieve Issuing Entity public keys to verify ATK signatures.
	- Token revocation status can be checked.
	- Issuer legitimacy can be confirmed.

<br>    

- **(TRUST) Trust Mechanisms:** A phased approach starting with verifiable attributes (trust_tags in the ATK) allowing services to assess agent trustworthiness based on concrete data, evolving potentially towards dynamic scoring.
    

- **(SIG) Agent Signature:** Standard asymmetric cryptography (Ed25519/ECDSA) used by Issuing Entities to sign ATKs, ensuring authenticity and integrity.**



<br><br><br><br>
[Back to Home](./index.md)<br>
[Next Page - Key Concepts in Action](./KeyConcepts.md)