---
name: amazon-codeguru-profiler-configure-anomaly-notifications
description: Attach, inspect and detach Amazon SNS anomaly-notification channels on a CodeGuru Profiler profiling group.
api: amazon-codeguru-profiler:amazon-codeguru-profiler-profilinggroups-api
generated: '2026-09-01'
method: generated
source: openapi/amazon-codeguru-profiler-profilinggroups-api-openapi.yml
operations:
  - AddNotificationChannels
  - GetNotificationConfiguration
  - RemoveNotificationChannel
---

# Configure anomaly notifications

Routes CodeGuru Profiler anomaly events to an Amazon SNS topic you own.

## What this surface actually is

CodeGuru Profiler does **not** deliver HTTP webhooks. It publishes to an SNS topic ARN that you
register against a profiling group. Delivery, retry, fan-out and signing are SNS's
responsibility, not the Profiler API's. There is no published schema for the notification
message body — the API models the *subscription*, not the *payload*. Plan for that gap before
building a consumer.

## Steps

1. **Read the current configuration first** — call `GetNotificationConfiguration` with
   `profilingGroupName`. `AddNotificationChannels` is additive, and the group accepts a
   **maximum of two channels**, so adding blind is how you hit
   `ServiceQuotaExceededException` (HTTP 402).

2. **Add a channel** — call `AddNotificationChannels` with `profilingGroupName` and a
   `channels[]` array of 1-2 `Channel` objects:
   - `uri` (required) — a valid SNS topic ARN.
   - `eventPublishers` (required) — the only accepted value is `AnomalyDetection`.
   - `id` (optional) — supply your own channel id, or the service generates a random UUID.
     **Supply your own if you intend to remove the channel later**, because
     `RemoveNotificationChannel` addresses the channel by `channelId` and a generated one has to
     be read back out of the response.

   Returns HTTP 200 with the full new `NotificationConfiguration`.

3. **Detach a channel** — call `RemoveNotificationChannel` with `profilingGroupName` and
   `channelId`. Returns the remaining configuration.

## Errors to handle

| Exception | HTTP | What to do |
|---|---|---|
| `ValidationException` | 400 | The ARN is malformed, or `eventPublishers` is not `AnomalyDetection`. |
| `ServiceQuotaExceededException` | 402 | Already at two channels. Remove one first. |
| `ConflictException` | 409 | Concurrent change to the notification configuration; re-read and retry. |
| `ResourceNotFoundException` | 404 | The profiling group — or, on remove, the channel id — does not exist in this region. |
| `ThrottlingException` | 429 | Exponential backoff with jitter; no `Retry-After` is returned. |

## Reversibility

Add and remove are exact inverses and neither destroys data, so this is the safest write
surface in the API. AWS publishes **no time window** on the reversal — none is assumed here.
Capture the channel `id` from the add response so the reversal is a single call.
