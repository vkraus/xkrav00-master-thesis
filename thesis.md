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
  - [Technology Stack](#technology-stack)
        - [Delta Lake](#delta-lake)
        - [Unity Catalog](#unity-catalog)
        - [Lakeflow Declarative Pipelines](#lakeflow-declarative-pipelines)
        - [Lakebase](#lakebase)
        - [Platform Synergies](#platform-synergies)
  - [Component Design](#component-design)
  - [Medallion Architecture](#medallion-architecture)
        - [Bronze Layer](#bronze-layer)
        - [Silver Layer](#silver-layer)
        - [Gold Layer](#gold-layer)
- [Data Model](#data-model)
  - [Schema Patterns](#schema-patterns)
        - [Bronze Pattern](#bronze-pattern)
        - [Silver Entity Pattern](#silver-entity-pattern)
        - [Silver Finding Pattern](#silver-finding-pattern)
        - [Relationship Pattern](#relationship-pattern)
        - [Gold Aggregation Pattern](#gold-aggregation-pattern)
  - [Entity Model](#entity-model)
        - [Entity Tables](#entity-tables)
        - [Finding Tables](#finding-tables)
        - [Reference Tables](#reference-tables)
        - [Relationship Tables](#relationship-tables)
  - [Aggregation Model](#aggregation-model)
        - [Application Risk Scores](#application-risk-scores)
        - [Team Metrics](#team-metrics)
        - [Vulnerability Trends](#vulnerability-trends)
        - [Coverage Analysis](#coverage-analysis)
        - [Extension Guide](#extension-guide)
- [Environment and Deployment](#environment-and-deployment)
  - [Deployment Strategy](#deployment-strategy)
  - [Project Structure](#project-structure)
  - [Pipeline Orchestration](#pipeline-orchestration)
  - [Monitoring and Observability](#monitoring-and-observability)
  - [Testing and Validation](#testing-and-validation)
- [Connector Framework](#connector-framework)
  - [Connector Abstraction](#connector-abstraction)
        - [Connector Categories](#connector-categories)
        - [Authentication](#authentication)
        - [Pagination](#pagination)
        - [Rate Limiting](#rate-limiting)
        - [Incremental State](#incremental-state)
        - [Extension Points](#extension-points)
  - [Ingestion Patterns](#ingestion-patterns)
        - [Common Landing Pattern](#common-landing-pattern)
        - [Source Code Management Sources](#source-code-management-sources)
        - [Security Scanner Sources](#security-scanner-sources)
        - [Application Inventory Sources](#application-inventory-sources)
  - [Transformation Patterns](#transformation-patterns)
        - [Schema Mapping](#schema-mapping)
        - [Normalization](#normalization)
        - [Data Quality Validation](#data-quality-validation)
        - [Deduplication](#deduplication)
        - [Business Context Attribution](#business-context-attribution)
  - [Testing and Validation](#testing-and-validation-1)
- [Analytics and Serving Framework](#analytics-and-serving-framework)
  - [Analytics Patterns](#analytics-patterns)
        - [Rule-Based Analytics](#rule-based-analytics)
        - [ML-Driven Analytics](#ml-driven-analytics)
        - [Extension Blueprint](#extension-blueprint)
  - [Serving Patterns](#serving-patterns)
        - [Analytical Serving](#analytical-serving)
        - [Operational Serving](#operational-serving)
        - [Event-Driven Serving](#event-driven-serving)
  - [Testing and Validation](#testing-and-validation-2)
  - [Implementation](#implementation)
- [Environment and Deployment](#environment-and-deployment-1)
  - [Workspace Setup](#workspace-setup)
  - [Silver Schema](#silver-schema)
  - [Project Structure and CI/CD](#project-structure-and-cicd)
  - [Pipeline Orchestration](#pipeline-orchestration-1)
  - [Monitoring and Observability](#monitoring-and-observability-1)
  - [Testing and Validation](#testing-and-validation-3)
- [Connectors](#connectors)
  - [ServiceNow](#servicenow)
  - [GitHub](#github)
  - [GitLab](#gitlab)
  - [SonarQube](#sonarqube)
  - [Semgrep](#semgrep)
  - [Dependency-Track](#dependency-track)
  - [TruffleHog](#trufflehog)
  - [Vulnerability Enrichment](#vulnerability-enrichment)
  - [Testing and Validation](#testing-and-validation-4)
- [Analytics and Serving](#analytics-and-serving)
  - [Application-Repository Mapping](#application-repository-mapping)
  - [Application Risk Scoring](#application-risk-scoring)
  - [Remediation and Compliance Metrics](#remediation-and-compliance-metrics)
  - [Vulnerability Trends](#vulnerability-trends-1)
  - [Risk Prediction Model](#risk-prediction-model)
  - [Serving Layer](#serving-layer)
  - [Testing and Validation](#testing-and-validation-5)
- [Testing and Validation](#testing-and-validation-6)
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

The preceding sections analyzed the sources of application security
data: asset inventories, development platforms, and security testing
tools across static and dynamic categories. Consolidating these
heterogeneous sources into a unified analytical platform is
fundamentally a data integration problem. This section surveys the
architectural paradigms and engineering patterns relevant to solving it,
independent of any specific platform.

#### Data Platform Architecture

The literature documents a progression from data warehouses through data
lakes to the lakehouse paradigm. provide a comprehensive body of
knowledge for data management, establishing the vocabulary and
principles referenced throughout this section. established the
relational model as the theoretical foundation. The data warehouse,
formalized by , stores subject-oriented, integrated data for analytical
decision-making using a top-down normalized approach. take a
complementary bottom-up path with dimensional modeling: star schemas
that organize data into fact and dimension tables optimized for queries.
Both approaches assume structured sources with stable schemas, a
condition that does not hold for heterogeneous security tool output.

The data lake  stores raw data in its native format, deferring schema
definition to consumption time (schema-on-read). This accommodates
format diversity but introduces governance challenges. Without proper
management, data lakes risk becoming “data swamps” where data is
abundant but unusable .

The lakehouse architecture  combines data lake flexibility with
warehouse governance by introducing open table formats that add
<span acronym-label="acid" acronym-form="singular+short">acid</span>
transactions, schema enforcement, and time travel on top of lake
storage . The lakehouse paradigm suits the application security problem:
it accommodates diverse, semi-structured tool output while providing the
governance and query performance required for both analytical dashboards
and operational lookups.

The medallion architecture  organizes lakehouse data into three layers:

- **Bronze**: Raw data with minimal transformation, preserving original
  source schemas.

- **Silver**: Cleaned, validated, and normalized data conforming to a
  unified schema.

- **Gold**: Consumption-ready aggregated metrics and enriched datasets.

This layered approach maps naturally to the security data integration
problem. The bronze layer captures raw tool output in source-native
schemas. The silver layer normalizes findings across tools into a
vendor-agnostic model. The gold layer computes the aggregated risk
metrics and enriched datasets that stakeholders consume.

A security data platform must serve two distinct access patterns.
<span acronym-label="olap" acronym-form="singular+short">olap</span>
queries power dashboards and trend analysis, operating over large
aggregated datasets where query throughput matters more than write
latency. <span acronym-label="oltp"
acronym-form="singular+short">oltp</span> access supports operational
workflows such as issue tracker integration and real-time risk lookups,
where low-latency reads and writes to individual records are essential.
The framework must accommodate both, a requirement that influences the
serving architecture designed in
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>.

#### Data Integration Patterns

cover data engineering fundamentals, including the distinction between
<span acronym-label="etl" acronym-form="singular+short">etl</span> and
<span acronym-label="elt" acronym-form="singular+short">elt</span>
paradigms. <span acronym-label="etl"
acronym-form="singular+short">etl</span> transforms data before loading,
requiring upfront schema knowledge and a dedicated transformation layer
between source and target. <span acronym-label="elt"
acronym-form="singular+short">elt</span> loads raw data first and
transforms it in place, aligning well with lakehouse architectures where
distributed compute engines perform transformations at scale . For
security data integration, <span acronym-label="elt"
acronym-form="singular+short">elt</span> is the natural fit: tool output
varies widely in structure and evolves frequently, making upfront
transformation brittle.

Full re-ingestion does not scale for enterprise environments with
thousands of repositories and dozens of security tools. Incremental
ingestion pulls only records that are new or changed since the last
synchronization. The high-water mark pattern tracks a timestamp or
cursor per source, resuming extraction from the last known position.
<span acronym-label="cdc" acronym-form="singular+short">cdc</span>
captures changes at the source level, propagating inserts, updates, and
deletes as events . Both approaches reduce <span acronym-label="api"
acronym-form="singular+short">api</span> call volume and processing
time, enabling more frequent pipeline runs without proportional resource
growth.

Source tools change their <span acronym-label="api"
acronym-form="plural+short">apis</span> and output formats regularly. A
rigid schema definition would break pipelines with every upstream
change. Schema-on-read stores raw data in its original structure and
applies schema interpretation at query time. Additive schema evolution
allows new fields to be absorbed without breaking existing queries or
downstream consumers . For security tool integration, this flexibility
is essential: tools add new finding attributes, rename fields, and
change enumerations across versions.

Pipeline re-runs must produce the same result regardless of how many
times they execute. This idempotency property is essential for handling
retries after partial failures and for reprocessing historical data
without creating duplicates. Data quality enforcement complements
idempotency through validation at each pipeline layer: schema
conformance at ingestion, value range checks during normalization, and
referential integrity at aggregation. Records that fail validation are
routed to quarantine tables rather than silently dropped or propagated
downstream . This quarantine pattern ensures zero silent data loss:
every ingested record is either successfully processed or isolated with
a documented failure reason.

#### Domain Data Model

The security domains analyzed in
<a href="#sec:app-inventory" data-reference-type="autoref"
data-reference="sec:app-inventory">[sec:app-inventory]</a> through
<a href="#sec:source-integration-summary" data-reference-type="autoref"
data-reference="sec:source-integration-summary">[sec:source-integration-summary]</a>
produce data about a common set of entities and relationships. Before
designing physical schemas, a vendor-agnostic conceptual model must
define what the framework represents. This subsection identifies the
core entities, their relationships, and the consumption patterns that
drive the serving layer.

Five primary entity types form the backbone of the domain model:

- **Applications** carry business context from asset inventories
  (<a href="#sec:app-inventory" data-reference-type="autoref"
  data-reference="sec:app-inventory">[sec:app-inventory]</a>): name,
  owning team, criticality tier, lifecycle status, and compliance scope.
  An application represents a business-level unit that may span multiple
  repositories and deployment environments.

- **Repositories** represent technical assets from
  <span acronym-label="scm" acronym-form="singular+short">scm</span>
  platforms
  (<a href="#sec:sw-dev-analysis" data-reference-type="autoref"
  data-reference="sec:sw-dev-analysis">[sec:sw-dev-analysis]</a>): code
  location, primary language, visibility, activity indicators, and
  archive status. The repository is the primary unit around which
  security findings are grouped.

- **Findings** capture security issues from any tool category analyzed
  in <a href="#sec:static-appsec" data-reference-type="autoref"
  data-reference="sec:static-appsec">[sec:static-appsec]</a> and
  <a href="#sec:dynamic-appsec" data-reference-type="autoref"
  data-reference="sec:dynamic-appsec">[sec:dynamic-appsec]</a>:
  severity, status, source tool, detection timestamp, affected code
  location, and rule or check identifier. Each finding traces to a
  specific tool scan.

- **Vulnerabilities** are <span acronym-label="cve"
  acronym-form="singular+short">cve</span>-identified issues enriched
  with three signals: <span acronym-label="cvss"
  acronym-form="singular+short">cvss</span> severity from the
  <span acronym-label="nvd" acronym-form="singular+short">nvd</span>,
  exploitation probability from <span acronym-label="epss"
  acronym-form="singular+short">epss</span>, and confirmed exploitation
  status from <span acronym-label="cisa"
  acronym-form="singular+short">cisa</span> <span acronym-label="kev"
  acronym-form="singular+short">kev</span>. Multiple findings from
  different tools may reference the same vulnerability.

- **Teams** provide organizational ownership, linking personnel to
  applications and remediation responsibilities. Team structure enables
  filtering and aggregation by organizational unit.

Several additional entity types provide the development process and
supply chain context necessary for actionable security analytics:

- **Commits** record individual code changes with author, timestamp, and
  affected files. They link findings to specific code versions and
  establish authorship for attribution.

- **Pull requests** represent code change proposals where security scans
  typically execute. Scan results are often reported per pull request,
  making it a natural grouping unit for new findings.

- **Pipeline runs** capture <span acronym-label="cicd"
  acronym-form="singular+short">cicd</span> execution records: which
  security tools ran, when, against which commit, and whether security
  gates passed. They indicate scan coverage and tool health across
  repositories.

- **Issues** track remediation work items in systems such as Jira.
  Linking findings to issues enables <span acronym-label="mttr"
  acronym-form="singular+short">mttr</span> calculation and
  <span acronym-label="sla" acronym-form="singular+short">sla</span>
  compliance monitoring.

- **Dependencies** represent third-party libraries identified through
  <span acronym-label="sca" acronym-form="singular+short">sca</span>:
  package name, version, license, and associated
  <span acronym-label="cve" acronym-form="singular+short">cve</span>
  identifiers. They connect <span acronym-label="sca"
  acronym-form="singular+short">sca</span> findings to the specific
  library version that introduced the vulnerability.

- **Branch protection policies** capture governance configurations from
  <span acronym-label="scm" acronym-form="singular+short">scm</span>
  platforms: required reviewers, mandatory status checks, and merge
  restrictions. They serve as indicators of development process maturity
  and security hygiene at the repository level.

<a href="#fig:domain-model" data-reference-type="autoref"
data-reference="fig:domain-model">[fig:domain-model]</a> illustrates the
entity relationships. Primary entities (bold borders) form the core
analytical model; supporting entities provide development process and
supply chain context.

<figure id="fig:domain-model">

<figcaption>Conceptual Domain Model</figcaption>
</figure>

The application-to-repository mapping is the most critical relationship:
it links technical findings to business context, enabling risk-aware
prioritization. This relationship is many-to-many; shared libraries
serve multiple applications, and microservice applications span multiple
repositories. Teams own applications, establishing the chain from
organizational accountability through business applications to technical
assets and their findings.

Development process entities add temporal and workflow context to this
core chain. Repositories contain commits and pull requests, which
trigger pipeline runs and produce findings. Findings that reference
<span acronym-label="cve" acronym-form="singular+short">cve</span>
identifiers link to vulnerability records, enabling enrichment with
external intelligence. Dependencies bridge repositories and
vulnerabilities: an <span acronym-label="sca"
acronym-form="singular+short">sca</span> finding links a specific
library version in a repository to a known <span acronym-label="cve"
acronym-form="singular+short">cve</span>. Issues track the remediation
of one or more findings, closing the loop from detection to resolution.

The entity structure maps naturally to dimensional modeling patterns .
Findings function as fact records: measurable events with severity,
detection date, and tool source. Applications, repositories, and teams
serve as dimension records that provide descriptive context for
analysis. Supporting entities such as commits, pull requests, and
pipeline runs add temporal and process dimensions. This alignment means
standard analytical techniques (filtering by dimension, aggregating
facts, computing trends over time) apply directly to the security
domain. When multiple tools detect the same underlying issue, cross-tool
deduplication collapses related findings while preserving traceability
to each source report.

Different stakeholders consume this data through different access
patterns. Application owners need aggregated risk dashboards showing
finding counts by severity, remediation progress, and compliance status
for their applications. Developers need actionable findings with
code-level context, delivered through issue trackers. Security experts
need drill-down access to raw findings, audit trails, and cross-tool
correlation for triage. Leadership needs executive metrics:
<span acronym-label="mttr" acronym-form="singular+short">mttr</span>,
<span acronym-label="sla" acronym-form="singular+short">sla</span>
compliance rates, vulnerability density trends, and portfolio-level
comparisons. These consumption patterns span the
<span acronym-label="olap" acronym-form="singular+short">olap</span> and
<span acronym-label="oltp" acronym-form="singular+short">oltp</span>
serving requirements identified in
<a href="#sec:data-architecture" data-reference-type="autoref"
data-reference="sec:data-architecture">[sec:data-architecture]</a> and
drive the serving architecture designed in
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>.

### Related Work and Gap Analysis

Despite the maturity of individual security tools analyzed in the
preceding sections, no standard approach exists for consolidating their
output into a unified data platform. Organizations face a fragmented
landscape of partial solutions, each addressing a subset of the
integration challenge. This section surveys existing approaches,
evaluates the closest platform-native offering, and identifies the
research gap this thesis addresses.

#### Existing Approaches

define <span acronym-label="aspm"
acronym-form="singular+short">aspm</span> as a category of tools that
continuously manage application risk through the collection, analysis,
and prioritization of security issues across the software lifecycle.
Commercial platforms such as Apiiro, Cycode, ArmorCode, and Snyk AppRisk
aggregate findings from multiple tools into unified dashboards with
correlation and risk scoring. However, they are proprietary, operate as
black boxes, and create vendor lock-in: organizations cannot customize
data pipelines, apply their own <span acronym-label="ml"
acronym-form="singular+short">ml</span> models, or extend integrations
beyond vendor-supported options.

Platform-native security features offer another partial solution. GitHub
Advanced Security provides code scanning via CodeQL, secret scanning,
and dependency review within the GitHub ecosystem . GitLab bundles
<span acronym-label="sast" acronym-form="singular+short">sast</span>,
<span acronym-label="dast" acronym-form="singular+short">dast</span>,
dependency scanning, container scanning, and a security dashboard into
its platform . Both approaches are ecosystem-locked: they aggregate
findings only from their own scanners. Organizations using multiple
<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms or third-party security tools cannot consolidate findings
through these native dashboards.

DefectDojo  is the most prominent open-source alternative, supporting
imports from over 150 tools through format-specific parsers. However, it
was designed as a vulnerability management interface, not a data
platform. Its PostgreSQL backend limits enterprise-scale analytics, and
advanced <span acronym-label="api"
acronym-form="singular+short">api</span> connectors are available only
in the commercial offering. <span acronym-label="ocsf"
acronym-form="singular+short">ocsf</span>  standardizes security event
schemas for <span acronym-label="siem"
acronym-form="singular+short">siem</span> and <span acronym-label="soar"
acronym-form="singular+short">soar</span> use cases but does not model
application-level entities such as repositories, applications, or
development teams.

In practice, many enterprises build ad-hoc integrations: custom scripts
that pull data from security tool <span acronym-label="api"
acronym-form="plural+short">apis</span>, <span acronym-label="etl"
acronym-form="singular+short">etl</span> pipelines that load findings
into data warehouses, and dashboards assembled from manual exports.
These solutions are fragile. They lack schema governance, break when
source <span acronym-label="api" acronym-form="plural+short">apis</span>
change, and encode institutional knowledge in unmaintained code. Each
organization reinvents the same integration patterns without reusable
abstractions or standard architectures.

#### Databricks Lakewatch

Databricks announced Lakewatch in March 2026 as an open, agentic
<span acronym-label="siem" acronym-form="singular+short">siem</span>
built natively on the Databricks lakehouse . The platform unifies
security, <span acronym-label="it"
acronym-form="singular+short">it</span>, and business data in a single
governed environment powered by Delta Lake and Unity Catalog. Key
capabilities include agentic triage (<span acronym-label="ai"
acronym-form="singular+short">ai</span> agents that parse and enrich
telemetry across formats), Detection-as-Code (version-controlled
detection rules), and an open ecosystem with integrations from security
vendors including Wiz, Palo Alto Networks, Okta, and Zscaler.

Lakewatch and the framework proposed in this thesis address different
security domains. Lakewatch focuses on runtime security operations:
threat detection, incident response, alert triage, and log analytics.
The framework focuses on application security posture: vulnerability
findings from <span acronym-label="sast"
acronym-form="singular+short">sast</span>, <span acronym-label="sca"
acronym-form="singular+short">sca</span>, <span acronym-label="dast"
acronym-form="singular+short">dast</span>, secret scanning, container
scanning, and <span acronym-label="iac"
acronym-form="singular+short">iac</span> tools, combined with
remediation tracking and risk aggregation. Their data sources differ
accordingly: Lakewatch ingests security logs and telemetry, while the
framework ingests security tool findings and application metadata.

The two systems are complementary rather than competing. Shared
lakehouse infrastructure enables data exchange: Lakewatch could consume
the framework’s application risk scores as enrichment context for
incident triage, while the framework could ingest Lakewatch’s runtime
detections as an additional finding source. Together, they cover both
proactive posture management and reactive threat detection.

#### Comparative Analysis and Research Gap

<a href="#tab:related-work-comparison" data-reference-type="autoref"
data-reference="tab:related-work-comparison">[tab:related-work-comparison]</a>
compares the surveyed approaches against criteria derived from the
domain analysis in
<a href="#sec:app-inventory" data-reference-type="autoref"
data-reference="sec:app-inventory">[sec:app-inventory]</a> through
<a href="#sec:data-eng-analysis" data-reference-type="autoref"
data-reference="sec:data-eng-analysis">[sec:data-eng-analysis]</a>. The
criteria reflect requirements that emerged from analyzing security data
sources, integration patterns, and stakeholder consumption needs.

<div id="tab:related-work-comparison">

| **Criterion**            | **ASPM** | **Platform-native** | **DefectDojo** | **Lakewatch** | **This thesis** |
|:-------------------------|:--------:|:-------------------:|:--------------:|:-------------:|:---------------:|
| Open-source              |    –     |          –          |      Yes       |       –       |       Yes       |
| Vendor-agnostic model    |    –     |          –          |    Partial     |       –       |       Yes       |
| Extensible connectors    |    –     |          –          |      Yes       |    Partial    |       Yes       |
| Lakehouse architecture   |    –     |          –          |       –        |      Yes      |       Yes       |
| OLAP + OLTP serving      |    –     |          –          |       –        |       –       |       Yes       |
| Data quality enforcement |    –     |          –          |       –        |       –       |       Yes       |
| AppSec-specific model    |   Yes    |       Partial       |      Yes       |       –       |       Yes       |
| Enterprise scalability   |   Yes    |       Partial       |       –        |      Yes      |       Yes       |

Comparison of Existing Approaches

</div>

No existing approach satisfies all criteria. Commercial
<span acronym-label="aspm" acronym-form="singular+short">aspm</span>
platforms are proprietary and inflexible, preventing organizations from
customizing pipelines or applying their own analytical models.
Platform-native aggregations are ecosystem-locked and cannot consolidate
findings across tool boundaries. DefectDojo lacks the data architecture
for enterprise-scale analytics. Lakewatch addresses a different security
domain: runtime operations rather than application security posture.
Academic literature on application security consolidation as a data
engineering problem is limited, with most work focusing on detection
techniques rather than cross-tool integration at enterprise scale.

This thesis fills the gap with an open, vendor-agnostic framework that
treats application security consolidation as a data engineering problem.
The framework applies lakehouse architecture and medallion data
organization to ingest heterogeneous security tool output, normalize it
into a unified domain model, and serve it through both
<span acronym-label="olap" acronym-form="singular+short">olap</span> and
<span acronym-label="oltp" acronym-form="singular+short">oltp</span>
interfaces. The design is extensible: adding a new data source requires
only a connector module, without changes to the core pipeline.
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> presents the framework
design, and <a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> demonstrates
its implementation.

## Framework

<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> analyzed the sources,
patterns, and gaps in enterprise application security data integration.
This chapter presents the proposed framework: a reusable blueprint that
defines the architecture, data model patterns, connector abstractions,
and extension points an organization follows to build its own
implementation. The framework is prescriptive but platform-aware; it
targets the Databricks lakehouse but separates general patterns from
platform-specific choices.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> demonstrates
a concrete instance of this blueprint.

### Solution Architecture

This section presents the framework’s architecture at three levels:
technology stack, component structure, and data layer organization. The
architecture addresses the requirements identified across the domain
analysis: heterogeneous source ingestion, vendor-agnostic normalization,
dual <span acronym-label="olap"
acronym-form="singular+short">olap</span>/<span acronym-label="oltp"
acronym-form="singular+short">oltp</span> serving, and extensibility for
new data sources and analytics.

#### Technology Stack

The framework targets the Databricks platform on
<span acronym-label="aws" acronym-form="singular+short">aws</span>. A
key architectural property of the platform is the separation of storage
and compute: data resides in cloud object storage while processing
engines scale independently, enabling cost-efficient handling of the
bursty, heterogeneous workloads typical of security data integration .
This subsection maps platform components to framework roles.

##### Delta Lake

Delta Lake is an open table format that adds <span acronym-label="acid"
acronym-form="singular+short">acid</span> transactions, schema
enforcement, and time travel to cloud object storage . It provides the
storage layer for all three medallion tiers. Schema evolution support
allows bronze tables to absorb new source fields without pipeline
changes. Time travel enables auditing and rollback, critical for a
security data platform where data integrity and reproducibility are
non-negotiable. demonstrated that the lakehouse architecture built on
Delta Lake achieves both warehouse-grade governance and data lake
flexibility, the combination required by the heterogeneous source
landscape analyzed in
<a href="#sec:source-integration-summary" data-reference-type="autoref"
data-reference="sec:source-integration-summary">[sec:source-integration-summary]</a>.

##### Unity Catalog

Unity Catalog provides unified data governance across the lakehouse . It
manages a three-level namespace (`catalog.schema.table`) that maps
directly to the medallion layer organization: one catalog per
environment, schemas for each source (bronze) and each domain (silver,
gold). Fine-grained access control enforces least-privilege access to
security data, which often contains sensitive vulnerability details.
Automated lineage tracking records data flow from source through
transformations to consumption, supporting auditability requirements.
Column-level tags enable classification of sensitive fields such as
<span acronym-label="cve" acronym-form="singular+short">cve</span>
descriptions and remediation guidance.

##### Lakeflow Declarative Pipelines

<span acronym-label="dltables"
acronym-form="singular+short">dltables</span> is the pipeline
orchestration framework for defining batch and streaming
transformations . Pipelines are declared as Python or
<span acronym-label="sql" acronym-form="singular+short">sql</span>
functions with explicit dependencies; the framework resolves execution
order automatically. Data quality expectations are embedded directly in
pipeline definitions as declarative constraints (e.g., “severity must be
one of critical, high, medium, low”). Records that violate expectations
are quarantined without stopping the pipeline, implementing the
quarantine pattern described in
<a href="#sec:data-integration-patterns" data-reference-type="autoref"
data-reference="sec:data-integration-patterns">[sec:data-integration-patterns]</a>.
<span acronym-label="dltables"
acronym-form="singular+short">dltables</span> handles incremental
processing natively through change data feed, reducing reprocessing cost
for large datasets.

##### Lakebase

Lakebase is a serverless PostgreSQL database that provides the
<span acronym-label="oltp" acronym-form="singular+short">oltp</span>
serving layer . It shares the underlying storage layer with the
lakehouse, enabling gold-layer tables to be exposed as
<span acronym-label="oltp"
acronym-form="singular+short">oltp</span>-queryable tables without data
duplication. This architecture satisfies the dual serving requirement
identified in
<a href="#sec:data-architecture" data-reference-type="autoref"
data-reference="sec:data-architecture">[sec:data-architecture]</a>:
<span acronym-label="olap" acronym-form="singular+short">olap</span>
queries run against <span acronym-label="sql"
acronym-form="singular+short">sql</span> warehouses for dashboards and
trend analysis, while <span acronym-label="oltp"
acronym-form="singular+short">oltp</span> queries run against Lakebase
for low-latency operational workloads such as issue tracker integration,
remediation state lookups, and serving layer <span acronym-label="api"
acronym-form="plural+short">apis</span>. Lakebase supports
scale-to-zero, reducing cost for bursty workloads. Instant database
branching creates isolated copies for development and testing without
duplicating data.

##### Platform Synergies

Running all components on a single platform provides governance,
lineage, and compute benefits that would require significant integration
effort across disparate tools. Unity Catalog governs access uniformly
from bronze ingestion through gold serving. Lineage tracks data from
source <span acronym-label="api"
acronym-form="singular+short">api</span> through transformations to
dashboard queries. The shared compute and storage model eliminates data
movement between analytical and operational stores.

The platform also enables integration with Lakewatch, the Databricks
<span acronym-label="siem" acronym-form="singular+short">siem</span>
analyzed in <a href="#sec:lakewatch" data-reference-type="autoref"
data-reference="sec:lakewatch">[sec:lakewatch]</a>. Both systems share
Delta Lake storage and Unity Catalog governance. The framework’s
gold-layer outputs (application risk scores, remediation status) can
serve as enrichment signals for Lakewatch threat detection, while
Lakewatch’s runtime security events could feed back into the framework
as an additional finding source. This bidirectional potential reinforces
the complementarity identified in the related work analysis.

#### Component Design

With the platform components established, the framework organizes into
five tiers, illustrated in
<a href="#fig:component-design" data-reference-type="autoref"
data-reference="fig:component-design">[fig:component-design]</a>. Data
flows top-to-bottom from sources through the platform to consumers.

<figure id="fig:component-design">

<figcaption>Component Design</figcaption>
</figure>

**Data sources** are the external systems analyzed in
<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a>: application inventories,
<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms, <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> tools, security scanners, and
vulnerability databases. They are outside the framework’s boundary; the
framework consumes their <span acronym-label="api"
acronym-form="plural+short">apis</span> but does not control them.

**The ingestion tier** hosts connectors that extract data from sources
and land it in the bronze layer. Three connector categories serve
different integration scenarios. LakeFlow Connect connectors use the
platform’s managed ingestion service for declarative, zero-code
extraction. <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> connectors use source-provided
client libraries for programmatic extraction with built-in
authentication and pagination. <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> connectors use the open-source
<span acronym-label="dltool" acronym-form="singular+short">dltool</span>
library for sources that lack a dedicated <span acronym-label="sdk"
acronym-form="singular+short">sdk</span>. All connectors share common
concerns: authentication, pagination, rate limiting, and incremental
state management. The connector framework in
<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>
defines these patterns.

**The processing tier** implements the medallion architecture
(<a href="#sec:medallion-arch" data-reference-type="autoref"
data-reference="sec:medallion-arch">[sec:medallion-arch]</a>). Delta
Lake provides the storage layer; <span acronym-label="dltables"
acronym-form="singular+short">dltables</span> orchestrates the
transformations. Bronze stores raw ingested data in source-native
schemas. Silver normalizes it into the vendor-agnostic entity and
finding model defined in
<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a>. Gold
computes aggregated metrics, <span acronym-label="ml"
acronym-form="singular+short">ml</span>-enriched scores, and
consumption-ready datasets. Unity Catalog governs access and tracks
lineage across all three layers.

**The serving tier** exposes processed data to downstream consumers.
<span acronym-label="sql" acronym-form="singular+short">sql</span>
warehouses serve <span acronym-label="olap"
acronym-form="singular+short">olap</span> queries for dashboards and
analytics. Lakebase serves <span acronym-label="oltp"
acronym-form="singular+short">oltp</span> workloads: low-latency
lookups, issue tracker integration, and operational
<span acronym-label="api" acronym-form="plural+short">apis</span>. A
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span> layer
provides <span acronym-label="http"
acronym-form="singular+short">http</span> access to the
<span acronym-label="oltp" acronym-form="singular+short">oltp</span>
store.

**Data consumers** are external systems that read from the serving tier:
issue trackers (Jira, ServiceNow), <span acronym-label="aspm"
acronym-form="singular+short">aspm</span> dashboards,
<span acronym-label="siem"
acronym-form="singular+short">siem</span>/<span acronym-label="soar"
acronym-form="singular+short">soar</span> platforms, and custom
reporting tools. Like data sources, consumers are outside the framework
boundary.

#### Medallion Architecture

The processing tier applies the medallion architecture pattern
introduced in
<a href="#sec:data-architecture" data-reference-type="autoref"
data-reference="sec:data-architecture">[sec:data-architecture]</a>. Each
layer is implemented as a Delta Lake schema within a single Unity
Catalog, providing unified governance and cross-layer lineage tracking.
<a href="#fig:medallion-design" data-reference-type="autoref"
data-reference="fig:medallion-design">[fig:medallion-design]</a>
illustrates the layer structure and the transformations between them.

<figure id="fig:medallion-design">

<figcaption>Medallion Layer Design</figcaption>
</figure>

##### Bronze Layer

The bronze layer stores raw data from each source system with minimal
transformation. Each connector writes to its own schema (e.g., `github`,
`servicenow`, `sonarqube`), preserving the source’s native data
structure. Records are appended with standard metadata columns:
ingestion timestamp, source system identifier, and batch identifier. No
business logic is applied at this layer; the goal is a faithful,
auditable copy of source data.

Bronze tables use a schema-on-read approach. New fields from source
<span acronym-label="api" acronym-form="singular+short">api</span>
changes are absorbed through additive schema evolution without breaking
existing pipelines. Partitioning by ingestion date enables efficient
time-range queries and supports retention policies. Records that fail
structural validation at ingestion (malformed <span acronym-label="json"
acronym-form="singular+short">json</span>, missing required fields) are
routed to per-source quarantine tables with diagnostic metadata.

##### Silver Layer

The silver layer is the system of record. Bronze-to-silver
transformations normalize heterogeneous source data into the
vendor-agnostic domain model defined in
<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a>. Three table
categories occupy this layer:

- **Entity tables** store normalized dimension data: applications,
  repositories, teams, commits, pull requests, pipeline runs,
  dependencies, and branch protection policies. Each entity table uses a
  surrogate key, a natural key from the source system, and
  `valid_from`/`valid_to` timestamps for change tracking.

- **Finding tables** store normalized security findings as fact records.
  Each finding carries a severity mapped to the canonical scale, a
  lifecycle status, the source tool identifier, and references to the
  affected entity (repository, application). Finding tables are
  organized by category: <span acronym-label="sast"
  acronym-form="singular+short">sast</span>, <span acronym-label="sca"
  acronym-form="singular+short">sca</span>, secrets,
  <span acronym-label="dast" acronym-form="singular+short">dast</span>,
  containers, and <span acronym-label="iac"
  acronym-form="singular+short">iac</span>.

- **Relationship tables** store many-to-many mappings:
  application-to-repository, finding-to-<span acronym-label="cve"
  acronym-form="singular+short">cve</span>, and cross-tool deduplication
  links.

The silver layer applies the data quality patterns from
<a href="#sec:data-integration-patterns" data-reference-type="autoref"
data-reference="sec:data-integration-patterns">[sec:data-integration-patterns]</a>:
severity harmonization, entity normalization, timestamp standardization,
and deduplication. <span acronym-label="dltables"
acronym-form="singular+short">dltables</span> expectations enforce
constraints declaratively; records that violate expectations are
quarantined rather than propagated.

##### Gold Layer

The gold layer computes consumption-ready datasets from silver data. Two
categories of gold tables serve distinct purposes:

- **Aggregation tables** compute metrics at defined grains: application
  risk scores, team remediation rates, <span acronym-label="mttr"
  acronym-form="singular+short">mttr</span> by severity,
  <span acronym-label="sla" acronym-form="singular+short">sla</span>
  compliance percentages, and time-series trend roll-ups. These tables
  power the dashboards and executive reports consumed through the
  <span acronym-label="olap" acronym-form="singular+short">olap</span>
  serving path.

- **<span acronym-label="ml"
  acronym-form="singular+short">ml</span>-enriched tables** store model
  outputs: composite risk scores, false positive predictions, and
  remediation time estimates. These scores augment the aggregation
  tables with predictive signals. The <span acronym-label="ml"
  acronym-form="singular+short">ml</span> workflow patterns are detailed
  in <a href="#sec:analytics-patterns" data-reference-type="autoref"
  data-reference="sec:analytics-patterns">[sec:analytics-patterns]</a>.

Gold tables use incremental refresh where possible: new silver records
trigger recomputation of only the affected aggregation partitions. Full
refresh is reserved for metrics that require global recomputation, such
as cross-application percentile rankings.

### Data Model

This section maps the conceptual domain model from
<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a> to physical
table designs across the three medallion layers. It defines reusable
schema patterns first, then applies them to produce the concrete entity,
finding, and aggregation tables the framework provides.

#### Schema Patterns

Schema patterns are reusable templates that standardize how tables are
created at each medallion layer. They ensure consistency across the data
model and lower the barrier for extending it with new entities or
sources. Four patterns cover the framework’s needs.

##### Bronze Pattern

Every bronze table follows the same structural convention. The source’s
native payload is stored alongside a fixed set of metadata columns:

- `_ingestion_timestamp` — when the record was ingested
  (<span acronym-label="utc" acronym-form="singular+short">utc</span>).

- `_source_system` — identifier of the originating tool or platform.

- `_batch_id` — unique identifier for the ingestion run, supporting
  idempotent replays.

- `_raw_payload` — the original <span acronym-label="json"
  acronym-form="singular+short">json</span> response or record,
  preserved for auditability.

Additional columns from the source’s native schema are included
alongside the raw payload through schema-on-read. New fields are
absorbed via additive schema evolution. Tables are partitioned by
ingestion date to support retention policies and efficient time-range
queries.

##### Silver Entity Pattern

Entity tables store normalized dimension data. Each follows a standard
structure:

- `id` — surrogate key (auto-generated).

- `natural_key` — the identifier from the source system (e.g.,
  repository full name, application `sys_id`).

- `source_system` — which tool or platform provided the record.

- `valid_from` / `valid_to` — timestamps for change tracking (Type 2
  slowly changing dimension). A `NULL` value in `valid_to` indicates the
  current version.

- Domain-specific columns — attributes defined by the entity type (e.g.,
  `criticality_tier` for applications, `primary_language` for
  repositories).

The natural key plus source system combination uniquely identifies a
record’s origin. The surrogate key provides a stable reference for
foreign keys even when source identifiers change.

##### Silver Finding Pattern

Finding tables store normalized fact data. Each follows a standard
structure:

- `finding_id` — surrogate key.

- `source_finding_id` — the identifier from the source tool.

- `source_tool` — which scanner produced the finding.

- `repository_id` — foreign key to the repository entity table.

- `severity` — normalized to the canonical four-level scale (critical,
  high, medium, low).

- `status` — normalized lifecycle state (open, confirmed, resolved,
  false_positive, wontfix).

- `detected_at` / `resolved_at` — <span acronym-label="utc"
  acronym-form="singular+short">utc</span> timestamps enabling
  <span acronym-label="mttr" acronym-form="singular+short">mttr</span>
  calculation.

- `rule_id` — the tool-specific rule or check that triggered the
  finding.

- Category-specific columns — attributes unique to the finding type
  (e.g., `file_path` and `line_range` for <span acronym-label="sast"
  acronym-form="singular+short">sast</span>, `package_name` and
  `installed_version` for <span acronym-label="sca"
  acronym-form="singular+short">sca</span>).

##### Relationship Pattern

Relationship tables store many-to-many mappings between entities. Each
contains foreign keys to both sides, a source system indicator, and
`valid_from`/`valid_to` timestamps to track when the relationship was
active. No payload columns are included; the table’s sole purpose is to
link entities. Examples include application-to-repository,
finding-to-<span acronym-label="cve"
acronym-form="singular+short">cve</span>, and cross-tool deduplication
links.

##### Gold Aggregation Pattern

Aggregation tables follow a grain-metric-period structure:

- **Grain columns** define the level of detail: the entity key
  (application, team, repository) and time period (day, week, month).

- **Metric columns** store computed values: finding counts by severity,
  <span acronym-label="mttr" acronym-form="singular+short">mttr</span>,
  <span acronym-label="sla" acronym-form="singular+short">sla</span>
  compliance percentage, risk score.

- **Period columns** store the time window: `period_start` and
  `period_end` (<span acronym-label="utc"
  acronym-form="singular+short">utc</span>).

- **Refresh metadata**: `computed_at` timestamp and refresh strategy
  indicator (incremental or full).

This structure enables consistent querying across all gold tables:
filter by grain, aggregate over periods, compare across entities.

#### Entity Model

The silver layer instantiates the schema patterns into concrete tables.
This subsection specifies the key tables organized by category: entities
(dimensions), findings (facts), reference data, and relationships.

##### Entity Tables

<a href="#tab:entity-tables" data-reference-type="autoref"
data-reference="tab:entity-tables">[tab:entity-tables]</a> lists the
entity tables and their key domain-specific columns. All tables include
the standard silver entity pattern columns (`id`, `natural_key`,
`source_system`, `valid_from`/`valid_to`).

<div id="tab:entity-tables">

| **Table**       | **Source**                                                                                                                              | **Key Domain Columns**                                                              |
|:----------------|:----------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------|
| applications    | <span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>                                                                    | name, criticality_tier, lifecycle_status, business_unit, compliance_scope           |
| repositories    | <span acronym-label="scm" acronym-form="singular+short">scm</span>                                                                      | full_name, primary_language, visibility, default_branch, archived, last_activity_at |
| teams           | <span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>/<span acronym-label="scm" acronym-form="singular+short">scm</span> | name, parent_team_id, contact_email                                                 |
| commits         | <span acronym-label="scm" acronym-form="singular+short">scm</span>                                                                      | sha, author, authored_at, message, repository_id                                    |
| pull_requests   | <span acronym-label="scm" acronym-form="singular+short">scm</span>                                                                      | number, title, state, author, created_at, merged_at, repository_id                  |
| pipeline_runs   | <span acronym-label="cicd" acronym-form="singular+short">cicd</span>                                                                    | pipeline_id, commit_sha, status, started_at, finished_at, repository_id             |
| dependencies    | <span acronym-label="sca" acronym-form="singular+short">sca</span>                                                                      | package_name, installed_version, license, ecosystem, repository_id                  |
| branch_policies | <span acronym-label="scm" acronym-form="singular+short">scm</span>                                                                      | required_reviewers, require_status_checks, enforce_admins, repository_id            |

Silver Entity Tables

</div>

##### Finding Tables

Finding tables share the silver finding pattern columns and add
category-specific attributes.
<a href="#tab:finding-tables" data-reference-type="autoref"
data-reference="tab:finding-tables">[tab:finding-tables]</a> summarizes
each.

<div id="tab:finding-tables">

| **Table**          | **Category-Specific Columns**                                     |
|:-------------------|:------------------------------------------------------------------|
| sast_findings      | file_path, line_start, line_end, cwe_id, language                 |
| sca_findings       | package_name, installed_version, fixed_version, cve_id, ecosystem |
| secret_findings    | secret_type, file_path, commit_sha, validity_status               |
| dast_findings      | url, http_method, parameter, attack_type                          |
| container_findings | image_name, image_tag, layer, cve_id                              |
| iac_findings       | resource_type, resource_name, file_path, policy_id, benchmark     |

Silver Finding Tables

</div>

Each finding table references its repository through `repository_id`.
Business application context is derived through the relationship tables
rather than stored directly on findings, preserving the many-to-many
application-to-repository mapping without duplicating finding records.

##### Reference Tables

Reference tables store external intelligence used for enrichment:

- **vulnerabilities** — <span acronym-label="cve"
  acronym-form="singular+short">cve</span> records with description,
  published date, and <span acronym-label="cvss"
  acronym-form="singular+short">cvss</span> base score from the
  <span acronym-label="nvd" acronym-form="singular+short">nvd</span>.

- **epss_scores** — daily <span acronym-label="epss"
  acronym-form="singular+short">epss</span> probabilities per
  <span acronym-label="cve" acronym-form="singular+short">cve</span>,
  enabling time-series analysis of exploitation likelihood.

- **kev_entries** — <span acronym-label="cisa"
  acronym-form="singular+short">cisa</span> <span acronym-label="kev"
  acronym-form="singular+short">kev</span> catalog entries indicating
  confirmed active exploitation, with the date added.

These tables are refreshed on a scheduled basis from their respective
external sources. Findings link to them through
<span acronym-label="cve" acronym-form="singular+short">cve</span>
identifiers, forming the three-signal enrichment model described in
<a href="#sec:static-appsec" data-reference-type="autoref"
data-reference="sec:static-appsec">[sec:static-appsec]</a>.

##### Relationship Tables

Three relationship tables implement the key mappings identified in the
domain model:

- **app_repo_mapping** — links applications to repositories
  (many-to-many). This is the most critical relationship for business
  context attribution.

- **finding_cve_mapping** — links findings to <span acronym-label="cve"
  acronym-form="singular+short">cve</span> records, enabling
  vulnerability enrichment.

- **dedup_links** — links findings identified as duplicates across
  tools, preserving traceability to each source report while
  establishing a canonical finding.

#### Aggregation Model

The gold layer computes consumption-ready metrics from silver data using
the aggregation pattern. Each gold table targets a specific stakeholder
need identified in
<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a>.

##### Application Risk Scores

The `app_risk_scores` table computes a composite risk metric per
application per period. Grain columns are `application_id` and time
period. Metric columns include: open finding counts by severity,
weighted risk score (combining severity, <span acronym-label="epss"
acronym-form="singular+short">epss</span> probability, and application
criticality tier), <span acronym-label="sla"
acronym-form="singular+short">sla</span> compliance percentage, and a
trend indicator (improving, stable, degrading). This table serves
application owners who need a single view of their application’s
security posture.

##### Team Metrics

The `team_metrics` table aggregates remediation performance per team per
period. Metrics include: <span acronym-label="mttr"
acronym-form="singular+short">mttr</span> by severity, finding closure
rate, new vs. resolved finding ratio, and <span acronym-label="sla"
acronym-form="singular+short">sla</span> breach count. Leadership uses
these metrics for cross-team comparisons and resource allocation
decisions.

##### Vulnerability Trends

The `vulnerability_trends` table provides time-series data at
configurable grains (daily, weekly, monthly). Metrics include: new
findings introduced, findings resolved, net open count, severity
distribution shifts, and mean age of open findings. These trends power
the longitudinal dashboards that track organizational progress.

##### Coverage Analysis

The `coverage_analysis` table identifies gaps in security tool coverage.
For each repository, it records which tool categories have produced
findings or scan records (indicating active scanning) and which have
not. Missing coverage is flagged per category: a repository with no
<span acronym-label="sast" acronym-form="singular+short">sast</span>
findings and no <span acronym-label="sast"
acronym-form="singular+short">sast</span> pipeline runs likely lacks
static analysis integration. This table enables security teams to
prioritize tooling rollout.

##### Extension Guide

Adding a new gold table follows a consistent process: define the grain
(which entity, which time period), specify the metrics (what to
compute), write a silver-to-gold <span acronym-label="dltables"
acronym-form="singular+short">dltables</span> transformation, and
configure the refresh strategy (incremental or full). The aggregation
pattern ensures all gold tables share a common query interface, so
dashboards and reporting tools can consume new tables without structural
changes.

### Environment and Deployment

The solution architecture
(<a href="#sec:solution-arch" data-reference-type="autoref"
data-reference="sec:solution-arch">[sec:solution-arch]</a>) and data
model (<a href="#sec:data-model" data-reference-type="autoref"
data-reference="sec:data-model">[sec:data-model]</a>) define the
framework’s components and data structures. Before these can be
populated with connectors or analytics, the deployment environment must
be provisioned and the codebase organized. This section covers the
foundational setup: deployment strategy, project structure, pipeline
orchestration, monitoring, and deployment-level verification. These are
one-time decisions that establish the platform; the repeatable patterns
for extending the framework with new sources and analytics follow in
<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>
and <a href="#sec:analytics-serving" data-reference-type="autoref"
data-reference="sec:analytics-serving">[sec:analytics-serving]</a>.

#### Deployment Strategy

The framework uses Databricks Asset Bundles as its deployment
mechanism . A bundle is a declarative configuration that describes
Databricks resources (jobs, pipelines, cluster policies, permissions)
alongside the source code that implements them. A single
`databricks.yml` configuration file at the project root defines all
resource mappings, inter-resource dependencies, and environment-specific
parameter overrides. This approach treats the deployment as
<span acronym-label="iac" acronym-form="singular+short">iac</span>: the
entire platform configuration is version-controlled, reviewable, and
reproducible from a single source.

Three environment targets structure the promotion path: development,
staging, and production. Each target overrides a set of parameters: the
Unity Catalog catalog name (one catalog per environment, following the
namespace design from
<a href="#sec:tech-stack" data-reference-type="autoref"
data-reference="sec:tech-stack">[sec:tech-stack]</a>), compute cluster
sizing, permission grants, and pipeline scheduling intervals.
Development uses smaller clusters and relaxed permissions for rapid
iteration. Staging mirrors production configuration for pre-release
validation. Production enforces strict access controls, full-scale
compute, and scheduled execution.

A <span acronym-label="cicd" acronym-form="singular+short">cicd</span>
pipeline automates the build-test-deploy cycle . On each code change,
the pipeline executes three stages: validation checks bundle
configuration syntax and resource compatibility, testing runs the
project’s test suite against the development environment, and deployment
promotes the validated bundle to the target environment. Staging and
production deployments require an approval gate; only reviewed and
tested changes reach shared environments. The pipeline runs on standard
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
platforms (GitHub Actions, Azure DevOps, GitLab
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>)
that invoke the Databricks <span acronym-label="cli"
acronym-form="singular+short">cli</span> for bundle operations.

#### Project Structure

The project follows a monorepo layout: all connectors, transformations,
analytics, tests, and deployment configuration reside in a single
repository. This simplifies dependency management, enables atomic
cross-layer changes, and supports the bundle deployment model described
in <a href="#sec:deployment-strategy" data-reference-type="autoref"
data-reference="sec:deployment-strategy">[sec:deployment-strategy]</a>.
The repository organizes into four top-level directories: `src/` for
pipeline source code (connectors, transformations, analytics), `tests/`
for the test suite, `config/` for lookup tables and environment-specific
settings, and the bundle configuration files at the root.

Within `src/`, each connector is an independent module containing its
own ingestion and transformation logic. Shared utilities (authentication
helpers, pagination handlers, normalization functions) reside in a
common library that connectors import. Silver-to-gold transformations
are grouped by analytic rather than by source, since a single gold table
may consume data from multiple connectors. This boundary ensures that
adding a new connector requires changes only within its own module and
the relevant gold-layer pipelines.

Naming conventions enforce consistency across the platform. Unity
Catalog objects follow the pattern
`<env>.<layer>_<source>.<table_name>`: for example,
`prod.bronze_github.code_scanning_alerts` or
`prod.silver.sast_findings`. Pipeline names mirror their source module:
`ingest_github`, `transform_github_silver`. Column names use
`snake_case` throughout. These conventions reduce cognitive load and
simplify governance policies that rely on name-based access rules.

Configuration management separates secrets from non-sensitive settings.
Secrets (<span acronym-label="api"
acronym-form="singular+short">api</span> tokens, service account
credentials) are stored in the platform’s secret scope and referenced by
name in pipeline code; they never appear in source files or bundle
configuration. Non-sensitive settings (severity mapping tables,
<span acronym-label="sla" acronym-form="singular+short">sla</span>
thresholds, scheduling intervals) are version-controlled as
configuration files and loaded at pipeline runtime. Environment-specific
overrides in the bundle configuration select the appropriate catalog,
secret scope, and compute target for each deployment.

#### Pipeline Orchestration

Lakeflow Jobs is the orchestration engine that schedules and coordinates
pipeline execution . A job groups related tasks into a
<span acronym-label="dag" acronym-form="singular+short">dag</span> with
explicit dependencies; the engine executes tasks in dependency order and
handles retries on failure. Jobs are defined in the bundle configuration
alongside the resources they operate on, making orchestration
version-controlled and promotable across environments through the same
deployment path described in
<a href="#sec:deployment-strategy" data-reference-type="autoref"
data-reference="sec:deployment-strategy">[sec:deployment-strategy]</a>.

The framework assigns one job per connector. Each connector job contains
two sequential tasks: an ingestion task that extracts data from the
source <span acronym-label="api"
acronym-form="singular+short">api</span> into bronze, and a
transformation task that normalizes bronze records into silver. This
isolation gives each connector an independent failure domain: a GitHub
<span acronym-label="api" acronym-form="singular+short">api</span>
outage does not block ServiceNow ingestion. Gold-layer analytics run as
separate jobs that list their upstream connector jobs as dependencies;
the orchestrator starts a gold job only after all required silver data
is fresh. <span acronym-label="ml"
acronym-form="singular+short">ml</span> model retraining runs on
independent schedules, decoupled from the ingestion cycle.

Source characteristics drive scheduling frequency. High-change sources
(<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms, security scanners producing frequent new findings) run on
shorter intervals, typically hourly. Stable sources (application
inventory from the <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span>) run daily. External
enrichment sources follow their respective update cadences:
<span acronym-label="nvd" acronym-form="singular+short">nvd</span> and
<span acronym-label="epss" acronym-form="singular+short">epss</span>
update daily, <span acronym-label="cisa"
acronym-form="singular+short">cisa</span> <span acronym-label="kev"
acronym-form="singular+short">kev</span> updates on weekdays. Gold
analytics trigger after their upstream connector jobs complete through
explicit job dependencies. Where strict ordering adds unnecessary
complexity, such as daily reporting workloads, a schedule offset from
the expected ingestion window is an acceptable alternative.

Each task is configured with a retry count and backoff interval for
transient failures. If retries exhaust, the task fails and downstream
tasks within the same job do not execute. Job-level alerts notify
operators of persistent failures through configured channels (email,
messaging webhooks). Since connector jobs are independent, a single
connector degradation does not cascade. Jobs run in parallel on
ephemeral job clusters that are created at job start and terminated at
completion, preventing resource contention between connectors and
ensuring cost efficiency through right-sized compute per workload.

#### Monitoring and Observability

Orchestration ensures pipelines run on schedule; monitoring ensures they
run correctly over time. The platform provides system tables that record
job execution history, pipeline events, and compute utilization . The
framework builds on these tables to track three dimensions: data
freshness, pipeline health, and data quality trends. All monitoring
queries run against the same <span acronym-label="sql"
acronym-form="singular+short">sql</span> warehouse that serves
analytics, keeping the operational overhead within the platform.

Data freshness tracks the recency of data at each medallion layer. Each
bronze table records the timestamp of its last successful ingestion;
each silver table records its last transformation run. A freshness
monitor queries these timestamps and flags tables where the age exceeds
a configurable threshold. Thresholds reflect the scheduling frequency
from <a href="#sec:orchestration" data-reference-type="autoref"
data-reference="sec:orchestration">[sec:orchestration]</a>: an hourly
connector that has not produced data in two hours is stale; a daily
enrichment source that has not refreshed in 36 hours is stale. Freshness
violations trigger alerts through the same channels configured for job
failures.

Pipeline health aggregates job execution metrics from system tables. Key
indicators include: job success rate over a rolling window, mean run
duration and its trend (detecting performance degradation before it
causes timeouts), task-level retry frequency (high retry rates signal
intermittent source issues), and quarantine volume (records routed to
quarantine tables per ingestion run). A rising quarantine rate often
precedes data quality issues in the silver layer and warrants
investigation before downstream aggregations are affected.

Alerting bridges monitoring signals to operational response. The
framework configures alerts at two levels. Job-level alerts fire on
individual failures or threshold breaches, such as a quarantine rate
exceeding a configured percentage of ingested records. System-level
alerts fire on aggregate degradation: multiple connectors stale
simultaneously, overall pipeline success rate below a threshold, or gold
tables not refreshed within their expected window. Alerts are delivered
through configured channels (email, messaging webhooks, incident
management integrations). The thresholds and channels are defined as
configuration, not code, enabling operators to tune sensitivity without
redeploying pipelines.

#### Testing and Validation

This subsection covers deployment-level verification: the checks that
confirm the environment is correctly provisioned and the codebase meets
quality standards. Component-level testing patterns for connectors and
analytics are defined separately in
<a href="#sec:connector-testing" data-reference-type="autoref"
data-reference="sec:connector-testing">[sec:connector-testing]</a> and
<a href="#sec:analytics-testing" data-reference-type="autoref"
data-reference="sec:analytics-testing">[sec:analytics-testing]</a>.

The <span acronym-label="cicd" acronym-form="singular+short">cicd</span>
pipeline enforces quality gates before deployment. Linting validates
code style and catches common errors (unused imports, undefined
variables, type mismatches). Formatting ensures consistent code layout
across contributors. Unit tests verify individual functions (severity
mapping lookups, timestamp parsers, schema mapping logic) in isolation
from the platform. All gates must pass before the pipeline proceeds to
deployment.

After deployment, environment validation confirms that infrastructure
prerequisites are in place. Automated checks verify that Unity Catalog
objects (catalogs, schemas, tables) exist with expected permissions,
compute resources (clusters, <span acronym-label="sql"
acronym-form="singular+short">sql</span> warehouses) are configured and
accessible, secret scopes contain the required credentials, and
<span acronym-label="dltables"
acronym-form="singular+short">dltables</span> pipelines are registered.
These checks serve as smoke tests for newly provisioned or updated
environments. Failures block pipeline execution until the environment is
corrected.

The framework uses pytest markers to link individual tests to
requirement identifiers. Each test function carries a marker referencing
a specific requirement from
<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a>, such as
`@pytest.mark.requirement("REQ-SCA-001")`. A traceability matrix is
generated automatically from test results, mapping each requirement to
its covering tests and their pass/fail status. This pattern applies
uniformly across environment, connector
(<a href="#sec:connector-testing" data-reference-type="autoref"
data-reference="sec:connector-testing">[sec:connector-testing]</a>), and
analytics
(<a href="#sec:analytics-testing" data-reference-type="autoref"
data-reference="sec:analytics-testing">[sec:analytics-testing]</a>)
testing. The cross-cutting traceability matrix that summarizes coverage
across all components is produced in the reference implementation
(<a href="#sec:testing-validation" data-reference-type="autoref"
data-reference="sec:testing-validation">[sec:testing-validation]</a>).

### Connector Framework

The connector framework defines how data moves from the heterogeneous
sources analyzed in <a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> into the medallion layers
described in <a href="#sec:medallion-arch" data-reference-type="autoref"
data-reference="sec:medallion-arch">[sec:medallion-arch]</a>.
<a href="#sec:component-design" data-reference-type="autoref"
data-reference="sec:component-design">[sec:component-design]</a>
introduced three connector categories (LakeFlow Connect,
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>, and
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span> with
<span acronym-label="dltool"
acronym-form="singular+short">dltool</span>); this section specifies the
common abstraction they share, the patterns for landing data in bronze,
and the patterns for transforming it to silver. The goal is a repeatable
recipe: adding a new source requires implementing a well-defined set of
concerns against a new <span acronym-label="api"
acronym-form="singular+short">api</span>, not redesigning the pipeline.

#### Connector Abstraction

Every connector must handle the same set of cross-cutting concerns, but
the three connector categories introduced in
<a href="#sec:component-design" data-reference-type="autoref"
data-reference="sec:component-design">[sec:component-design]</a> differ
in how much of this work the developer performs versus the platform or
library.

##### Connector Categories

**LakeFlow Connect connectors** use the platform’s managed ingestion
service. They are declarative: the connector is configured through the
bundle definition, not coded. Authentication, pagination, incremental
state, and schema inference are handled by the platform. This category
suits sources with supported LakeFlow Connect integrations where
full-table ingestion meets requirements. The trade-off is limited
flexibility: custom transformation logic, selective field extraction,
and non-standard pagination cannot be injected.

**<span acronym-label="sdk" acronym-form="singular+short">sdk</span>
connectors** use a source-provided client library (e.g., the
<span acronym-label="aws" acronym-form="singular+short">aws</span>
<span acronym-label="sdk" acronym-form="singular+short">sdk</span> for
Python, PyGitHub, python-gitlab) for programmatic extraction. These
<span acronym-label="sdk" acronym-form="plural+short">sdks</span>
encapsulate authentication, pagination, rate limiting, and object model
mapping, letting the developer work with high-level methods rather than
raw <span acronym-label="http" acronym-form="singular+short">http</span>
requests. This category suits sources that offer an official
<span acronym-label="sdk" acronym-form="singular+short">sdk</span> with
good coverage of the required endpoints. The developer controls the
extraction logic, but the <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> handles the transport-level
concerns.

**<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span>
connectors with <span acronym-label="dltool"
acronym-form="singular+short">dltool</span>** use the open-source
<span acronym-label="dltool" acronym-form="singular+short">dltool</span>
library to build ingestion pipelines against sources that lack a
dedicated <span acronym-label="sdk"
acronym-form="singular+short">sdk</span>. The library provides pre-built
authentication, pagination, and incremental loading components that the
developer composes declaratively against the source’s
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span>. This
category handles the mechanical concerns (request construction, response
parsing, state management) while the developer specifies endpoints,
schema mapping, and extraction parameters.

The decision follows a preference order: use LakeFlow Connect if a
supported integration exists and meets requirements; use the source’s
<span acronym-label="sdk" acronym-form="singular+short">sdk</span> when
one is available with sufficient endpoint coverage; fall back to
<span acronym-label="dltool" acronym-form="singular+short">dltool</span>
for sources with only a <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span>. The five responsibilities
defined below represent the full contract. <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> connectors implement them
through <span acronym-label="dltool"
acronym-form="singular+short">dltool</span> library components.
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>
connectors delegate them to the client library. LakeFlow Connect
connectors satisfy them through platform configuration. The reference
implementation in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> demonstrates
all three categories.

##### Authentication

Security tool <span acronym-label="api"
acronym-form="plural+short">apis</span> use several authentication
mechanisms: <span acronym-label="pat"
acronym-form="plural+short">pats</span>, OAuth 2.0 client credentials,
and service account keys. The connector abstraction externalizes
credentials through a platform secret scope. Each connector declares
which credential type it requires; the framework resolves it at runtime.
This separation keeps secrets out of pipeline code and enables
credential rotation without redeploying connectors.

##### Pagination

The source integration summary in
<a href="#sec:source-integration-summary" data-reference-type="autoref"
data-reference="sec:source-integration-summary">[sec:source-integration-summary]</a>
shows that <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> are the dominant integration
surface. These <span acronym-label="api"
acronym-form="plural+short">apis</span> return results in pages. Two
pagination strategies cover the majority of sources: offset-based (page
number and size parameters) and cursor-based (an opaque token returned
with each response). The connector abstraction encapsulates the
pagination strategy so that downstream pipeline logic receives a
continuous stream of records regardless of the underlying mechanism.
GraphQL-based sources such as the GitHub <span acronym-label="api"
acronym-form="singular+short">api</span> use cursor-based pagination
exclusively.

##### Rate Limiting

Source <span acronym-label="api" acronym-form="plural+short">apis</span>
enforce rate limits, typically expressed as requests per time window.
The connector abstraction implements adaptive backoff: when a rate limit
response is received (<span acronym-label="http"
acronym-form="singular+short">http</span> 429), the connector pauses for
the duration specified in the response headers before retrying. For
sources without explicit rate limit headers, configurable per-source
rate limits prevent exceeding undocumented thresholds. Transient errors
(<span acronym-label="http" acronym-form="singular+short">http</span>
5xx) trigger exponential backoff with a configurable maximum retry
count.

##### Incremental State

Full re-ingestion does not scale for enterprise environments with large
data volumes, as discussed in
<a href="#sec:data-integration-patterns" data-reference-type="autoref"
data-reference="sec:data-integration-patterns">[sec:data-integration-patterns]</a>.
Each connector maintains a high-water mark: the timestamp or cursor of
the last successfully ingested record. On subsequent runs, the connector
resumes from this position, fetching only new or changed records. The
high-water mark is persisted in a state table within the bronze schema,
co-located with the data it tracks. For sources that support
<span acronym-label="cdc" acronym-form="singular+short">cdc</span>
(e.g., ServiceNow’s update set mechanism), the connector consumes change
events directly.

##### Extension Points

Adding a new source connector follows the category preference order. For
a LakeFlow Connect connector: register credentials, add the connector
configuration to the bundle definition, and map the landing tables to
the bronze schema. For an <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> connector: register
credentials, implement the extraction logic using the source’s client
library, define the high-water mark column, and configure the bronze
table. For a <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> connector with
<span acronym-label="dltool"
acronym-form="singular+short">dltool</span>: register credentials,
define the <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> source configuration (base
<span acronym-label="url" acronym-form="singular+short">url</span>,
endpoints, pagination type), and configure the
<span acronym-label="dltool" acronym-form="singular+short">dltool</span>
pipeline to land in the bronze schema. In all three cases, no changes to
the silver or gold layers are needed at this stage; transformation
patterns
(<a href="#sec:transformation-patterns" data-reference-type="autoref"
data-reference="sec:transformation-patterns">[sec:transformation-patterns]</a>)
handle the mapping separately.

#### Ingestion Patterns

Ingestion moves data from source <span acronym-label="api"
acronym-form="plural+short">apis</span> into the bronze layer. All
connectors follow the same landing pattern, with source-type-specific
variations described below.

##### Common Landing Pattern

Every ingestion run produces append-only writes to the target bronze
table. The full <span acronym-label="api"
acronym-form="singular+short">api</span> response is preserved in the
`_raw_payload` column alongside the metadata columns defined by the
bronze schema pattern
(<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>):
ingestion timestamp, source system identifier, and batch identifier. No
field filtering or transformation occurs at this stage; the bronze layer
is a faithful copy of source data.

The batch identifier enables idempotent replays. If a pipeline run fails
partway through, re-executing the same batch overwrites only the records
from that batch, preventing duplicates. For sources where merge
semantics are appropriate (e.g., entity snapshots from a
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>),
the connector uses upsert writes keyed on the source record’s natural
identifier.

Records that fail structural validation at landing, such as malformed
<span acronym-label="json" acronym-form="singular+short">json</span> or
responses with unexpected schema changes, are routed to per-source
quarantine tables. Each quarantine record includes the raw payload, the
error description, and the batch identifier. This quarantine pattern
ensures zero silent data loss: every record retrieved from a source is
either successfully landed or isolated with a documented failure
reason .

##### Source Code Management Sources

<span acronym-label="scm" acronym-form="singular+short">scm</span>
connectors pull repository metadata, commits, pull requests, and branch
protection configurations through <span acronym-label="rest"
acronym-form="singular+short">rest</span> or GraphQL
<span acronym-label="api" acronym-form="plural+short">apis</span>. These
sources produce moderate data volumes with frequent updates. The
high-water mark is typically the `updated_at` timestamp on the most
recently modified record. Webhook-triggered runs complement scheduled
pulls for near-real-time ingestion of events such as new pull requests
or merged commits.

##### Security Scanner Sources

Security scanner connectors handle the widest format diversity.
Server-based tools (SonarQube, Snyk, Dependency-Track) expose
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="plural+short">apis</span> with
paginated <span acronym-label="json"
acronym-form="singular+short">json</span> responses, similar to
<span acronym-label="scm" acronym-form="singular+short">scm</span>
sources. <span acronym-label="cli"
acronym-form="singular+short">cli</span>-based tools (Semgrep,
TruffleHog, Trivy) produce output files in <span acronym-label="json"
acronym-form="singular+short">json</span> or <span acronym-label="sarif"
acronym-form="singular+short">sarif</span> format  that must be
collected from <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> pipeline artifacts or uploaded
to a staging location. Platform-integrated scanners (GitHub Code
Scanning, GitLab Security) expose findings through their host platform’s
<span acronym-label="api" acronym-form="singular+short">api</span>,
sharing the same authentication and pagination infrastructure as the
<span acronym-label="scm" acronym-form="singular+short">scm</span>
connector for that platform.

For <span acronym-label="sarif"
acronym-form="singular+short">sarif</span>-producing tools, the
connector preserves the full <span acronym-label="sarif"
acronym-form="singular+short">sarif</span> document in the raw payload.
<span acronym-label="sarif" acronym-form="singular+short">sarif</span>
encodes results, rules, and tool metadata in a single structure, and
parsing it into individual findings is deferred to the transformation
layer.

##### Application Inventory Sources

<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
connectors differ from other sources in two ways. First, they must
traverse relationships: an application record references its owning
team, associated repositories, and dependent services through foreign
key attributes or relationship tables in the <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span>. The connector must resolve
these references during ingestion, either by following relationship
<span acronym-label="api" acronym-form="plural+short">apis</span> or by
ingesting related tables separately and joining them in the
transformation layer. Second, <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> data includes
organization-specific custom attributes (e.g., compliance scope, data
classification) that vary across deployments. The schema-on-read
approach at the bronze layer absorbs these custom fields without
requiring connector changes.

#### Transformation Patterns

Transformations move data from the bronze layer to the silver entity and
finding tables defined in
<a href="#sec:entity-model" data-reference-type="autoref"
data-reference="sec:entity-model">[sec:entity-model]</a>. Each
transformation is a <span acronym-label="dltables"
acronym-form="singular+short">dltables</span> pipeline that reads from
one or more bronze tables and writes to a silver table. Five patterns
compose the bronze-to-silver path.

##### Schema Mapping

Each source connector has a corresponding schema mapping that extracts
typed columns from the bronze raw payload. The mapping defines which
<span acronym-label="json" acronym-form="singular+short">json</span>
fields correspond to which silver columns, applies type casts (e.g.,
string timestamps to <span acronym-label="utc"
acronym-form="singular+short">utc</span> datetime), and assigns the
surrogate key. Mappings are defined declaratively as column expressions
in the <span acronym-label="dltables"
acronym-form="singular+short">dltables</span> pipeline, making them easy
to review and update when source schemas change.

##### Normalization

Three normalization rules bring heterogeneous source data to a common
form:

- **Severity harmonization.** Tools use different severity scales, as
  described in
  <a href="#sec:static-appsec" data-reference-type="autoref"
  data-reference="sec:static-appsec">[sec:static-appsec]</a>. The
  framework maps each tool’s native scale to the canonical four-level
  model (critical, high, medium, low) through per-tool lookup tables.
  These tables are maintained as configuration, not code, enabling
  updates without pipeline changes.

- **Status normalization.** Finding lifecycle states vary across tools
  (e.g., SonarQube’s “confirmed” vs. GitHub’s “open”). A per-tool status
  mapping translates each tool’s states to the canonical five-state
  model (open, confirmed, resolved, false_positive, wontfix).

- **Timestamp standardization.** All timestamps are converted to
  <span acronym-label="utc" acronym-form="singular+short">utc</span>.
  Source-specific formats (ISO 8601, Unix epoch, tool-specific strings)
  are parsed during schema mapping and stored as
  <span acronym-label="utc" acronym-form="singular+short">utc</span>
  datetime columns.

##### Data Quality Validation

<span acronym-label="dltables"
acronym-form="singular+short">dltables</span> expectations enforce
constraints on every record entering the silver layer. Expectations are
declared alongside the transformation logic and checked at runtime.
Examples include: severity must be one of the four canonical values,
status must be one of the five canonical states, repository foreign keys
must reference an existing silver entity, and timestamps must fall
within a plausible range. Records that violate expectations are
quarantined rather than propagated, consistent with the quarantine
pattern applied at ingestion.

##### Deduplication

When multiple tools scan the same repository, overlapping findings must
be identified and linked. Three deduplication strategies handle
different overlap scenarios:

- **Exact <span acronym-label="cve"
  acronym-form="singular+short">cve</span> match.** Two
  <span acronym-label="sca" acronym-form="singular+short">sca</span>
  findings referencing the same <span acronym-label="cve"
  acronym-form="singular+short">cve</span> and package in the same
  repository are duplicates. This is the simplest case.

- **Location-based matching.** Two <span acronym-label="sast"
  acronym-form="singular+short">sast</span> findings targeting the same
  file, line range, and weakness category (mapped via
  <span acronym-label="cwe" acronym-form="singular+short">cwe</span>) in
  the same repository are likely duplicates. A confidence threshold
  accounts for minor line number differences caused by tool-specific
  parsing.

- **Cross-category correlation.** A secret detected by both a
  <span acronym-label="cli"
  acronym-form="singular+short">cli</span>-based scanner and a
  platform-integrated scanner at the same file path and commit is a
  duplicate. Matching uses the secret type and file location.

Deduplicated findings are not deleted. Instead, a deduplication link
record is created in the `dedup_links` relationship table
(<a href="#sec:entity-model" data-reference-type="autoref"
data-reference="sec:entity-model">[sec:entity-model]</a>), preserving
traceability to each source report while establishing a canonical
finding for aggregation. Deduplication pairs are enumerated per tool
combination in the reference implementation
(<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>).

##### Business Context Attribution

The final transformation step links findings to business applications.
The `app_repo_mapping` relationship table maps repositories to
applications. Since this mapping is many-to-many (one application may
span multiple repositories; one repository may serve multiple
applications), findings inherit application context through a join
rather than a direct foreign key. This join enables the gold-layer
aggregations in
<a href="#sec:aggregation-model" data-reference-type="autoref"
data-reference="sec:aggregation-model">[sec:aggregation-model]</a> to
compute per-application metrics. The mapping itself is sourced from the
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
connector and can be supplemented by automated repository-to-application
inference in the <span acronym-label="ml"
acronym-form="singular+short">ml</span> workflows described in
<a href="#sec:analytics-patterns" data-reference-type="autoref"
data-reference="sec:analytics-patterns">[sec:analytics-patterns]</a>.

#### Testing and Validation

Connector tests use the pytest infrastructure and requirement markers
established in <a href="#sec:env-testing" data-reference-type="autoref"
data-reference="sec:env-testing">[sec:env-testing]</a>. Three additional
libraries complete the connector testing stack. An
<span acronym-label="http" acronym-form="singular+short">http</span>
request mocking library (such as `responses` or `requests-mock`)
intercepts <span acronym-label="api"
acronym-form="singular+short">api</span> calls to simulate source system
behavior without network access. A PySpark DataFrame assertion library
(such as `chispa`) compares transformation outputs against expected
results with clear diff reporting. <span acronym-label="dltables"
acronym-form="singular+short">dltables</span> expectations, defined
alongside transformation logic, provide runtime data quality validation
within pipeline execution. Together, these tools enable isolated,
reproducible tests that run in the <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> pipeline without depending on
live source systems.

Ingestion tests verify the connector abstraction concerns from
<a href="#sec:connector-abstraction" data-reference-type="autoref"
data-reference="sec:connector-abstraction">[sec:connector-abstraction]</a>.
Authentication tests confirm that credentials are resolved from the
secret scope and that invalid or expired tokens produce clear error
messages rather than silent failures. Pagination tests supply multi-page
mock responses and verify that the connector retrieves all pages without
data loss or duplication. Rate limit tests simulate
<span acronym-label="http" acronym-form="singular+short">http</span> 429
responses and verify that the connector pauses and retries according to
the backoff policy. Incremental state tests run the connector twice with
an intermediate data change and confirm the second run fetches only new
records, resuming correctly from the persisted high-water mark. Shared
test fixtures provide reusable mock response generators for common
<span acronym-label="api" acronym-form="singular+short">api</span>
patterns.

Transformation tests verify the bronze-to-silver path from
<a href="#sec:transformation-patterns" data-reference-type="autoref"
data-reference="sec:transformation-patterns">[sec:transformation-patterns]</a>.
Schema mapping tests supply known bronze payloads and assert that silver
columns have correct types, values, and null handling. Severity
normalization tests verify that every value in the tool’s native
severity scale maps to the correct canonical level; the test dataset
must cover all source-specific values, including edge cases such as
“informational” or “unknown” that the tool may produce. Status
normalization tests cover all tool-specific lifecycle states similarly.
Timestamp tests cover format edge cases: ISO 8601 with and without
timezone offsets, Unix epoch in seconds and milliseconds, and
tool-specific string formats. Tests are data-driven: each case is a pair
of (input bronze record, expected silver record), maintained as
<span acronym-label="json" acronym-form="singular+short">json</span>
fixtures alongside the connector module.

Data quality tests verify <span acronym-label="dltables"
acronym-form="singular+short">dltables</span> expectation behavior. For
each expectation defined on a silver table, a test supplies a record
that violates the constraint and confirms it is routed to the quarantine
table. A complementary test supplies a valid record and confirms it
passes through. Deduplication tests supply known duplicate pairs (same
<span acronym-label="cve" acronym-form="singular+short">cve</span> and
package for <span acronym-label="sca"
acronym-form="singular+short">sca</span>, same file, line range, and
<span acronym-label="cwe" acronym-form="singular+short">cwe</span> for
<span acronym-label="sast" acronym-form="singular+short">sast</span>,
same file path and commit for secrets) and verify that correct
`dedup_links` records are created. Negative cases supply similar but
distinct findings and verify they are not incorrectly linked.

Every connector must pass tests covering: authentication and credential
resolution, pagination across multiple response pages, rate limit
backoff, incremental state resume, schema mapping for all ingested
endpoints, severity and status normalization for all source-specific
values, at least one data quality expectation per silver table, and
deduplication for all applicable tool overlap pairs. New connectors are
not merged until this suite passes in the <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> pipeline.

### Analytics and Serving Framework

The data model (<a href="#sec:data-model" data-reference-type="autoref"
data-reference="sec:data-model">[sec:data-model]</a>) and connector
framework
(<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>)
defined how data is structured and ingested. This section addresses the
final stage: computing consumption-ready insights from silver data and
delivering them to stakeholders.
<a href="#sec:aggregation-model" data-reference-type="autoref"
data-reference="sec:aggregation-model">[sec:aggregation-model]</a>
defined *which* gold tables the framework provides; this section defines
*how* those computations are structured and how the results reach
consumers through analytical, operational, and event-driven channels.

#### Analytics Patterns

Gold-layer computations fall into two categories: rule-based analytics
that apply deterministic formulas to silver data, and
<span acronym-label="ml" acronym-form="singular+short">ml</span>-driven
analytics that learn patterns from historical data. Both produce outputs
that follow the gold aggregation pattern defined in
<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>.

##### Rule-Based Analytics

Rule-based analytics implement deterministic business logic as
<span acronym-label="sql" acronym-form="singular+short">sql</span>
transformations or <span acronym-label="dltables"
acronym-form="singular+short">dltables</span> pipelines. Three
computation patterns cover the framework’s needs.

**Composite scoring** combines multiple signals into a single metric.
The application risk score, for example, weights open finding counts by
severity, multiplies by <span acronym-label="epss"
acronym-form="singular+short">epss</span> exploitation probability, and
factors in the application’s criticality tier. The formula is
configurable: organizations assign weights to each signal based on their
risk appetite. <span acronym-label="sla"
acronym-form="singular+short">sla</span> compliance calculations follow
the same pattern, comparing finding ages against severity-specific
thresholds to produce a compliance percentage.

**Time-series aggregation** rolls up finding data at daily, weekly, and
monthly grains. Each roll-up computes period metrics (new findings,
resolved findings, net open count) and derived indicators
(period-over-period change, moving averages, severity distribution
shifts). These aggregations power the trend dashboards that track
organizational progress over time.

**Threshold classification** assigns categorical labels based on metric
values. Risk tiers (critical, high, medium, low) are assigned to
applications based on their composite score. Coverage gaps are flagged
when a repository lacks scan records for a tool category.
<span acronym-label="sla" acronym-form="singular+short">sla</span>
breaches are marked when open finding age exceeds the severity-specific
threshold. These classifications enable filtering and alerting in
downstream serving.

Two refresh strategies apply to rule-based analytics. **Incremental
refresh** recomputes only the partitions affected by new silver records;
this suits most aggregations where each record maps to a single grain
partition (e.g., one application, one time period). **Full refresh**
recomputes the entire table; this is necessary for metrics that depend
on global state, such as cross-application percentile rankings or
organization-wide severity distributions.

##### ML-Driven Analytics

<span acronym-label="ml" acronym-form="singular+short">ml</span>-driven
analytics learn patterns from historical silver and gold data to produce
predictive signals that rule-based formulas cannot capture. The
framework supports four use cases.

**Composite risk scoring** predicts which applications carry the highest
real risk by combining finding data with development activity signals
(commit frequency, dependency age, remediation velocity). Unlike the
rule-based risk score that weights predefined signals, the
<span acronym-label="ml" acronym-form="singular+short">ml</span> model
learns which combinations of factors historically preceded security
incidents.

**False positive prediction** estimates the probability that a new
finding is a false positive, based on patterns in historical triage
decisions. Features include the source tool, rule identifier, file type,
finding age at triage, and the repository’s historical false positive
rate for the same rule. High-confidence predictions reduce noise for
developers by deprioritizing likely false positives in dashboards and
notifications.

**Remediation time estimation** predicts <span acronym-label="mttr"
acronym-form="singular+short">mttr</span> for new findings based on
historical resolution data. Features include severity, tool category,
repository activity level, team workload, and dependency complexity.
These predictions inform <span acronym-label="sla"
acronym-form="singular+short">sla</span> compliance forecasting and
resource allocation.

**Anomaly detection** identifies unusual patterns: unexpected spikes in
finding volumes, sudden changes in severity distributions, or new
finding categories appearing in previously clean repositories. These
signals flag potential tool misconfigurations, new attack surfaces, or
integration issues that warrant investigation.

The <span acronym-label="ml" acronym-form="singular+short">ml</span>
workflow uses three platform components. MLflow provides experiment
tracking, model versioning, and a model registry that manages the
lifecycle from development through staging to production . The Feature
Store provides reusable feature tables computed from silver and gold
data, ensuring consistent feature definitions across training and
inference . Model Serving exposes registered models as real-time
inference endpoints for latency-sensitive predictions.

Model outputs integrate into the gold layer through two paths. Batch
predictions (risk scores, false positive probabilities) are written to
dedicated columns on gold tables during scheduled pipeline runs,
augmenting the rule-based metrics with predictive signals. Real-time
predictions (on-demand risk assessments for newly ingested findings) are
served through inference endpoints and cached in Lakebase for
low-latency access.

##### Extension Blueprint

Adding a new analytics workflow follows a consistent process regardless
of type. First, define the business question the analytic answers and
identify the stakeholder it serves. Second, determine whether a
rule-based formula or an <span acronym-label="ml"
acronym-form="singular+short">ml</span> model is appropriate: rule-based
suits well-understood relationships with clear formulas;
<span acronym-label="ml" acronym-form="singular+short">ml</span> suits
pattern recognition over complex, high-dimensional data. Third,
implement the computation as a <span acronym-label="dltables"
acronym-form="singular+short">dltables</span> pipeline (rule-based) or
an MLflow-tracked experiment (<span acronym-label="ml"
acronym-form="singular+short">ml</span>). Fourth, wire the output to a
gold table following the aggregation pattern, configure the refresh
strategy, and register the new table in Unity Catalog for governance and
lineage tracking.

#### Serving Patterns

The serving layer delivers gold-layer outputs to the data consumers
identified in
<a href="#sec:component-design" data-reference-type="autoref"
data-reference="sec:component-design">[sec:component-design]</a>. Three
delivery modes address different access patterns and latency
requirements.

##### Analytical Serving

Analytical serving targets dashboards, reporting tools, and ad-hoc
analysis through the <span acronym-label="olap"
acronym-form="singular+short">olap</span> path. A
<span acronym-label="sql" acronym-form="singular+short">sql</span>
warehouse executes queries against gold-layer Delta tables, providing
sub-five-second response times for pre-computed aggregations.
Materialized views cache frequently accessed query patterns, reducing
compute cost for recurring dashboard refreshes.

Stakeholder-specific views organize gold data for each audience:
executive risk overviews surface application risk scores and
organizational trends, team dashboards present remediation metrics and
<span acronym-label="sla" acronym-form="singular+short">sla</span>
compliance, and security engineering views expose tool coverage gaps and
deduplication statistics. These views are implemented as
<span acronym-label="sql" acronym-form="singular+short">sql</span> views
on top of the gold tables, not separate data copies, ensuring
consistency across all consumers.

##### Operational Serving

Operational serving targets low-latency workloads through the
<span acronym-label="oltp" acronym-form="singular+short">oltp</span>
path. Lakebase exposes gold-layer tables as PostgreSQL-queryable
relations with sub-50-millisecond response times . Because Lakebase
shares the underlying storage layer with the lakehouse, gold tables are
accessible without data duplication or synchronization pipelines.

Three operational workloads use this path. Remediation state lookups
retrieve the current status, severity, and ownership of individual
findings for integration with developer workflows. Operational
<span acronym-label="api" acronym-form="plural+short">apis</span> expose
risk scores, coverage data, and finding details through the PostgREST
Data <span acronym-label="api" acronym-form="singular+short">api</span>,
providing <span acronym-label="http"
acronym-form="singular+short">http</span> access to any gold table
without custom <span acronym-label="api"
acronym-form="singular+short">api</span> code. <span acronym-label="ml"
acronym-form="singular+short">ml</span> inference results cached in
Lakebase serve real-time risk assessments for newly ingested findings.
Lakebase’s scale-to-zero capability reduces cost during off-peak periods
when operational queries are infrequent.

##### Event-Driven Serving

Event-driven serving pushes data to external systems rather than waiting
for them to query. This mode closes the loop between data analysis and
operational action.

**Automated issue creation** triggers when new critical findings or
<span acronym-label="sla" acronym-form="singular+short">sla</span>
breaches are detected. The framework creates work items in issue
trackers (Jira, ServiceNow) through their <span acronym-label="api"
acronym-form="plural+short">apis</span>, linking back to the finding
record in the platform. Idempotency guards prevent duplicate ticket
creation on pipeline re-runs.

**Threshold-based notifications** alert stakeholders when metrics cross
configured boundaries: a risk score exceeds a threshold, a new
<span acronym-label="kev"
acronym-form="singular+short">kev</span>-listed vulnerability is
detected, or <span acronym-label="sla"
acronym-form="singular+short">sla</span> compliance drops below a target
percentage. Notifications are delivered through configured channels
(email, messaging platforms, webhooks).

**<span acronym-label="siem"
acronym-form="singular+short">siem</span>/<span acronym-label="soar"
acronym-form="singular+short">soar</span> event feeds** push structured
security events to platforms such as Lakewatch
(<a href="#sec:lakewatch" data-reference-type="autoref"
data-reference="sec:lakewatch">[sec:lakewatch]</a>).
<span acronym-label="cdc" acronym-form="singular+short">cdc</span> on
gold tables generates a stream of change events, such as new critical
findings, risk score changes, or coverage regressions, that
<span acronym-label="soar" acronym-form="singular+short">soar</span>
playbooks consume for automated response. The shared infrastructure with
Lakewatch, described in
<a href="#sec:tech-stack" data-reference-type="autoref"
data-reference="sec:tech-stack">[sec:tech-stack]</a>, enables this
integration without external data movement.

**Bidirectional synchronization** keeps the framework’s view consistent
with external systems. Issue tracker status updates (e.g., a Jira ticket
moved to “Done”) flow back into the framework through scheduled polling
or webhooks, updating the corresponding finding’s lifecycle state in the
silver layer. This feedback loop ensures that remediation metrics in the
gold layer reflect actual resolution progress.

#### Testing and Validation

Analytics and serving tests extend the pytest infrastructure from
<a href="#sec:env-testing" data-reference-type="autoref"
data-reference="sec:env-testing">[sec:env-testing]</a> with additional
components. Gold-layer computation tests use PySpark DataFrame
assertions (the same library as connector tests) to validate aggregation
outputs against known silver inputs. <span acronym-label="ml"
acronym-form="singular+short">ml</span> model tests use MLflow’s
`evaluate()` <span acronym-label="api"
acronym-form="singular+short">api</span> to compute standard metrics and
`validate_evaluation_results()` to enforce minimum performance
thresholds before model promotion . Serving layer tests use
<span acronym-label="http" acronym-form="singular+short">http</span>
client libraries to verify endpoint response correctness and measure
latency against target thresholds.

Rule-based analytics tests verify the computations from
<a href="#sec:analytics-patterns" data-reference-type="autoref"
data-reference="sec:analytics-patterns">[sec:analytics-patterns]</a>.
Each test supplies a fixed set of silver records with known values and
asserts that the gold table output matches expected metrics exactly.
Composite scoring tests cover boundary conditions: zero findings (score
should be minimal), all-critical findings (maximum score), mixed
severity distributions, and cases where enrichment data
(<span acronym-label="epss" acronym-form="singular+short">epss</span>
scores, <span acronym-label="kev"
acronym-form="singular+short">kev</span> status) is missing for some
findings. Time-series aggregation tests verify correct period bucketing,
period-over-period change calculations, and handling of periods with no
activity. Threshold classification tests verify correct tier assignment
at each boundary value. Refresh idempotency tests run the same pipeline
twice on identical silver input and confirm no duplicate or changed gold
records.

<span acronym-label="ml" acronym-form="singular+short">ml</span> model
tests cover the full lifecycle from
<a href="#sec:analytics-patterns" data-reference-type="autoref"
data-reference="sec:analytics-patterns">[sec:analytics-patterns]</a>.
Training tests verify that models converge on the training dataset and
produce metrics (accuracy, precision, recall, F1 score) above configured
thresholds. Validation tests use a held-out dataset to check for
overfitting; the gap between training and validation metrics must remain
within a configured tolerance. Feature freshness tests verify that
Feature Store tables used for inference contain data no older than a
configured staleness threshold. Prediction drift tests compare recent
prediction distributions against a baseline and flag significant
statistical shifts. Model promotion tests use MLflow’s validation
<span acronym-label="api" acronym-form="singular+short">api</span> to
confirm that a candidate model meets or exceeds the currently registered
production model’s performance before promotion in the model registry.

Serving layer tests verify the three delivery modes from
<a href="#sec:serving-patterns" data-reference-type="autoref"
data-reference="sec:serving-patterns">[sec:serving-patterns]</a>.
Analytical serving tests execute representative dashboard queries
against the <span acronym-label="sql"
acronym-form="singular+short">sql</span> warehouse and verify response
times fall below the five-second target for pre-computed aggregations.
Operational serving tests query Lakebase endpoints and verify
sub-50-millisecond response times for single-record lookups and correct
<span acronym-label="json" acronym-form="singular+short">json</span>
response structure from the PostgREST <span acronym-label="api"
acronym-form="singular+short">api</span>. Event-driven serving tests
verify issue creation idempotency (triggering the same finding event
twice must not create duplicate tickets), notification delivery for
threshold breaches, and bidirectional synchronization consistency (an
external status update must propagate to the silver layer within the
configured polling interval).

Every gold table must include tests for metric correctness against known
inputs, boundary conditions, and refresh idempotency. Every
<span acronym-label="ml" acronym-form="singular+short">ml</span> model
must include training convergence, validation accuracy, drift
monitoring, and promotion gating tests. Every serving endpoint must
include response correctness and latency verification. New analytics or
serving configurations are not merged until this suite passes.

## Implementation

### Environment and Deployment

#### Workspace Setup

#### Silver Schema

#### Project Structure and CI/CD

#### Pipeline Orchestration

#### Monitoring and Observability

#### Testing and Validation

### Connectors

#### ServiceNow

#### GitHub

#### GitLab

#### SonarQube

#### Semgrep

#### Dependency-Track

#### TruffleHog

#### Vulnerability Enrichment

#### Testing and Validation

### Analytics and Serving

#### Application-Repository Mapping

#### Application Risk Scoring

#### Remediation and Compliance Metrics

#### Vulnerability Trends

#### Risk Prediction Model

#### Serving Layer

#### Testing and Validation

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
