# Arist

Arist is an AI-native enterprise enablement platform (founded 2019, New York City) that delivers
training, communications, nudges and surveys in the flow of work — over SMS, WhatsApp, Slack,
Microsoft Teams, email and its own web and mobile apps — instead of through a traditional LMS portal.
The product is packaged as an agent suite: a Needs Analysis agent, a Creator agent, a Core Platform +
Routing agent, and an Analytics agent.

- Website: https://arist.com/
- Help center / documentation: https://help.arist.co/
- Trust center: https://trust.arist.co/
- Status: https://status.arist.app/
- Login: https://arist.app/login
- Secondary market listing: https://forgeglobal.com/arist_stock/

## API posture

Arist publishes **no OpenAPI, no developer portal, no SDKs and no CLI**. Customer system
integrations (Workday, Salesforce, SAP SuccessFactors, Oracle, ServiceNow, Cornerstone) are built by
Arist through **Workato**, which stores the Arist API credentials on the customer's behalf.

Two real API hosts were found and probed:

| Host | Result |
|---|---|
| `api.arist.app` | Amazon API Gateway; every anonymous path (`/openapi.json`, `/swagger.json`, `/v1/openapi.json`, `/api-docs`, `/docs`, `/redoc`, `/graphql`) returns `403 MissingAuthenticationToken` |
| `auth.arist.app` | Auth0 tenant publishing a full **OpenID Connect Discovery / RFC 8414** document anonymously — the only machine-readable contract Arist publishes |

No A2A agent card, no MCP server, no AsyncAPI, no `security.txt`. `arist.app` and `status.arist.app`
answer 200 with an HTML shell for every `/.well-known/*` path — those are SPA catch-alls, not hits.

## Artifacts

| Dir | File | Method |
|---|---|---|
| `llms/` | `arist-llms.txt`, `arist-help-llms.txt` | searched (verbatim) |
| `well-known/` | `arist-well-known.yml`, `arist-openid-configuration.json`, `arist-oauth-authorization-server.json`, `arist-jwks.json` | searched |
| `authentication/` | `arist-authentication.yml` | searched |
| `scopes/` | `arist-scopes.yml` | searched |
| `security/` | `arist-domain-security.yml` | probed |
| `security/` | `arist-trust-center.yml` | searched |
| `conformance/` | `arist-conformance.yml` | searched |
| `lifecycle/` | `arist-lifecycle.yml` | searched |
| `changelog/` | `arist-changelog.yml` | searched |
| `conventions/` | `arist-conventions.yml` | searched |

Compliance: ISO 27001, ISO 27701, ISO 42001, SOC 2 Type 2 (Secureframe trust center; evidence
documents are request-gated).
