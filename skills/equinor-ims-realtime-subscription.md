---
generated: '2026-10-09'
method: generated
name: ims-realtime-subscription
title: Manage IMS real-time data subscriptions
description: Point real-time IMS data at an Event Hub, subscribe to sensor timeseries, list subscriptions and delete them.
api: openapi/equinor-ims-export-subscriptions-openapi.yml
operations:
- SetRealTimeDestination
- CreateRealTimeSubscription
- ListRealTimeSubscriptions
- DeleteRealTimeSubscription
source: Grounded in openapi/equinor-ims-export-subscriptions-openapi.yml (Azure API Management export from api.equinor.com).
  Every operationId was checked verbatim against the spec.
---

# Manage IMS real-time data subscriptions

Point real-time IMS data at an Event Hub, subscribe to sensor timeseries, list subscriptions and delete them.

## Auth
- Send your Equinor API portal (Azure API Management) subscription key as the `sub` header (or `sub` query parameter), as declared in the spec's `securitySchemes`. Keys come from subscribing to a product at https://api.equinor.com/.
- Base URL: `https://api.gateway.equinor.com/plant/ims-subscriptions` (the spec also lists an `api-ncc` gateway host where applicable).

## Steps
1. **SetRealTimeDestination** (`POST /realtime/destination`): Set the Event Hub destination for real-time data.
2. **CreateRealTimeSubscription** (`POST /realtime`): Create the subscription (201). Bound it with `lifeTime` or `expirationTime`.
3. **ListRealTimeSubscriptions** (`GET /realtime`): List your subscriptions; `excludeExpired` hides lapsed ones. Page with `continuationToken`.
4. **DeleteRealTimeSubscription** (`DELETE /realtime/timeseriesid/{timeseriesId}`): Remove a subscription by timeseries id (`DeleteRealTimeSubscriptionByUid` removes one by uid).

## Notes
- Error responses are the status codes documented per operation in the spec (400/401/403/404/500, plus 429/504 where listed). No provider-specific problem-type catalog is published.
