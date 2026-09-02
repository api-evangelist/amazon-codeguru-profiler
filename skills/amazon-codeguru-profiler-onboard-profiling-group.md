---
name: amazon-codeguru-profiler-onboard-profiling-group
description: Create an Amazon CodeGuru Profiler profiling group, enable collection, and confirm the agent is reporting.
api: amazon-codeguru-profiler:amazon-codeguru-profiler-profilinggroups-api
generated: '2026-09-01'
method: generated
source: openapi/amazon-codeguru-profiler-profilinggroups-clienttoken-api-openapi.yml
operations:
  - CreateProfilingGroup
  - UpdateProfilingGroup
  - DescribeProfilingGroup
  - ListProfilingGroups
  - TagResource
---

# Onboard a profiling group

Stands up a new CodeGuru Profiler profiling group and verifies that a profiling agent has
started reporting into it.

## Before you start

- Every request is signed with **AWS Signature Version 4**. There is no API key or bearer
  token. The caller needs `codeguru-profiler:CreateProfilingGroup`,
  `codeguru-profiler:UpdateProfilingGroup` and `codeguru-profiler:DescribeProfilingGroup`.
- Base host is `codeguru-profiler.{region}.amazonaws.com` over HTTPS. Only ten regions are
  served — see `lifecycle/amazon-codeguru-profiler-lifecycle.yml`.
- The account quota is **500 profiling groups per region** (adjustable). Exceeding it returns
  `ServiceQuotaExceededException` (HTTP 402), not a validation error.

## Steps

1. **Check the name is free** — call `ListProfilingGroups`. Page with `maxResults` and
   `nextToken`; the absence of `nextToken` means you have the last page.

2. **Create the group** — call `CreateProfilingGroup`.
   - `clientToken` is a **required** query parameter and must be a UUID (1-64 chars, `[\w-]+`).
     It is the idempotency key: reuse the *same* token on every retry of the *same* logical
     create, and generate a *new* one for a genuinely new group. This is the only operation in
     the API where an idempotency token is mandatory.
   - Set `computePlatform` to `AWSLambda` for Lambda functions, or `Default` for EC2, ECS, EKS,
     Fargate and on-premises. If omitted it defaults to `Default`.
   - `profilingGroupName` is 1-255 chars matching `[\w-]+` and is the natural key.
   - Pass `tags` here rather than calling `TagResource` afterwards — it saves a round trip.
   - Success returns **HTTP 201** with the `ProfilingGroupDescription`, including the `arn`.

3. **Enable collection** — call `UpdateProfilingGroup` with
   `agentOrchestrationConfig.profilingEnabled = true`. Read the current value with
   `DescribeProfilingGroup` first if you may need to reapply the previous state; this operation
   has no revision guard.

4. **Confirm the agent is reporting** — call `DescribeProfilingGroup` and read
   `profilingStatus.latestAgentOrchestratedAt` and
   `profilingStatus.latestAgentProfileReportedAt`. Both are ISO 8601 timestamps. Until the agent
   has posted at least once, `latestAgentProfileReportedAt` will be absent — that is expected,
   not an error. Agents report on a five-minute cadence.

## Errors to handle

| Exception | HTTP | What to do |
|---|---|---|
| `ValidationException` | 400 | Fix the parameter; do not retry unchanged. |
| `ConflictException` | 409 | A group with that name already exists, or the state changed under you. Re-read and decide. |
| `ServiceQuotaExceededException` | 402 | At the 500-group quota. Delete an unused group or request an increase; retrying will not help. |
| `ThrottlingException` | 429 | Retry with exponential backoff and jitter. No `Retry-After` header is returned. |
| `InternalServerException` | 500 | Retry after a delay — reusing the same `clientToken`. |

## Reversibility

`DeleteProfilingGroup` reverses the create, but it is **destructive and has no undo**: it takes
the group's aggregated profiles, findings reports and notification configuration with it, and
recreating the same name does not restore any of it. AWS publishes no restore window. Treat
deletion as terminal and confirm with a human before calling it.
