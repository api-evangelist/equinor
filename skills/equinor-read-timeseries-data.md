---
generated: '2026-10-09'
method: generated
name: read-timeseries-data
title: Read timeseries data
description: Find a timeseries in the Equinor Timeseries API, then read raw, latest or aggregated datapoints over a time window.
api: openapi/equinor-timeseries-openapi.yml
operations:
- GetSearch
- getTimeseriesById
- GetData
- GetLatest
- GetAggregatedData
source: Grounded in openapi/equinor-timeseries-openapi.yml (Azure API Management export from api.equinor.com). Every operationId
  was checked verbatim against the spec.
---

# Read timeseries data

Find a timeseries in the Equinor Timeseries API, then read raw, latest or aggregated datapoints over a time window.

## Auth
- Send your Equinor API portal (Azure API Management) subscription key as the `sub` header (or `sub` query parameter), as declared in the spec's `securitySchemes`. Keys come from subscribing to a product at https://api.equinor.com/.
- Base URL: `https://api.gateway.equinor.com/plant/timeseries` (the spec also lists an `api-ncc` gateway host where applicable).

## Steps
1. **GetSearch** (`GET /search`): Search timeseries by `name`, `description`, `unit`, `assetId` or `facility`. Page with `limit` + `continuationToken`. Capture the `id` of the match.
2. **getTimeseriesById** (`GET /{id}`): Confirm the metadata (unit, facility, source) of the chosen timeseries.
3. **GetData** (`GET /{id}/data`): Read datapoints between `startTime` and `endTime`. Follow `continuationToken` until it is absent.
4. **GetLatest** (`GET /{id}/data/latest`): Read the most recent datapoint only (optionally bounded by `beforeTime`/`afterTime`).
5. **GetAggregatedData** (`GET /{id}/data/aggregates`): Read aggregates; `aggregateFunction` is required, `processingInterval` sets the bucket size.

## Notes
- Error responses are the status codes documented per operation in the spec (400/401/403/404/500, plus 429/504 where listed). No provider-specific problem-type catalog is published.
- The spec documents 429 responses on these operations: back off and retry.
- For more than one series use the batch variants `GetMultipleData` (POST /query/data) and `GetMultipleLatest` (POST /query/data/latest). The spec caps each call at 100 series.
