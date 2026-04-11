<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table of Contents

- [Acknowledgements](#acknowledgements)
- [Abstract](#abstract)
  - [Keywords](#keywords)
  - [Introduction](#introduction)
- [Motivation](#motivation)
- [Objective](#objective)
- [Methodology](#methodology)
- [Structure](#structure)
  - [Analysis](#analysis)
- [Asset Discovery and Inventory](#asset-discovery-and-inventory)
  - [Application Portfolio Management](#application-portfolio-management)
  - [Configuration Management Databases](#configuration-management-databases)
  - [Integration Options](#integration-options)
        - [ServiceNow APIs](#servicenow-apis)
        - [ServiceNow Application](#servicenow-application)
        - [Integration Challenges](#integration-challenges)
  - [Cloud Asset Discovery](#cloud-asset-discovery)
  - [Cross-Layer Correlation](#cross-layer-correlation)
- [Software Development](#software-development)
  - [Source Code Management](#source-code-management)
  - [Continuous Integration and Delivery](#continuous-integration-and-delivery)
  - [Issue Tracking](#issue-tracking)
- [Static Application Security](#static-application-security)
  - [Static Application Security Testing](#static-application-security-testing)
  - [Software Composition Analysis](#software-composition-analysis)
  - [Secret Detection](#secret-detection)
  - [Container Image Scanning](#container-image-scanning)
  - [Infrastructure as Code Security](#infrastructure-as-code-security)
- [Dynamic Application Security](#dynamic-application-security)
  - [Dynamic Application Security Testing](#dynamic-application-security-testing)
  - [Penetration Testing](#penetration-testing)
  - [Web Application Firewalls](#web-application-firewalls)
  - [Runtime Application Self-Protection](#runtime-application-self-protection)
  - [Runtime API Security](#runtime-api-security)
  - [Vulnerability Management and Cloud Posture](#vulnerability-management-and-cloud-posture)
  - [Source Integration Summary](#source-integration-summary)
- [Data Engineering](#data-engineering)
  - [Data Platform Architecture](#data-platform-architecture)
  - [Data Integration Patterns](#data-integration-patterns)
  - [Domain Data Model](#domain-data-model)
- [Related Work and Gap Analysis](#related-work-and-gap-analysis)
  - [Existing Approaches](#existing-approaches)
  - [Databricks Lakewatch](#databricks-lakewatch)
  - [Comparative Analysis and Research Gap](#comparative-analysis-and-research-gap)
  - [Framework](#framework)
- [Solution Architecture](#solution-architecture)
  - [Component Design](#component-design)
  - [Medallion Architecture](#medallion-architecture)
  - [Technology Stack](#technology-stack)
- [Data Model](#data-model)
  - [Schema Patterns](#schema-patterns)
  - [Entity Model](#entity-model)
  - [Aggregation Model](#aggregation-model)
- [Connector Framework](#connector-framework)
  - [Connector Abstraction](#connector-abstraction)
  - [Ingestion Patterns](#ingestion-patterns)
  - [Transformation Patterns](#transformation-patterns)
- [Analytics and Serving Layer](#analytics-and-serving-layer)
  - [Aggregation Patterns](#aggregation-patterns)
  - [ML Workflows](#ml-workflows)
  - [Serving Patterns](#serving-patterns)
- [Deployment and Engineering Practices](#deployment-and-engineering-practices)
  - [Deployment Strategy](#deployment-strategy)
  - [Project Structure](#project-structure)
  - [Testing Strategy](#testing-strategy)
  - [Implementation](#implementation)
- [Environment and Deployment](#environment-and-deployment)
  - [Workspace Setup](#workspace-setup)
  - [Silver Schema](#silver-schema)
  - [Project Structure and CI/CD](#project-structure-and-cicd)
- [Connectors](#connectors)
  - [ServiceNow](#servicenow)
  - [GitHub](#github)
  - [GitLab](#gitlab)
  - [SonarQube](#sonarqube)
  - [Semgrep](#semgrep)
  - [Dependency-Track](#dependency-track)
  - [TruffleHog](#trufflehog)
  - [Vulnerability Enrichment](#vulnerability-enrichment)
- [Analytics and Serving](#analytics-and-serving)
  - [Application-Repository Mapping](#application-repository-mapping)
  - [Application Risk Scoring](#application-risk-scoring)
  - [Remediation and Compliance Metrics](#remediation-and-compliance-metrics)
  - [Vulnerability Trends](#vulnerability-trends)
  - [Risk Prediction Model](#risk-prediction-model)
  - [Serving Layer](#serving-layer)
- [Testing and Validation](#testing-and-validation)
  - [Conclusion](#conclusion)
- [Thesis Outcomes and Contributions](#thesis-outcomes-and-contributions)
- [Limitations](#limitations)
- [Future Work](#future-work)
- [Appendices](#appendices)
  - [Generative AI Use Disclosure](#generative-ai-use-disclosure)
- [Text Content](#text-content)
- [Diagrams and Figures](#diagrams-and-figures)
- [Source Code](#source-code)
- [Requirements Specification](#requirements-specification)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<div class="center">

Prague University of Economics and Business  
Faculty of Informatics and Statistics

=0

<embed src="img/FIS_2_logo_2_rgb_EN.pdf" />

<img src="img/FIS_2_logo_2_rgb_CZ" alt="image" />

**A Data Integration Framework  
for Enterprise Application Security**

MASTER’S THESIS

|                |                                                    |
|---------------:|:---------------------------------------------------|
| Study program: | Applied Data Analytics and Artificial Intelligence |
|                | Retail and E-Commerce Data Analytics               |
|                |                                                    |

|             |                   |
|------------:|:------------------|
|     Author: | Bc. Vojtěch Kraus |
| Supervisor: | Ing. Aleš Kotuč   |
|             |                   |
|             |                   |

Prague, month YYYY

</div>

### Acknowledgements

I would like to thank Ing. Aleš Kotuč for his guidance and valuable
feedback.

### Abstract

To protect their business-critical applications from cybersecurity
threats, enterprise security teams rely on numerous tools to detect and
resolve vulnerabilities in application source code, configuration,
dependencies, CI/CD pipelines, and runtime infrastructure. These tools
use different integration patterns, protocols, and data formats, making
it difficult to consistently parse, deduplicate, triage, and group their
findings. In large environments, additional challenges emerge when
linking all findings to the corresponding business applications. This
thesis presents a data framework to tackle those challenges, delivering
three distinct contributions: (1) a requirements specification for an
application security data platform, (2) a reusable and extensible design
covering architecture, data model, and medallion-based data pipeline,
and (3) a reference implementation built on the Databricks platform.
Together, these contributions offer application security teams a
foundation for building a robust data platform independent of individual
cybersecurity vendors, relieving them of risks usually associated with
vendor lock-in.

#### Keywords

application security, software security, DevSecOps, security
integration, data consolidation, medallion architecture, Databricks

## Introduction

### Motivation

### Objective

### Methodology

### Structure

## Analysis

This chapter surveys the literature and analyzes the functional domains
relevant to building an application security data platform. Each section
covers one domain, combining theoretical foundations with practical tool
and <span acronym-label="api" acronym-form="singular+short">api</span>
analysis. The focus is on reviewing existing knowledge, observing source
system interfaces, data models, and integration patterns, not on
prescribing a solution. Technology choices for the target platform are
deferred to <a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> and
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>.

<a href="#sec:app-inventory" data-reference-type="autoref"
data-reference="sec:app-inventory">[sec:app-inventory]</a> establishes
the business and infrastructure asset context underlying all security
findings. <a href="#sec:sw-dev-analysis" data-reference-type="autoref"
data-reference="sec:sw-dev-analysis">[sec:sw-dev-analysis]</a> examines
software development platforms as data sources. Application security
tooling is split into two sections:
<a href="#sec:static-appsec" data-reference-type="autoref"
data-reference="sec:static-appsec">[sec:static-appsec]</a> covers tools
that analyze source code and build artifacts before deployment, while
<a href="#sec:dynamic-appsec" data-reference-type="autoref"
data-reference="sec:dynamic-appsec">[sec:dynamic-appsec]</a> covers
tools that test running applications and monitor deployed
infrastructure. This separation reflects a fundamental difference in how
findings are produced and correlated: static tools identify targets by
repository and file path, while dynamic tools identify targets by
<span acronym-label="url" acronym-form="singular+short">url</span>,
host, or cloud resource, requiring different integration strategies.
<a href="#sec:data-eng-analysis" data-reference-type="autoref"
data-reference="sec:data-eng-analysis">[sec:data-eng-analysis]</a>
covers the data engineering patterns that underpin the framework’s
design. Finally,
<a href="#sec:related-work" data-reference-type="autoref"
data-reference="sec:related-work">[sec:related-work]</a> surveys
existing solutions and identifies the gap this thesis addresses.

### Asset Discovery and Inventory

Asset discovery and inventory is the foundational data source for any
application security data platform. It establishes the business context
for all security findings. On the business side, organizations maintain
application inventories in a <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> or a custom-built catalog. On
the infrastructure side, cloud providers and container orchestrators
expose asset inventories through <span acronym-label="api"
acronym-form="plural+short">apis</span>. Without a reliable catalog of
business applications and their mapping to technical and infrastructure
assets, a vulnerability discovered in a repository or a running service
cannot be attributed to an owner, assessed for business impact, or
prioritized against organizational risk criteria.

#### Application Portfolio Management

Enterprise organizations maintain catalogs of their business
applications with metadata such as application name, description,
ownership information, lifecycle status, and relationships to other
assets .

These registries also capture security-relevant attributes. Information
security is commonly assessed along three dimensions known as the
<span acronym-label="cia" acronym-form="singular+short">cia</span>
triad: confidentiality (preventing unauthorized disclosure), integrity
(preventing unauthorized modification), and availability (ensuring
authorized access) . Business impact assessments evaluate all three
<span acronym-label="cia" acronym-form="singular+short">cia</span>
dimensions to produce criticality ratings, commonly structured as tiers:
Tier 1 for mission-critical applications, Tier 2 for important
supporting systems, and Tier 3 for non-critical internal tools.
Separately, regulatory scope flags identify which compliance frameworks
apply to a given application, further contributing to the security
requirement set.

The most important attribute from a data integration perspective is the
mapping between business applications and their technical assets. A
single business application may span multiple source code repositories,
microservices, infrastructure components, and deployment environments.
This mapping serves as the glue connecting technical security findings
to business context. When the framework ingests a vulnerability from a
<span acronym-label="sast" acronym-form="singular+short">sast</span>
scanner linked to a specific repository, the application inventory
mapping determines which business application is affected, who owns it,
and how critical it is. This enables the risk-aware prioritization that
stakeholders require.

#### Configuration Management Databases

The most common <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> platform in enterprise
environments is ServiceNow, holding over 44% of the global
<span acronym-label="itsm" acronym-form="singular+short">itsm</span>
market share . It serves as the reference platform for this thesis. A
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
organizes all managed assets as <span acronym-label="ci"
acronym-form="plural+short">cis</span>, each with attributes describing
its type, status, and ownership .

ServiceNow arranges <span acronym-label="ci"
acronym-form="plural+short">cis</span> in a class hierarchy rooted at
the `cmdb_ci` base table. Each subclass inherits base attributes (name,
`sys_id`, operational status, environment) and adds domain-specific
fields. For application inventory purposes, the most relevant class is
`cmdb_ci_appl` (Application), which extends the base
<span acronym-label="ci" acronym-form="singular+short">ci</span> with
attributes such as version, business unit, used-for classification, and
references to the owning support group .

Beyond the application record itself, the <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> captures relationships between
<span acronym-label="ci" acronym-form="plural+short">cis</span> through
a dedicated relationship table (`cmdb_rel_ci`). These relationships
model dependencies such as “runs on” (application to server), “depends
on” (application to database), and “hosted on” (application to cloud
service). For the framework, the most valuable relationships are those
linking business applications to technical assets that correspond to
entities in the security data: repository names, deployment targets, and
infrastructure components. ServiceNow also allows organizations to
define custom attributes and relationship types, so the specific fields
available for ingestion may vary between deployments.

#### Integration Options

Integrating <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> data into an external data
platform requires choosing between two strategies: pulling data from
ServiceNow via its <span acronym-label="api"
acronym-form="plural+short">apis</span>, or pushing data from a custom
ServiceNow application to an external target.

##### ServiceNow APIs

ServiceNow exposes two complementary <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> for <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> data extraction. The Table
<span acronym-label="api" acronym-form="singular+short">api</span>
provides generic CRUD operations against any ServiceNow table through
the endpoint `/api/now/table/{tableName}` . Responses are
<span acronym-label="json"
acronym-form="singular+short">json</span>-formatted, with support for
server-side filtering (`sysparm_query`), field selection
(`sysparm_fields`), and pagination via `sysparm_limit` and
`sysparm_offset` (default maximum of 10 000 records per request). The
`sysparm_display_value` parameter resolves reference fields to
human-readable names instead of internal `sys_id` values.

The <span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
Instance <span acronym-label="api"
acronym-form="singular+short">api</span>
(`/now/cmdb/instance/{className}`) provides a <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span>-aware alternative that
understands the <span acronym-label="ci"
acronym-form="singular+short">ci</span> class hierarchy . It can
retrieve a <span acronym-label="ci"
acronym-form="singular+short">ci</span> with its relationships in a
single call, reducing the number of <span acronym-label="api"
acronym-form="singular+short">api</span> calls needed to reconstruct the
application-to-asset mapping. However, it is more constrained in its
query capabilities than the Table <span acronym-label="api"
acronym-form="singular+short">api</span>.

Both <span acronym-label="api" acronym-form="plural+short">apis</span>
require authentication, typically through Basic Authentication with a
service account granted the `rest_service` or `cmdb_read` role, or
through OAuth 2.0 for more security-conscious deployments. Rate limits
vary by instance configuration and are governed by platform transaction
quotas rather than per-endpoint limits. For incremental data extraction,
the `sys_updated_on` timestamp field present on all records serves as a
reliable high-water mark, allowing consumers to query only records
modified since the last extraction.

Any pull-based integration must handle authentication, pagination, rate
limiting, and incremental state management. Several integration
libraries and platform-native connectors abstract these concerns; the
specific tooling choice depends on the target data platform and is
discussed in
<a href="#sec:servicenow-impl" data-reference-type="autoref"
data-reference="sec:servicenow-impl">[sec:servicenow-impl]</a>.

##### ServiceNow Application

An alternative to pulling data is to push it from the source. ServiceNow
supports building scoped applications that run on the platform itself. A
custom application can use Outbound REST Messages to send
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
data to an external target (e.g., a cloud storage bucket or a
<span acronym-label="rest" acronym-form="singular+short">rest</span>
endpoint) on a schedule defined through Scheduled Jobs or Flow Designer.
The application can also expose a Scripted <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> , a custom endpoint that shapes
the data exactly as the consumer needs it, pre-joining application
records with their relationships and custom attributes in a single
response.

The advantage is full access to ServiceNow’s internal scripting
capabilities, relationship traversal, and business logic without
external <span acronym-label="api"
acronym-form="singular+short">api</span> call overhead. The disadvantage
is that development and maintenance happen inside the ServiceNow
platform, requiring ServiceNow development expertise and a separate
deployment lifecycle. Changes to the <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> schema or extraction logic
must be coordinated across two platforms. This approach is best suited
for organizations with mature ServiceNow development teams that prefer
to own the data export logic on the source side.

##### Integration Challenges

In implementation phase, the application inventory presents the most
significant integration challenge among all data sources because it is
the least standardized. Security testing tools converge around common
<span acronym-label="api" acronym-form="singular+short">api</span>
patterns and output formats, but each organization structures its
application inventory differently: the hierarchy of applications, the
granularity of asset mapping, and the attributes captured vary
substantially . This makes the application inventory connector the
hardest to generalize and the one most likely to require
implementation-specific customization.

Data quality in <span acronym-label="cmdb"
acronym-form="plural+short">cmdbs</span> is a persistent concern .
Application records may be incomplete (missing ownership or criticality
assignments), outdated (reflecting decommissioned applications still
listed as active), or inconsistently maintained across business units.
Any integration must account for these quality issues through validation
rules and default values that surface problems without blocking the data
pipeline.

Despite these difficulties, the application inventory is indispensable.
Without the business context it provides, security findings lack the
organizational meaning needed for effective prioritization and
governance.

#### Cloud Asset Discovery

Major cloud providers offer asset inventory <span acronym-label="api"
acronym-form="plural+short">apis</span>. <span acronym-label="aws"
acronym-form="singular+short">aws</span> Config maintains a continuously
updated resource inventory through a <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span>. Azure Resource Graph supports
a query language for cross-subscription metadata retrieval. Google Cloud
provides the Cloud Asset Inventory <span acronym-label="api"
acronym-form="singular+short">api</span>. All three offer mature
<span acronym-label="sdk" acronym-form="plural+short">sdks</span> that
abstract authentication, pagination, and retry logic. Kubernetes exposes
workload metadata (deployments, pods, container specifications) through
its <span acronym-label="api" acronym-form="singular+short">api</span>,
enabling the framework to trace from runtime workloads to container
images and, through <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> metadata, to source
repositories.

Cloud asset data serves as the infrastructure counterpart to the
business application inventory in the preceding subsections. While the
application inventory maps business applications to repositories and
teams, cloud asset discovery maps applications to their runtime
infrastructure: compute instances, containers, load balancers, and
network configurations. Joining these two inventories enables the
framework to link security findings from any layer to both code owners
and infrastructure owners.

#### Cross-Layer Correlation

The central challenge in asset inventory is correlating identifiers
across layers. Security tools that analyze source code identify targets
by repository, file path, and code location. Tools that operate on
running infrastructure identify targets by host, container, cloud
resource, or <span acronym-label="url"
acronym-form="singular+short">url</span>. Bridging these two coordinate
systems requires the application-to-asset mapping described in the
preceding subsections, which serves as the joining entity linking
runtime infrastructure to business applications and their source
repositories.

This correlation enables cross-layer analyses: tracing a runtime
vulnerability to the code that introduced it, linking a
<span acronym-label="waf" acronym-form="singular+short">waf</span> alert
to the responsible application and team, or determining which
<span acronym-label="iac" acronym-form="singular+short">iac</span>
finding corresponds to a live <span acronym-label="cspm"
acronym-form="singular+short">cspm</span> detection. Without it,
findings from dynamic security tools
(<a href="#sec:dynamic-appsec" data-reference-type="autoref"
data-reference="sec:dynamic-appsec">[sec:dynamic-appsec]</a>) remain
isolated from the development context, limiting their actionability. The
data model in <a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> addresses this by
defining explicit relationships between application entities,
infrastructure assets, and security findings across all layers.

### Software Development

Modern software is built collaboratively from source code, organized in
repositories, and deployed through automated pipelines . While
<a href="#sec:app-inventory" data-reference-type="autoref"
data-reference="sec:app-inventory">[sec:app-inventory]</a> established
the business context for security findings, the platforms that support
software development provide the technical entities around which those
findings are organized. Repositories, build pipelines, and issue
trackers form the second major data source category for the framework.

These platforms share common integration patterns that simplify
connector design. All expose <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> with <span acronym-label="json"
acronym-form="singular+short">json</span> responses as the primary
integration surface. Authentication relies on token-based mechanisms:
OAuth tokens, <span acronym-label="pat"
acronym-form="plural+short">pats</span>, or service account credentials.
Pagination follows either offset-based or cursor-based patterns, and all
platforms impose rate limits that consumers must handle through backoff
strategies. This consistency enables shared connector logic for
authentication, pagination, rate limiting, and error recovery across
tools.

#### Source Code Management

provide a thorough treatment of Git, covering branching strategies,
merging, and distributed workflows, while offers a more recent visual
introduction. extend this perspective to organizational scale,
describing how large engineering teams manage repositories with
thousands of contributors. For this thesis, the repository is the
primary entity around which security findings are grouped, as detailed
in the data model in
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>.

Development teams host their Git repositories on cloud-based
<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms. GitHub is the dominant platform, with over 150 million
developers and adoption by 92% of Fortune 100 companies . The 2025 Stack
Overflow Developer Survey reports GitHub at 81% adoption for code
collaboration, followed by GitLab at 36% . Bitbucket and Azure DevOps
serve smaller but significant enterprise segments. Most large
organizations use more than one platform, whether through acquisitions,
team preferences, or regulatory separation, making multi-platform
ingestion a practical requirement.

Beyond source code, <span acronym-label="scm"
acronym-form="singular+short">scm</span> platforms expose metadata
relevant to security governance. Repository attributes include the
primary programming language, creation and last activity dates,
visibility settings (public or private), and archive status. Branch
protection rules indicate the maturity of the development process. Team
and contributor assignments establish ownership relationships that feed
into the application-to-team mapping described in
<a href="#sec:app-inventory" data-reference-type="autoref"
data-reference="sec:app-inventory">[sec:app-inventory]</a>.

These platforms share common <span acronym-label="api"
acronym-form="singular+short">api</span> patterns. GitHub exposes two
complementary <span acronym-label="api"
acronym-form="plural+short">apis</span> : a <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> (v3) with resource-oriented
endpoints and page-based pagination, and a GraphQL
<span acronym-label="api" acronym-form="singular+short">api</span> (v4)
that enables selective field retrieval with cursor-based pagination.
Both use the same authentication mechanisms (OAuth tokens or
<span acronym-label="pat" acronym-form="plural+short">pats</span>) and
share a rate limit of 5 000 requests per hour. GitLab offers a similar
dual <span acronym-label="rest"
acronym-form="singular+short">rest</span>/GraphQL surface . Azure DevOps
provides a <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> authenticated through Azure
Active Directory, with comparable response formats and pagination.
Across all platforms, authentication is token-based and responses are
<span acronym-label="json"
acronym-form="singular+short">json</span>-formatted, enabling shared
connector logic for authentication, pagination, and rate limit handling.

#### Continuous Integration and Delivery

<span acronym-label="sdlc" acronym-form="singular+short">sdlc</span>
practices have shifted from sequential models to iterative methodologies
and DevOps. present empirical evidence that high-performing teams deploy
more frequently with shorter lead times, achieved through
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
automation. complement this with practical guidance for implementing
DevOps pipelines at scale. The <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> pipeline, an automated
sequence of build, test, and deploy stages, is relevant to this thesis
because each stage can integrate security tools whose findings the
framework consolidates.

GitHub Actions is the most widely adopted <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> platform, used by 62% of
developers for personal projects and 41% in organizational settings .
Jenkins remains prevalent in enterprises at 28% organizational adoption,
followed by GitLab CI at 19%. Notably, 32% of organizations use two or
more <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> tools, and 9% use at least
three, reinforcing the multi-platform integration challenge observed for
<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms.

<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
platforms provide contextual data about when and how security scans run.
Pipeline definitions reveal which security tools are integrated into the
build process. Build results indicate whether security gates passed or
failed. Execution metadata records which commit was scanned, when the
scan ran, and how long it took. This information serves as operational
context rather than a primary finding source: knowing that a
repository’s last security scan ran three months ago, or that a scan
consistently fails, signals coverage gaps and tool health that
complement the findings from security tools.

Integration patterns vary more across <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> platforms than across
<span acronym-label="scm" acronym-form="singular+short">scm</span>
tools. GitHub Actions exposes build data through its
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span> with
<span acronym-label="json" acronym-form="singular+short">json</span>
responses, consistent with the broader GitHub <span acronym-label="api"
acronym-form="singular+short">api</span> surface. Jenkins uses an
<span acronym-label="xml" acronym-form="singular+short">xml</span>-based
<span acronym-label="api" acronym-form="singular+short">api</span> with
a different authentication model. Azure Pipelines follows the Azure
DevOps <span acronym-label="rest"
acronym-form="singular+short">rest</span> conventions. Despite these
differences, the retrieved data is structurally similar: pipeline
identifiers, run statuses, timestamps, and associated commit references.

#### Issue Tracking

Issue tracking systems are relevant to the framework because they track
remediation status. When a security finding is assigned for remediation,
an issue is typically created in the team’s tracker, either manually or
through automation. The framework must read issue status to determine
whether a finding is under active remediation, who is responsible, and
whether it has been resolved within the required
<span acronym-label="sla" acronym-form="singular+short">sla</span>
window.

Jira is the dominant issue tracking platform in enterprise environments.
The 2025 Stack Overflow Developer Survey reports Jira at 46% adoption,
behind only GitHub (81%) and ahead of GitLab (36%) for code
documentation and collaboration tools . Azure DevOps Work Items serves
organizations within the Microsoft ecosystem. GitHub Issues and GitLab
Issues provide lightweight built-in tracking tightly coupled with their
respective <span acronym-label="scm"
acronym-form="singular+short">scm</span> platforms. As with
<span acronym-label="scm" acronym-form="singular+short">scm</span> and
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
tools, many organizations use multiple trackers across different teams.

These platforms expose <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> with <span acronym-label="json"
acronym-form="singular+short">json</span> responses and paginated
results. Jira provides <span acronym-label="jql"
acronym-form="singular+short">jql</span>, a query language for precise
filtering by project, status, labels, or custom fields, enabling
retrieval of only security-relevant issues without downloading entire
project backlogs. GitHub and GitLab expose issues through the same
<span acronym-label="api" acronym-form="singular+short">api</span>
surfaces used for repository data. Most trackers also support webhooks
for real-time event notifications when issue status changes, reducing
reliance on periodic polling.

The integration with issue trackers is bidirectional. The framework
reads remediation status and may also create new issues when findings
require attention. This bidirectional flow introduces complexity around
idempotency (avoiding duplicate issue creation) and state
synchronization (keeping the framework’s view consistent with the
tracker’s current state).

### Static Application Security

Application security encompasses the practices and tools for identifying
vulnerabilities in software throughout its lifecycle . advocated for
security touchpoints spanning the entire development process. The
DevSecOps paradigm  realizes this vision by embedding security testing
into <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> pipelines.
<span acronym-label="sast" acronym-form="singular+short">sast</span>
examines source code, <span acronym-label="sca"
acronym-form="singular+short">sca</span> checks third-party
dependencies, secret scanners flag leaked credentials, and
<span acronym-label="dast" acronym-form="singular+short">dast</span>
probes running applications. The practical consequence is a high volume
of security data from tools with different <span acronym-label="api"
acronym-form="plural+short">apis</span>, output formats, and severity
models. The <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> Top 10 classifies common web
application risks , but it does not define a data interchange standard.

Several cross-cutting data standards bring partial consistency. The
<span acronym-label="cve" acronym-form="singular+short">cve</span>
system assigns unique identifiers to known vulnerabilities .
<span acronym-label="cwe" acronym-form="singular+short">cwe</span>
classifies underlying weakness types . <span acronym-label="cvss"
acronym-form="singular+short">cvss</span> scores attack vector,
complexity, and impact on a 0–10 scale . <span acronym-label="epss"
acronym-form="singular+short">epss</span> complements
<span acronym-label="cvss" acronym-form="singular+short">cvss</span>
with a predictive signal : the probability that a vulnerability will be
exploited within 30 days, computed by <span acronym-label="ml"
acronym-form="singular+short">ml</span> models.
<span acronym-label="cisa" acronym-form="singular+short">cisa</span>
maintains the <span acronym-label="kev"
acronym-form="singular+short">kev</span> catalog . It adds a third
signal: confirmed active exploitation from real-world incident data.
Together, <span acronym-label="cvss"
acronym-form="singular+short">cvss</span>, <span acronym-label="epss"
acronym-form="singular+short">epss</span>, and <span acronym-label="kev"
acronym-form="singular+short">kev</span> form a three-signal enrichment
model used throughout the framework.

For data interchange, <span acronym-label="sarif"
acronym-form="singular+short">sarif</span> defines a
<span acronym-label="json"
acronym-form="singular+short">json</span>-based format for static
analysis results . CycloneDX and <span acronym-label="spdx"
acronym-form="singular+short">spdx</span> provide
<span acronym-label="sbom" acronym-form="singular+short">sbom</span>
schemas . <span acronym-label="ocsf"
acronym-form="singular+short">ocsf</span> standardizes security event
exchange . It targets <span acronym-label="siem"
acronym-form="singular+short">siem</span> and <span acronym-label="soar"
acronym-form="singular+short">soar</span> use cases. No single format
covers all tool categories. <span acronym-label="sarif"
acronym-form="singular+short">sarif</span> addresses static analysis but
not <span acronym-label="sca" acronym-form="singular+short">sca</span>
or runtime findings. CycloneDX and <span acronym-label="spdx"
acronym-form="singular+short">spdx</span> cover software composition,
not code-level vulnerabilities. <span acronym-label="ocsf"
acronym-form="singular+short">ocsf</span> serves security operations,
not application security posture. This gap motivates the normalization
model in <a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>.

The analysis of security tooling is organized into two sections by
operational model. This section covers static analysis tools that
examine source code and build artifacts without executing the
application. Their findings reference repositories, file paths, and line
numbers, making them directly attributable to development teams.
<a href="#sec:dynamic-appsec" data-reference-type="autoref"
data-reference="sec:dynamic-appsec">[sec:dynamic-appsec]</a> covers
tools that operate on running applications and deployed infrastructure,
where findings reference <span acronym-label="url"
acronym-form="plural+short">urls</span>, hosts, and cloud resources,
requiring additional mapping to connect them back to source code. Mobile
application security testing is excluded from this analysis, as the
framework targets web applications and backend services.

#### Static Application Security Testing

<span acronym-label="sast" acronym-form="singular+short">sast</span>
examines source code, bytecode, or binary code for vulnerabilities
without executing the program. provide the foundations, covering taint
analysis, control flow analysis, and pattern matching to detect
injection flaws, buffer overflows, and insecure data handling. A key
tradeoff is between detection coverage and false positive rates: tools
with broader rule sets catch more issues but generate more noise .

SonarQube provides the most mature integration surface among
<span acronym-label="sast" acronym-form="singular+short">sast</span>
tools. Its <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> offers paginated endpoints with
server-side filtering by project, severity, status, and rule, returning
<span acronym-label="json" acronym-form="singular+short">json</span>
responses . Beyond individual findings, the <span acronym-label="api"
acronym-form="singular+short">api</span> exposes project-level quality
metrics useful for coverage analysis. Semgrep operates as a
<span acronym-label="cli" acronym-form="singular+short">cli</span> tool
running user-defined rules against source code, producing
<span acronym-label="json" acronym-form="singular+short">json</span> or
<span acronym-label="sarif" acronym-form="singular+short">sarif</span>
output . The Semgrep Cloud Platform adds a centralized
<span acronym-label="api" acronym-form="singular+short">api</span> for
managing rules and results across projects. Checkmarx exposes a
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span> for
scan management and result retrieval, with <span acronym-label="sarif"
acronym-form="singular+short">sarif</span> export support.

<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms also provide built-in <span acronym-label="sast"
acronym-form="singular+short">sast</span> capabilities. GitHub Code
Scanning runs CodeQL analysis and exposes results through the code
scanning alerts <span acronym-label="api"
acronym-form="singular+short">api</span> . GitLab integrates
<span acronym-label="sast" acronym-form="singular+short">sast</span> as
a <span acronym-label="cicd" acronym-form="singular+short">cicd</span>
pipeline job with findings accessible through its security
<span acronym-label="api" acronym-form="singular+short">api</span> .
When both platform-native and standalone tools scan the same repository,
the resulting overlap requires deduplication in the normalization layer.

Each finding typically includes a rule identifier, the affected file
path and line number, a severity rating, the offending code snippet, and
remediation guidance. However, severity models differ across tools.
SonarQube uses a five-level scale (blocker, critical, major, minor,
info). Semgrep and Checkmarx use high, medium, and low, sometimes with a
numerical score. This divergence makes severity normalization one of the
most important tasks in the framework’s transformation layer. The
reference implementation integrates SonarQube, Semgrep, and additional
<span acronym-label="sast" acronym-form="singular+short">sast</span>
sources as described in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>.

#### Software Composition Analysis

<span acronym-label="sca" acronym-form="singular+short">sca</span>
identifies known vulnerabilities in third-party dependencies. Modern
applications commonly include hundreds of transitive dependencies,
creating a large attack surface . provide a systematic review of supply
chain attacks, including typosquatting, dependency confusion, and
malicious package injection. <span acronym-label="sca"
acronym-form="singular+short">sca</span> tools analyze dependency
manifests, resolve the full dependency tree, and cross-reference
versions against vulnerability databases such as the
<span acronym-label="nvd" acronym-form="singular+short">nvd</span>.

Snyk provides <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> (legacy v1 and current v3)
returning <span acronym-label="json"
acronym-form="singular+short">json</span> responses with filtering by
severity and project . Dependabot, integrated into GitHub, exposes
alerts through the GitHub GraphQL <span acronym-label="api"
acronym-form="singular+short">api</span> . <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> Dependency-Track is an
open-source platform that ingests <span acronym-label="sbom"
acronym-form="plural+short">sboms</span> in CycloneDX or
<span acronym-label="spdx" acronym-form="singular+short">spdx</span>
format and identifies vulnerabilities against multiple databases . It
provides a <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> for project management and
findings retrieval. Many <span acronym-label="sca"
acronym-form="singular+short">sca</span> tools also generate
<span acronym-label="sbom" acronym-form="plural+short">sboms</span> ,
increasingly required by regulatory frameworks . The reference
implementation integrates Dependabot, Dependency-Track, and GitLab
dependency scanning, as described in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>.

<span acronym-label="sca" acronym-form="singular+short">sca</span>
output is comparatively well standardized because the underlying data
originates from shared public databases. Each finding typically includes
the vulnerable dependency name and version, a <span acronym-label="cve"
acronym-form="singular+short">cve</span> identifier, a
<span acronym-label="cvss" acronym-form="singular+short">cvss</span>
score, the fixed version when available, and exploitability metadata.
Despite this, transitive dependency resolution remains a challenge:
different tools may resolve the same dependency tree differently,
causing one tool to flag a <span acronym-label="cve"
acronym-form="singular+short">cve</span> while another does not. The
framework must handle this during deduplication, recognizing that the
same <span acronym-label="cve" acronym-form="singular+short">cve</span>
reported by multiple tools against the same repository likely represents
a single issue.

<span acronym-label="sca" acronym-form="singular+short">sca</span> tools
also detect license violations (e.g., GPL-licensed code in proprietary
applications), producing compliance findings alongside vulnerability
data. The <span acronym-label="slsa"
acronym-form="singular+short">slsa</span> framework  complements
<span acronym-label="sca" acronym-form="singular+short">sca</span> from
a different angle: while <span acronym-label="sca"
acronym-form="singular+short">sca</span> checks whether dependencies
contain known vulnerabilities, <span acronym-label="slsa"
acronym-form="singular+short">slsa</span> verifies the integrity and
provenance of build artifacts, ensuring they have not been tampered with
during the build process. Both concerns feed into the broader supply
chain security picture.

#### Secret Detection

Secret detection tools scan version control history for credentials,
<span acronym-label="api" acronym-form="singular+short">api</span> keys,
tokens, and other sensitive material. Once a secret is committed, it
persists in Git history even after deletion from the working tree. Tools
use two complementary detection approaches. Pattern-based detection
matches strings against known credential formats using regular
expressions. Entropy-based detection flags strings with unusually high
randomness, catching novel credential formats at the cost of higher
false positive rates.

GitLeaks scans repositories against over 150 predefined patterns and
produces <span acronym-label="json"
acronym-form="singular+short">json</span> output . It runs as a
<span acronym-label="cli" acronym-form="singular+short">cli</span> tool,
typically in <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> pipelines or pre-commit hooks.
TruffleHog supports over 800 secret types, combines pattern and entropy
analysis, and adds live credential verification to confirm whether a
detected secret remains valid . Both tools operate as
<span acronym-label="cli" acronym-form="singular+short">cli</span> tools
without server-side <span acronym-label="api"
acronym-form="plural+short">apis</span>; integration requires executing
the tool and parsing its output.

Platform-integrated scanners take a different approach. GitHub Secret
Scanning exposes alerts through the GitHub <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> with webhook notifications for
new detections . GitLab Secret Detection runs as a
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
pipeline job and reports results through GitLab’s security dashboard and
<span acronym-label="api" acronym-form="singular+short">api</span> .
These tools are simpler to integrate because they use existing platform
<span acronym-label="api" acronym-form="singular+short">api</span>
surfaces, but they only cover repositories hosted on their respective
platforms.

The primary integration challenge is the absence of a standard output
format. Each tool defines its own <span acronym-label="json"
acronym-form="singular+short">json</span> schema, and none supports
<span acronym-label="sarif" acronym-form="singular+short">sarif</span>.
Findings include the secret type, file path, commit reference, and
sometimes a validity status, but field names and structures vary across
tools.

#### Container Image Scanning

Container image scanning examines built container images for
vulnerabilities in <span acronym-label="os"
acronym-form="singular+short">os</span> packages, application libraries,
and configuration. While <span acronym-label="sca"
acronym-form="singular+short">sca</span> analyzes source-level
dependency manifests, container scanners operate on assembled images,
detecting <span acronym-label="os"
acronym-form="singular+short">os</span>-level vulnerabilities and
misconfigurations that source-level analysis does not cover.

Trivy is a widely adopted open-source scanner supporting container
images, filesystems, and Git repositories . It produces
<span acronym-label="json" acronym-form="singular+short">json</span> or
<span acronym-label="sarif" acronym-form="singular+short">sarif</span>
output and integrates into <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> pipelines as a
<span acronym-label="cli" acronym-form="singular+short">cli</span> tool.
Commercial alternatives such as Aqua and Prisma Cloud add registry
scanning, policy enforcement, and centralized management through
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="plural+short">apis</span>.
Findings typically include the vulnerable package name and version, a
<span acronym-label="cve" acronym-form="singular+short">cve</span>
identifier, the fixed version, and the image layer where the package was
introduced.

The integration challenge is linking image vulnerabilities to source
code repositories. Container images are identified by registry, name,
and tag, not by the source code that produced them. Establishing this
mapping requires tracing through <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> metadata: which pipeline built
the image, from which repository, at which commit.

#### Infrastructure as Code Security

<span acronym-label="iac" acronym-form="singular+short">iac</span>
security tools perform static analysis on infrastructure definitions:
Terraform configurations, CloudFormation templates, Kubernetes
manifests, and Dockerfiles. They detect misconfigurations before
deployment, such as overly permissive access policies, unencrypted
storage, exposed ports, and missing logging.

Checkov is a prominent open-source scanner supporting over 1 000
built-in policies across multiple <span acronym-label="iac"
acronym-form="singular+short">iac</span> frameworks . tfsec focuses on
Terraform, and KICS covers a broad range of formats. All operate as
<span acronym-label="cli" acronym-form="singular+short">cli</span> tools
producing <span acronym-label="json"
acronym-form="singular+short">json</span> or <span acronym-label="sarif"
acronym-form="singular+short">sarif</span> output. Findings are
file-and-line-based, structurally similar to <span acronym-label="sast"
acronym-form="singular+short">sast</span> output, but target
infrastructure configuration rather than application logic.

Kubernetes admission controllers such as OPA/Gatekeeper and Kyverno
enforce policies at deploy time, rejecting workloads that violate
security constraints. They occupy a middle ground between pre-deployment
<span acronym-label="iac" acronym-form="singular+short">iac</span>
scanning and post-deployment <span acronym-label="cspm"
acronym-form="singular+short">cspm</span>: the policies are defined as
code, but enforcement happens at the cluster boundary. Their violation
logs provide an additional signal about infrastructure security posture.

These tools complement the runtime monitoring tools discussed in
<a href="#sec:dynamic-appsec" data-reference-type="autoref"
data-reference="sec:dynamic-appsec">[sec:dynamic-appsec]</a>.
<span acronym-label="cspm" acronym-form="singular+short">cspm</span>
scanners and <span acronym-label="vmdr"
acronym-form="singular+short">vmdr</span> platforms detect the same
misconfiguration classes after deployment in the live environment.
Correlating pre-deployment <span acronym-label="iac"
acronym-form="singular+short">iac</span> findings with post-deployment
runtime detections is a challenge the framework addresses through its
unified data model.

### Dynamic Application Security

While the static analysis tools in
<a href="#sec:static-appsec" data-reference-type="autoref"
data-reference="sec:static-appsec">[sec:static-appsec]</a> examine
source code and build artifacts, the tools in this section operate on
running applications and deployed infrastructure. The cross-cutting data
standards introduced in
<a href="#sec:static-appsec" data-reference-type="autoref"
data-reference="sec:static-appsec">[sec:static-appsec]</a>, particularly
<span acronym-label="cve" acronym-form="singular+short">cve</span>,
<span acronym-label="cvss" acronym-form="singular+short">cvss</span>,
<span acronym-label="epss" acronym-form="singular+short">epss</span>,
and <span acronym-label="kev" acronym-form="singular+short">kev</span>,
apply equally to dynamic findings. The cross-layer correlation challenge
that connects these findings to business applications is addressed in
<a href="#sec:runtime-correlation" data-reference-type="autoref"
data-reference="sec:runtime-correlation">[sec:runtime-correlation]</a>.

#### Dynamic Application Security Testing

<span acronym-label="dast" acronym-form="singular+short">dast</span>
tests running applications by sending crafted <span acronym-label="http"
acronym-form="singular+short">http</span> requests and analyzing
responses for vulnerability indicators . Unlike
<span acronym-label="sast" acronym-form="singular+short">sast</span>,
which works on source code, <span acronym-label="dast"
acronym-form="singular+short">dast</span> requires a deployed
application and detects vulnerabilities that manifest only at runtime,
such as authentication bypass, server misconfiguration, and certain
injection flaws.

<span acronym-label="owasp" acronym-form="singular+short">owasp</span>
<span acronym-label="zap" acronym-form="singular+short">zap</span> is
the most widely used open-source <span acronym-label="dast"
acronym-form="singular+short">dast</span> tool, providing a
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span> for
scan management and result retrieval with <span acronym-label="json"
acronym-form="singular+short">json</span> and <span acronym-label="xml"
acronym-form="singular+short">xml</span> output . Burp Suite exposes a
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span> in
its Enterprise edition; the Professional edition is a desktop tool
without programmatic access. Findings from both tools include the target
<span acronym-label="url" acronym-form="singular+short">url</span>, the
affected <span acronym-label="http"
acronym-form="singular+short">http</span> parameter, the vulnerability
type mapped to <span acronym-label="cwe"
acronym-form="singular+short">cwe</span> identifiers , exploitation
evidence, and a confidence rating.

The core integration challenge is that <span acronym-label="dast"
acronym-form="singular+short">dast</span> findings are
<span acronym-label="url"
acronym-form="singular+short">url</span>-based, not code-based. A
<span acronym-label="sast" acronym-form="singular+short">sast</span>
finding points to a file and line in a repository; a
<span acronym-label="dast" acronym-form="singular+short">dast</span>
finding points to a <span acronym-label="url"
acronym-form="singular+short">url</span> endpoint. Mapping
<span acronym-label="url" acronym-form="singular+short">url</span>-based
findings to source repositories requires deployment metadata or
application inventory data from
<a href="#sec:app-inventory" data-reference-type="autoref"
data-reference="sec:app-inventory">[sec:app-inventory]</a>. Without this
mapping, <span acronym-label="dast"
acronym-form="singular+short">dast</span> findings can be attributed to
applications but not to development teams or code locations.

#### Penetration Testing

Manual penetration testing traditionally produces no machine-readable
output. External firms deliver results as narrative
<span acronym-label="pdf" acronym-form="singular+short">pdf</span> or
Word reports, requiring a structured upload mechanism (e.g., a
<span acronym-label="json" acronym-form="singular+short">json</span> or
<span acronym-label="csv" acronym-form="singular+short">csv</span>
template) for security teams to transcribe key fields.
<span acronym-label="ml" acronym-form="singular+short">ml</span>-based
document parsing could automate extraction, though the inconsistent
formatting of penetration test reports makes this non-trivial.

Emerging platforms such as XBOW use autonomous <span acronym-label="ai"
acronym-form="singular+short">ai</span> agents to perform penetration
testing at scale, delivering validated findings with reproducible
exploit evidence . These platforms offer <span acronym-label="api"
acronym-form="singular+short">api</span> access for test orchestration
and integrate with security data ecosystems, moving penetration testing
toward the structured, automatable data exchange that other tool
categories already provide.

Despite low frequency, penetration testing findings are often among the
most critical, representing validated exploitable vulnerabilities. The
framework must accommodate both manual uploads and automated
<span acronym-label="api" acronym-form="singular+short">api</span>
ingestion to cover the full spectrum of penetration testing practices.

#### Web Application Firewalls

<span acronym-label="waf" acronym-form="plural+short">wafs</span>
operate at the network perimeter, inspecting inbound
<span acronym-label="http" acronym-form="singular+short">http</span>
traffic against rule sets such as the <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> Core Rule Set. They log
blocked and flagged requests, recording the matched rule, request
details, and action taken. Most commercial <span acronym-label="waf"
acronym-form="plural+short">wafs</span> (<span acronym-label="aws"
acronym-form="singular+short">aws</span> WAF, Cloudflare, Akamai) expose
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="plural+short">apis</span> for
log retrieval and configuration management.

These platforms typically bundle <span acronym-label="ddos"
acronym-form="singular+short">ddos</span> protection alongside
<span acronym-label="waf" acronym-form="singular+short">waf</span>
capabilities. <span acronym-label="ddos"
acronym-form="singular+short">ddos</span> mitigation services filter
volumetric and application-layer attacks, logging traffic patterns,
attack signatures, and mitigation actions. This telemetry provides
availability impact data that complements the vulnerability-focused
findings from other tool categories.

<span acronym-label="waf" acronym-form="plural+short">wafs</span> and
<span acronym-label="ddos" acronym-form="singular+short">ddos</span>
protection generate high-volume event data rather than discrete
findings. The framework ingests aggregated attack patterns and anomaly
indicators rather than individual request logs, focusing on the subset
relevant to application security posture assessment.

#### Runtime Application Self-Protection

<span acronym-label="rasp" acronym-form="singular+short">rasp</span>
tools instrument the application runtime, detecting attacks such as
<span acronym-label="sql" acronym-form="singular+short">sql</span>
injection and path traversal from within the application context. Unlike
<span acronym-label="waf" acronym-form="plural+short">wafs</span>, which
operate at the network perimeter, <span acronym-label="rasp"
acronym-form="singular+short">rasp</span> can correlate attacks with
specific application functions and code paths. This produces richer
contextual data per event, but <span acronym-label="rasp"
acronym-form="singular+short">rasp</span> adoption remains limited
compared to <span acronym-label="waf"
acronym-form="plural+short">wafs</span>, and integration surfaces vary
across vendors.

Like <span acronym-label="waf" acronym-form="plural+short">wafs</span>,
<span acronym-label="rasp" acronym-form="singular+short">rasp</span>
tools produce event streams rather than discrete findings. The
integration approach is similar: the framework consumes aggregated
indicators rather than raw event logs.

#### Runtime API Security

Traditional <span acronym-label="dast"
acronym-form="singular+short">dast</span> tools actively probe
applications with crafted requests. Runtime <span acronym-label="api"
acronym-form="singular+short">api</span> security platforms take a
different approach: they passively monitor live
<span acronym-label="api" acronym-form="singular+short">api</span>
traffic, build behavioral baselines, and detect anomalies that indicate
abuse . This continuous monitoring catches threats that active scanning
misses, including business logic abuse, account takeover patterns, and
data exfiltration through legitimate <span acronym-label="api"
acronym-form="singular+short">api</span> endpoints.

Salt Security pioneered this category, applying <span acronym-label="ai"
acronym-form="singular+short">ai</span>-based behavioral analysis to
<span acronym-label="api" acronym-form="singular+short">api</span>
traffic to discover shadow <span acronym-label="api"
acronym-form="plural+short">apis</span>, detect anomalies, and identify
attack patterns . Noname Security, acquired by Akamai in 2024 , offers
similar capabilities: <span acronym-label="api"
acronym-form="singular+short">api</span> discovery, vulnerability
detection, and runtime protection integrated into Akamai’s edge
platform. Both expose <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> for configuration and findings
retrieval.

Runtime <span acronym-label="api"
acronym-form="singular+short">api</span> security produces
event-oriented data similar to <span acronym-label="waf"
acronym-form="plural+short">wafs</span> and <span acronym-label="rasp"
acronym-form="singular+short">rasp</span>, but with richer
<span acronym-label="api"
acronym-form="singular+short">api</span>-specific context: the affected
endpoint, request/response patterns, the deviation from baseline
behavior, and the attack classification. The framework treats these as a
continuous finding source, ingesting aggregated indicators rather than
raw traffic data.

#### Vulnerability Management and Cloud Posture

<span acronym-label="vmdr" acronym-form="singular+short">vmdr</span>
tools scan infrastructure for <span acronym-label="os"
acronym-form="singular+short">os</span> vulnerabilities, missing
patches, and exposed services. Qualys exposes data through a
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span> with
<span acronym-label="xml" acronym-form="singular+short">xml</span>
responses. Wiz uses a GraphQL <span acronym-label="api"
acronym-form="singular+short">api</span> for selective queries across
cloud environments. These tools produce findings tied to infrastructure
identifiers (hostnames, IP addresses, cloud resource
<span acronym-label="arn" acronym-form="plural+short">arns</span>), not
to source code locations.

<span acronym-label="cspm" acronym-form="singular+short">cspm</span>
tools complement <span acronym-label="vmdr"
acronym-form="singular+short">vmdr</span> by evaluating cloud
configurations against compliance benchmarks such as
<span acronym-label="cis" acronym-form="singular+short">cis</span>
Benchmarks and organizational policies. Findings indicate
misconfigurations (public S3 buckets, overly permissive
<span acronym-label="iam" acronym-form="singular+short">iam</span>
roles, unencrypted storage) rather than software vulnerabilities.
<span acronym-label="cspm" acronym-form="singular+short">cspm</span>
overlaps with <span acronym-label="iac"
acronym-form="singular+short">iac</span> security
(<a href="#sec:iac-security" data-reference-type="autoref"
data-reference="sec:iac-security">[sec:iac-security]</a>): both detect
the same misconfiguration classes, but <span acronym-label="iac"
acronym-form="singular+short">iac</span> tools scan before deployment
while <span acronym-label="cspm"
acronym-form="singular+short">cspm</span> scans the live environment.
Correlating pre-deployment and post-deployment findings is a key
integration challenge.

#### Source Integration Summary

<a href="#tab:data-source-comparison" data-reference-type="autoref"
data-reference="tab:data-source-comparison">[tab:data-source-comparison]</a>
summarizes the integration characteristics across all source categories
analyzed in this chapter.

<div id="tab:data-source-comparison">

| **Source Category**   |     **API**     | **Format** | **Frequency** | **Standardization** |
|:----------------------|:---------------:|:----------:|:-------------:|:-------------------:|
| Application Inventory |      REST       |    JSON    |      Low      |         Low         |
| Cloud Assets          |      REST       |    JSON    |  Continuous   |       Medium        |
| SCM Platforms         |  REST/GraphQL   |    JSON    |    Medium     |        High         |
| Issue Trackers        |      REST       |    JSON    |    Medium     |       Medium        |
| CI/CD Platforms       |    REST/XML     |  JSON/XML  |    Medium     |       Medium        |
| SAST                  |    REST/CLI     | JSON/SARIF |   On-demand   |       Medium        |
| SCA                   |  REST/GraphQL   |    JSON    |  Continuous   |        High         |
| Secret Scanning       |    CLI/REST     |    JSON    |   On-demand   |         Low         |
| Container Scanning    |       CLI       | JSON/SARIF |   On-demand   |       Medium        |
| IaC Scanning          |       CLI       | JSON/SARIF |   On-demand   |       Medium        |
| DAST                  |    REST/CLI     |  JSON/XML  |   On-demand   |       Medium        |
| Penetration Testing   |      None       |    PDF     |   Periodic    |        None         |
| WAF/DDoS              |      REST       |    JSON    |  Continuous   |         Low         |
| RASP                  | Vendor-specific |    JSON    |  Continuous   |         Low         |
| API Security          |      REST       |    JSON    |  Continuous   |         Low         |
| VMDR/CSPM             |  REST/GraphQL   |  JSON/XML  |  Continuous   |       Medium        |

Data Source Integration Characteristics

</div>

Several patterns emerge from this comparison. <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> with <span acronym-label="json"
acronym-form="singular+short">json</span> responses are the dominant
integration surface, but <span acronym-label="xml"
acronym-form="singular+short">xml</span> responses, GraphQL queries,
<span acronym-label="cli" acronym-form="singular+short">cli</span>
output parsing, and manual uploads are all necessary. Standardization
varies: <span acronym-label="sca"
acronym-form="singular+short">sca</span> benefits from the
<span acronym-label="cve"
acronym-form="singular+short">cve</span>/<span acronym-label="nvd"
acronym-form="singular+short">nvd</span> ecosystem,
<span acronym-label="sast" acronym-form="singular+short">sast</span> is
partially standardized through <span acronym-label="sarif"
acronym-form="singular+short">sarif</span>, and secret scanning has no
standard format. Update frequencies range from continuous dependency
monitoring to periodic penetration tests. These characteristics define
what the ingestion layer described in
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> must accommodate.

### Data Engineering

#### Data Platform Architecture

#### Data Integration Patterns

#### Domain Data Model

### Related Work and Gap Analysis

#### Existing Approaches

#### Databricks Lakewatch

#### Comparative Analysis and Research Gap

## Framework

### Solution Architecture

#### Component Design

#### Medallion Architecture

#### Technology Stack

### Data Model

#### Schema Patterns

#### Entity Model

#### Aggregation Model

### Connector Framework

#### Connector Abstraction

#### Ingestion Patterns

#### Transformation Patterns

### Analytics and Serving Layer

#### Aggregation Patterns

#### ML Workflows

#### Serving Patterns

### Deployment and Engineering Practices

#### Deployment Strategy

#### Project Structure

#### Testing Strategy

## Implementation

### Environment and Deployment

#### Workspace Setup

#### Silver Schema

#### Project Structure and CI/CD

### Connectors

#### ServiceNow

#### GitHub

#### GitLab

#### SonarQube

#### Semgrep

#### Dependency-Track

#### TruffleHog

#### Vulnerability Enrichment

### Analytics and Serving

#### Application-Repository Mapping

#### Application Risk Scoring

#### Remediation and Compliance Metrics

#### Vulnerability Trends

#### Risk Prediction Model

#### Serving Layer

### Testing and Validation

## Conclusion

### Thesis Outcomes and Contributions

### Limitations

### Future Work

# Appendices

## Generative AI Use Disclosure

### Text Content

### Diagrams and Figures

### Source Code

### Requirements Specification
