# Hosted Specs

This directory contains OpenAPI specs that were patched from their original sources to fix issues that prevent them from being consumed by spec2cli or other strict OpenAPI tooling.

Each spec here is referenced by an entry in `apis/` via the raw GitHub URL.

## Why patch upstream specs?

Some vendors ship specs with:
- Invalid OpenAPI 3.x syntax (e.g. Swagger 2.0 `$ref` paths inside an OpenAPI 3.x document)
- Protocol-relative server URLs
- Non-standard path parameter syntax (e.g. `<id>` instead of `{id}`)
- Missing or malformed `securitySchemes`

When that happens we mirror a corrected copy here and pin the entry in `apis/` to this version, with a comment in the spec explaining what was changed.

## Specs

- `sympla.yaml` — Sympla API. Original at https://developers.sympla.com.br/api-doc/swagger.yaml had: protocol-relative server URL, `$ref: '#/parameters/...'` (Swagger 2 syntax inside OpenAPI 3.1), top-level `parameters:` block instead of `components.parameters`, `<presentation_id>` path params, and no global `security:` declaration. All five fixed here.
