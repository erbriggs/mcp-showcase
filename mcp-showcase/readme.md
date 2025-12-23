# HubSpot Model Context Protocol (MCP) (Local Develop)

**Reference Video:** [HubSpot MCP Overview](https://www.youtube.com/watch?v=bZo4jVdZfaI)
**Beta Notes:** [HubSpot MCP Beta](https://developers.hubspot.com/docs/mcp/hubspot-mcp-beta)
**Beta Rollout:** [HubSpot MCP Rollout Notes](https://app.hubspot.com/product-updates/44397854/in-beta?rollout=239890)

## What MCP Is

Model Context Protocol (MCP) is a standardized protocol that enables Large Language Models (LLMs) to interact securely and predictably with external systems. In HubSpot's implementation, MCP provides a structured, OAuth-scoped layer between AI agents and the HubSpot Developer Platform.

### MCP Ensures

- Secure OAuth-scoped access
- Standardized schema for actions
- Idempotent, safe execution
- Predictable, typed results returned to the LLM

## HubSpot's Developer MCP Server

The Developer MCP Server is a local runtime that exposes HubSpot CLI capabilities as MCP tools. This allows an AI agent (e.g., ChatGPT or Claude) to operate like a HubSpot developer with controlled permissions.

### Capabilities

- Read/write CMS theme files
- Interact with HubSpot CMS assets
- Deploy or retrieve modules
- Access HubSpot CRM API endpoints
- Execute CLI commands via MCP
- Interact with HubDB, GraphQL, and serverless functions
- Retrieve CRM, CMS, or code context for agent reasoning

**In short:** HubSpot MCP allows an LLM to act as a safe, scoped HubSpot development assistant.

## Why HubSpot Created MCP

HubSpot is introducing MCP to support an AI-native development workflow where agents autonomously assist in building, maintaining, and optimizing HubSpot solutions.

### Intended Use Cases

- Build or modify CMS modules and themes
- Refactor or modernize legacy HubL
- Query CRM objects and use results in code
- Create or update serverless functions
- Inspect portal schema and content
- Autogenerate workflows or content
- Implement CRM-driven personalization
- Automate HubDB or other data-heavy operations
- Setup Serverless Functions & Endpoints

MCP effectively becomes the API layer for AI-driven development inside HubSpot.

## Examples of Developer-Focused MCP Workflows

### AI-Driven Personalization Using CRM Context

A serverless function pulls CRM contact details and the AI agent updates HubL to personalize content.

**What MCP Facilitates:**

- CRM property access
- HubL snippet generation
- Module patching
- Deployment back to the portal
- Change logging

### Automated HubDB or GraphQL Content Management

For membership portals and data-rich builds, MCP can:

- Pull and inspect GraphQL schema
- Validate HubDB and CRM-linked structures
- Suggest schema fixes
- Read/write HubDB rows
- Autogenerate React components
- Produce documentation for data models

## Use Case Catalogue

### Use Case 1: AI-Assisted Theme Refactoring and Deployment

**Effort:** High  
**Value:** High

**Problem:**  
Themes grow complex over time and require refactoring, module updates, CSS modernization, and HubL cleanup.

**MCP Value:**

- Pull theme locally
- Suggest or implement refactoring
- Fix ESLint and formatting issues
- Update module.json file properties
- Deploy updates through MCP/CLI

**Metrics:**

- 30% reduction in manual development time
- 40% fewer deployment errors
- Faster onboarding for new developers

**Required Scopes:**

- `cms-source-access`
- `files.write`
- `content.write`

---

### Use Case 2: Membership Portal Enhancements via GraphQL + MCP

**Effort:** Medium  
**Value:** Very High

**Problem:**  
Membership portals rely on GraphQL for dashboards, permissions, and user data, but updates and performance tuning require manual effort.

**MCP Value:**

- Inspect and document GraphQL schema
- Suggest or generate optimized queries
- Build React components for dashboards
- Push updates to serverless functions
- Validate property usage and access control

**Metrics:**

- 25% reduction in GraphQL debugging time
- 50% faster development of new membership features
- More accurate and sustainable API usage

**Required Scopes:**

- `crm.objects.read`
- `hubdb.read`
- `cms-serverless.write`
- `graphql.schema.read`

---

### Use Case 3: Automated CRM Quality Auditing for Quotes and Data Projects

**Effort:** Low  
**Value:** High

**Problem:**  
Clients often have inconsistent CRM data, causing workflow failures and reporting issues.

**MCP Value:**

- Read CRM objects
- Identify missing or invalid property values
- Recommend workflow logic
- Autogenerate CRM "health dashboard" UI
- Create serverless endpoints for periodic audits

**Required Scopes:**

- `crm.objects.read`
- `crm.objects.write`
- `workflow.write`

---

### Use Case 4: Serverless Function Generation and Deployment ( showcase this )

**Effort:** Low to Medium
**Value:** High

**Problem:**
Developers frequently need to create serverless functions for custom logic, but writing boilerplate code, configuring endpoints, and managing deployments can be time-consuming and error-prone.

**MCP Value:**

- **Automated Function Scaffolding**: Use `create-cms-function` tool to generate complete serverless function structure with proper configuration
- **Intelligent Build Management**: Automatically handle webpack configuration updates, dependency installation, and build process troubleshooting
- **Deployment Automation**: Build and deploy functions directly to HubSpot, including runtime configuration and error resolution
- **Development Workflow**: Streamline the entire process from creation to deployment without manual CLI commands

**Example Workflow:**

```plaintext
1. Request: "Create a new serverless function"
2. MCP prompts for: filename, folder, endpoint path, HTTP method
3. MCP generates:
   - Function file with boilerplate code
   - serverless.json configuration
   - Updates webpack config if needed
4. MCP handles:
   - Dependency installation
   - Build process (with Node.js compatibility fixes)
   - Deployment to HubSpot portal
```

**Technical Details:**

- Creates function in `src/{folder}.functions/` structure
- Generates GET/POST endpoints with proper routing
- Includes sample API integration code (e.g., HubSpot Content Search)
- Manages webpack bundling for production deployment
- Automatically resolves common issues (Node.js version compatibility, missing dependencies)

**Required Scopes:**

- `cms.functions.write` - Create and deploy serverless functions
- `cms.functions.read` - Read existing function configurations

**Time Savings:**

- Manual process: 15-20 minutes (scaffolding, configuration, troubleshooting, deployment)
- With MCP: 2-3 minutes (mostly answering prompts)
- Eliminates common deployment errors and configuration mistakes

---

## Local Developer MCP Server: Should You Use It?

**Yes.** The local Developer MCP Server is exactly what HubSpot intends developers to use for experimentation and POC work.

A local setup lets the AI agent:

- Generate and edit code
- Inspect modules and files
- Query CRM or CMS data
- Inspect GraphQL schemas
- Push changes to HubSpot via the CLI

It is the most straightforward way to demonstrate MCP functionality.

## Recommended Next Steps

1. Install and configure the HubSpot Developer MCP Server locally
2. Finalize and document the three use cases above
3. Select one pilot POC (recommended: GraphQL Membership Portal Enhancer)
4. Use the MCP agent in the Demo Portal to:
   - Inspect GraphQL schema
   - Generate a HubL or React component
   - Write the output into the theme or repo
   - Capture screenshots or terminal output as supporting evidence
5. Prepare a short walkthrough to present to the AI/tech teams

```

```
