---
generated: '2026-10-09'
method: generated
name: lookup-ims-tag
title: Look up an IMS sensor tag
description: Search the IMS Metadata API for a sensor tag within a plant and fetch its full metadata.
api: openapi/equinor-ims-metadata-openapi.yml
operations:
- get-plant-search-tag
- get-plant-tag
source: Grounded in openapi/equinor-ims-metadata-openapi.yml (Azure API Management export from api.equinor.com). Every operationId
  was checked verbatim against the spec.
---

# Look up an IMS sensor tag

Search the IMS Metadata API for a sensor tag within a plant and fetch its full metadata.

## Auth
- Send your Equinor API portal (Azure API Management) subscription key as the `Ocp-Apim-Subscription-Key` header (or `subscription-key` query parameter), as declared in the spec's `securitySchemes`. Keys come from subscribing to a product at https://api.equinor.com/.
- Base URL: `https://api.gateway.equinor.com/plant/ims-metadata` (the spec also lists an `api-ncc` gateway host where applicable).

## Steps
1. **get-plant-search-tag** (`GET /{plant}/search/{tag}`): Search tags in a `plant`. Filter with `imsType`/`systemCode`; page with `limit` + `continuationToken`.
2. **get-plant-tag** (`GET /{plant}/{tag}`): Fetch the exact tag record by plant and tag name.

## Notes
- Error responses are the status codes documented per operation in the spec (400/401/403/404/500, plus 429/504 where listed). No provider-specific problem-type catalog is published.
- To search every plant use `get-search-tag` (GET /search/{tag}). `get-uid-uid` resolves a tag by its unique id.
