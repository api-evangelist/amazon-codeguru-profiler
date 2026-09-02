---
name: amazon-codeguru-profiler-read-recommendations
description: Pull CodeGuru Profiler findings, recommendations and anomalies for a profiling group over a time range, and send feedback on an anomaly.
api: amazon-codeguru-profiler:amazon-codeguru-profiler-internal-api
generated: '2026-09-01'
method: generated
source: openapi/amazon-codeguru-profiler-internal-api-openapi.yml
operations:
  - GetFindingsReportAccountSummary
  - ListFindingsReports
  - GetRecommendations
  - SubmitFeedback
  - BatchGetFrameMetricData
---

# Read profiler findings and recommendations

Retrieves what CodeGuru Profiler concluded about an application's CPU behaviour, and optionally
tells the service whether a detected anomaly was useful.

## Steps

1. **Scan the account** — call `GetFindingsReportAccountSummary` to get
   `FindingsReportSummary` objects across every profiling group in the account and region.
   Optional `dailyReportsOnly` narrows to daily reports. Page with `maxResults` / `nextToken`.
   Use this to decide *which* group is worth looking at before pulling detail.

2. **List reports for one group** — call `ListFindingsReports` with `profilingGroupName`,
   `startTime` and `endTime` (all ISO 8601). Each summary carries `id`,
   `profileStartTime`, `profileEndTime` and `totalNumberOfFindings`.

3. **Get the recommendations** — call `GetRecommendations` with `profilingGroupName`,
   `startTime` and `endTime`. Optional `locale` selects the language of the human-readable text.
   The response carries two distinct things, and they are not the same:
   - `recommendations[]` — each has a `pattern` (`id`, `name`, `description`,
     `resolutionSteps`, `thresholdPercent`) plus `topMatches[]` with `frameAddress` and
     `thresholdBreachValue`. This is the actionable "fix this code" output.
   - `anomalies[]` — each has a `metric`, a `reason`, and `instances[]` with start/end times
     and any existing `userFeedback`. This is "something changed", not "here is the fix".

4. **Drill into a frame over time** — call `BatchGetFrameMetricData` with `frameMetrics`,
   `startTime`, `endTime`, `period` and `targetResolution` to get the time series behind a
   recommendation. `unprocessedEndTimes` in the response lists windows the service could not
   compute — treat those as missing data, not as zeroes.

5. **Send feedback (optional)** — call `SubmitFeedback` with `profilingGroupName`,
   `anomalyInstanceId` and a feedback `type` of `Positive` or `Negative`. Returns **HTTP 204**.
   Feedback can be re-submitted but **cannot be withdrawn**; there is no delete-feedback
   operation.

## Conventions that apply

- Pagination is cursor-based (`nextToken` / `maxResults`) on the two list operations. Neither
  `GetRecommendations` nor `BatchGetFrameMetricData` paginates — bound them with a narrower
  time range instead.
- Only `ListProfileTimes` supports `orderBy`; these operations have no sort control.
- Errors are AWS JSON exceptions, not RFC 9457 problem+json. Read `x-amzn-ErrorType` for the
  exception name and quote `x-amzn-RequestId` to AWS Support.
- `ResourceNotFoundException` (404) here usually means the profiling group name is wrong or is
  in a different region — the API is regional and names are not global.
- This flow is read-only apart from step 5, so idempotency and dry-run do not apply.
