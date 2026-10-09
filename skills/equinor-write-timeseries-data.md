---
generated: '2026-10-09'
method: generated
name: write-timeseries-data
title: Create a timeseries and write datapoints
description: Get or create timeseries metadata, then add or update its datapoints.
api: openapi/equinor-timeseries-openapi.yml
operations:
- GetOrAddTimeseries
- writeData
- GetLatest
source: Grounded in openapi/equinor-timeseries-openapi.yml (Azure API Management export from api.equinor.com). Every operationId
  was checked verbatim against the spec.
---

# Create a timeseries and write datapoints

Get or create timeseries metadata, then add or update its datapoints.

## Auth
- Send your Equinor API portal (Azure API Management) subscription key as the `sub` header (or `sub` query parameter), as declared in the spec's `securitySchemes`. Keys come from subscribing to a product at https://api.equinor.com/.
- Base URL: `https://api.gateway.equinor.com/plant/timeseries` (the spec also lists an `api-ncc` gateway host where applicable).

## Steps
1. **GetOrAddTimeseries** (`POST /getoradd`): Get or create the timeseries metadata in one call. This is the idempotent-style entry point; `postTimeseries` (POST /) always creates. Capture the returned `id`.
2. **writeData** (`POST /{id}/data`): Add or update datapoints for that `id`. Pass `async=true` to get a 202 accepted response instead of 200.
3. **GetLatest** (`GET /{id}/data/latest`): Read back the last datapoint to verify the write.

## Notes
- Error responses are the status codes documented per operation in the spec (400/401/403/404/500, plus 429/504 where listed). No provider-specific problem-type catalog is published.
- A 409 on `GetOrAddTimeseries` is documented: treat it as a conflict, not a transient error.
- `writeMultipleData` (POST /data) writes to several series in one request.
