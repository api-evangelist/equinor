---
generated: '2026-10-09'
method: generated
name: query-alarms-and-events
title: Query alarms and events for a facility
description: List the facilities enabled for Alarm & Events, count events by priority, then retrieve events in a time window.
api: openapi/equinor-alarm-events-openapi.yml
operations:
- GetSources
- GetCounts
- GetEvents
source: Grounded in openapi/equinor-alarm-events-openapi.yml (Azure API Management export from api.equinor.com). Every operationId
  was checked verbatim against the spec.
---

# Query alarms and events for a facility

List the facilities enabled for Alarm & Events, count events by priority, then retrieve events in a time window.

## Auth
- Send your Equinor API portal (Azure API Management) subscription key as the `Ocp-Apim-Subscription-Key` header (or `subscription-key` query parameter), as declared in the spec's `securitySchemes`. Keys come from subscribing to a product at https://api.equinor.com/.
- Base URL: `https://api.gateway.equinor.com/iiot/ae` (the spec also lists an `api-ncc` gateway host where applicable).

## Steps
1. **GetSources** (`GET /sources`): List the facilities enabled for Alarm and Events.
2. **GetCounts** (`GET /events/{facility}/count`): Get event counts by priority for a `facility` between `startTime` and `endTime`.
3. **GetEvents** (`GET /events/{facility}`): Retrieve events; `sourceName` is required. Narrow with `startTime`/`endTime`, `eventType`, `description`; `sort` orders them.

## Notes
- Error responses are the status codes documented per operation in the spec (400/401/403/404/500, plus 429/504 where listed). No provider-specific problem-type catalog is published.
- For push delivery use `SetRealTimeDestination` (Azure EventHub only), then `CreateSubscriptions`.
