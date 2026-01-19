# Building an Enterprise-Ready Chatbot in One Day

## Create a chatbot in a day and adjust it to the needs of your organization.

Remarks: The [PDF](enterprise_chatbot_in_one_day.pdf) includes information about the prerequisites, the steps of the hackathon, and all necessary links.

The base scenario for the hackathon (in our case) was: [RAG chat app with Azure OpenAI and Azure AI Search (Python)](https://github.com/Azure-Samples/azure-search-openai-demo)

Goals:

- Reuse existing examples as a base for hackathons.
- Show how easily those examples can be extended (using GitHub Copilot).
- Discuss how to "transform" a sample into an enterprise-ready solution (authentication, custom search, document ingestion, validation of answers, etc.).

### High-level steps for the hackathon

- Introduction: what is an enterprise-ready chatbot?
- Manually deploy the base scenario to Azure.
- Detailed explanation of the architecture and components used in the base scenario.
- Use CI/CD to deploy the base scenario to Azure (using GitHub Codespaces and GitHub Actions).
- Check security using GitHub Advanced Security and validate code quality in the solution.
- Use AI to understand the code structure and key architectural components/patterns.
- Modify the solution—add new UI elements (in this example: Santa Claus).
- New functionality (using GitHub Copilot prompts!):
  - Custom "chunking" of documents.
  - Priority fields for documents for better answers (and manual tuning of the vector search).
  - Semantic Ranking configuration.
  - Web/SharePoint search and agentic retrieval.
  - Validator for answers (using the RAG pattern) and key differences—agents vs. pure RAG, and how to combine agents with RAG.
  - Additional activity logging (e.g., for compliance/legal reasons).
  - Authentication using Microsoft Entra ID.
- Governance, manageability, and security considerations for enterprise-ready chatbots.
  - Services selection criteria (costs, security, compliance, etc.)
  - Roles and responsibilities
  - Networking isolation with focus on private endpoints
  - Publishing the application
  - How to use Azure Policy to help us
  - Managed identities—how to use them (and how they are used in the base scenario)
  - Defender for Cloud
  - Final goal: Zero Trust architecture

### Final result screenshots

![chatscreen](https://github.com/user-attachments/assets/cb32c18b-e940-4101-aebe-e6ac93495dfb)