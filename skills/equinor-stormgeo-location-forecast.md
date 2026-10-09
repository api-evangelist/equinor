---
generated: '2026-10-09'
method: generated
name: stormgeo-location-forecast
title: Get a StormGeo weather forecast for a location
description: List StormGeo locations and parameters, then fetch a forecast of a given type for one location.
api: openapi/equinor-stormgeo-openapi.yml
operations:
- get-locations
- get-parameters
- get-locations-id-forecasts-forecasttype
source: Grounded in openapi/equinor-stormgeo-openapi.yml (Azure API Management export from api.equinor.com). Every operationId
  was checked verbatim against the spec.
---

# Get a StormGeo weather forecast for a location

List StormGeo locations and parameters, then fetch a forecast of a given type for one location.

## Auth
- The StormGeo spec declares no securitySchemes, so the contract does not state the auth method. It is served through the same api.gateway.equinor.com gateway, but do not assume a key scheme the spec does not state.
- Base URL: `https://api.gateway.equinor.com/stormgeo/v1` (the spec also lists an `api-ncc` gateway host where applicable).

## Steps
1. **get-locations** (`GET /locations`): List available locations (`Filters`, `Sorts`, `PageSize`, `Page`). Capture a location `id`.
2. **get-parameters** (`GET /parameters`): List parameters you can request (see also `get-parameter-sets`).
3. **get-locations-id-forecasts-forecasttype** (`GET /locations/{id}/forecasts/{forecastType}`): Fetch the forecast. `parameterSetId`, `unitProfileId` and `timeResolution` are optional.

## Notes
- Error responses are the status codes documented per operation in the spec (400/401/403/404/500, plus 429/504 where listed). No provider-specific problem-type catalog is published.
