---
generated: '2026-10-09'
method: generated
name: bluebook-table-a1
title: Read BlueBook Table A1
description: List the published BlueBook Table A1 versions and read the latest one or a specific one.
api: openapi/equinor-bluebook-openapi.yml
operations:
- GetTableA1Versions
- GetLatestTableA1
- GetTableA1
source: Grounded in openapi/equinor-bluebook-openapi.yml (Azure API Management export from api.equinor.com). Every operationId
  was checked verbatim against the spec.
---

# Read BlueBook Table A1

List the published BlueBook Table A1 versions and read the latest one or a specific one.

## Auth
- Send your Equinor API portal (Azure API Management) subscription key as the `Ocp-Apim-Subscription-Key` header (or `subscription-key` query parameter), as declared in the spec's `securitySchemes`. Keys come from subscribing to a product at https://api.equinor.com/.
- Base URL: `https://api.gateway.equinor.com/bluebook` (the spec also lists an `api-ncc` gateway host where applicable).

## Steps
1. **GetTableA1Versions** (`GET /table-a1s`): List available versions.
2. **GetLatestTableA1** (`GET /table-a1s/latest`): Read the latest table.
3. **GetTableA1** (`GET /table-a1s/{version}`): Read a specific version.

## Notes
- Error responses are the status codes documented per operation in the spec (400/401/403/404/500, plus 429/504 where listed). No provider-specific problem-type catalog is published.
