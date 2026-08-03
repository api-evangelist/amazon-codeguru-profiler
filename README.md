# Amazon CodeGuru Profiler

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Amazon CodeGuru Profiler collects runtime performance data from your live applications, providing recommendations to help you reduce CPU utilization, cut costs, and improve application performance. The profiler analyzes your application's CPU and heap usage to identify the most expensive lines of code and offers actionable recommendations.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/amazon-codeguru-profiler/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - Amazon, AWS, Application Performance, Profiling, DevOps, Machine Learning

## Timestamps

- **Created:** 2026-03-16
- **Modified:** 2026-04-19

## APIs

### Amazon CodeGuru Profiler API

The Amazon CodeGuru Profiler REST API.

**Human URL:** [https://docs.aws.amazon.com/codeguru/latest/profiler-api/Welcome.html](https://docs.aws.amazon.com/codeguru/latest/profiler-api/Welcome.html)

#### Tags:

 - Amazon, AWS, Application Performance, Profiling, DevOps

#### Properties

- [Documentation](https://docs.aws.amazon.com/codeguruprofiler/)
- [APIReference](https://docs.aws.amazon.com/codeguru/latest/profiler-api/Welcome.html)
- [OpenAPI](openapi/amazon-codeguru-profiler-openapi-original.yaml)

## Common Properties

- [GettingStarted](https://docs.aws.amazon.com/codeguru/profiler)
- [Pricing](https://aws.amazon.com/codeguruprofiler/pricing/)
- [Console](https://console.aws.amazon.com/codeguruprofiler/)
- [Portal](https://aws.amazon.com/codeguruprofiler/)
- [Documentation](https://docs.aws.amazon.com/codeguruprofiler/)
- [TermsOfService](https://aws.amazon.com/service-terms/)
- [PrivacyPolicy](https://aws.amazon.com/privacy/)
- [StatusPage](https://health.aws.amazon.com/health/status)
- [Blog](https://aws.amazon.com/blogs/devops/)
- [SignUp](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html)
- [GitHubOrganization](https://github.com/aws)

## Features

| Name | Description |
|------|-------------|
| Application Profiling | Continuously profile application CPU utilization and heap usage in production without significant overhead. |
| AI-Powered Recommendations | Receive actionable recommendations from machine learning models identifying expensive code paths and resource inefficien |
| Flame Graphs | Visualize CPU usage with flame graphs that highlight the most resource-intensive code paths. |
| Anomaly Detection | Automatically detect anomalies in application performance and CPU utilization patterns. |
| Java and Python Support | Profile JVM-based applications and Python applications using language-specific profiling agents. |

## Use Cases

| Name | Description |
|------|-------------|
| Production Performance Optimization | Identify and eliminate the most expensive code paths consuming CPU in live production applications. |
| Cost Reduction | Reduce compute costs by optimizing code that consumes excessive CPU time and cloud resources. |
| Latency Investigation | Investigate application latency issues by profiling which code paths contribute most to request processing time. |

## Integrations

| Name | Description |
|------|-------------|
| AWS Lambda | Profile Lambda function execution to identify performance bottlenecks. |
| Amazon ECS | Profile containerized applications running on ECS. |
| Amazon EC2 | Profile applications running on EC2 instances. |
| AWS CodeGuru Reviewer | Combine profiling insights with code review recommendations. |

## Artifacts

Machine-readable API specifications organized by format.

### OpenAPI

- [amazon-codeguru-profiler-openapi-original](openapi/amazon-codeguru-profiler-openapi-original.yaml)

### JSON Schema

122 JSON Schema files generated from the OpenAPI specification.

- [amazon-codeguru-profiler-action-group-schema](json-schema/amazon-codeguru-profiler-action-group-schema.json)
- [amazon-codeguru-profiler-add-notification-channels-request-schema](json-schema/amazon-codeguru-profiler-add-notification-channels-request-schema.json)
- [amazon-codeguru-profiler-add-notification-channels-response-schema](json-schema/amazon-codeguru-profiler-add-notification-channels-response-schema.json)
- [amazon-codeguru-profiler-agent-configuration-schema](json-schema/amazon-codeguru-profiler-agent-configuration-schema.json)
- [amazon-codeguru-profiler-agent-orchestration-config-schema](json-schema/amazon-codeguru-profiler-agent-orchestration-config-schema.json)
- ...and 117 more in [json-schema/](json-schema/)

### JSON Structure

122 JSON Structure files in [json-structure/](json-structure/).

### JSON-LD

- [amazon-codeguru-profiler-context](json-ld/amazon-codeguru-profiler-context.jsonld)

### Examples

122 example JSON files in [examples/](examples/).

## Capabilities

Naftiko capabilities organized as shared per-API definitions composed into customer-facing workflows.

### Shared Per-API Definitions

- [codeguruprofiler](capabilities/shared/codeguruprofiler.yaml) — 23 operations

### Workflow Capabilities

| Workflow | APIs Combined | Tools | Persona |
|----------|--------------|-------|---------|
| [Amazon CodeGuru Profiler Application Performance Profiling](capabilities/amazon-codeguru-profiler-application-performance.yaml) | codeguruprofiler | 8 | DevOps Engineer |

## Vocabulary

- [amazon-codeguru-profiler-vocabulary](vocabulary/amazon-codeguru-profiler-vocabulary.yaml) — Unified taxonomy mapping 4 resources, 5 actions, 1 workflows, and 3 personas

## Rules

- [amazon-codeguru-profiler-spectral-rules](rules/amazon-codeguru-profiler-spectral-rules.yml) — 10 rules enforcing Amazon CodeGuru Profiler API conventions

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
