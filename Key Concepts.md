
##### Key Concepts in Action


**Key Entities in the Ecosystem**

- User: The human principal delegating authority to an AI agent.
    
- Issuing Entity (IE): An organization authorized to issue AIDs and sign ATKs for agents (e.g., AI providers, agent application builders).
    
- AI/LLM Provider: The entity providing the underlying AI model capabilities.
    
- Service Provider (SP): Digital services, websites, or APIs that agents interact with.
    
- Registry Operator: Entity maintaining instances of the Registry Service (REG).
- Agent Builder: Developer or organization creating the agent application/service.**

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
    

- **Accountability**: The Service Provider logs the action with the verified AID and claims from the ATK.