# Amazon CodeGuru Profiler

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
