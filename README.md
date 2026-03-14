# spec2cli-registry

Community-maintained registry of OpenAPI specs for [spec2cli](https://github.com/lucianfialho/spec2cli).

## How it works

spec2cli fetches this registry to discover available API templates. Run:

```bash
npx spec2cli search payments    # search by keyword
npx spec2cli use stripe --help  # use an API from the registry
```

## Adding a new API

1. Fork this repo
2. Create a JSON file in `apis/` with your API name (e.g. `apis/twilio.json`)
3. Follow this format:

```json
{
  "name": "twilio",
  "description": "Twilio API — SMS, voice, video, email",
  "categories": ["communications", "sms", "voice"],
  "specUrl": "https://raw.githubusercontent.com/twilio/twilio-oai/main/spec/json/twilio_api_v2010.json",
  "baseUrl": "https://api.twilio.com",
  "authType": "bearer",
  "authEnvVar": "TWILIO_AUTH_TOKEN",
  "docs": "https://www.twilio.com/docs/usage/api"
}
```

4. Open a pull request

## Fields

| Field | Required | Description |
|---|---|---|
| `name` | Yes | Short name (lowercase, used as `spec2cli use <name>`) |
| `description` | Yes | One-line description |
| `categories` | Yes | Array of category tags for search |
| `specUrl` | Yes | URL to the OpenAPI 3.x spec (YAML or JSON) |
| `baseUrl` | Yes | Default API base URL |
| `authType` | Yes | `bearer`, `apiKey`, or `none` |
| `authEnvVar` | No | Environment variable name for the API key/token |
| `authHeader` | No | Custom header name (for apiKey type, defaults to X-API-Key) |
| `docs` | No | Link to API documentation |

## Requirements

- The spec must be OpenAPI 3.x (YAML or JSON)
- The `specUrl` must be publicly accessible
- The `baseUrl` must be the production API endpoint
- One API per file
