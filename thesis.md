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
  - [Analysis and Requirements](#analysis-and-requirements)
- [Application Inventory](#application-inventory)
  - [Application Portfolio Management](#application-portfolio-management)
  - [Configuration Management Databases](#configuration-management-databases)
  - [Integration Options](#integration-options)
        - [ServiceNow APIs](#servicenow-apis)
        - [ServiceNow Application](#servicenow-application)
        - [Integration Challenges](#integration-challenges)
- [Software Development](#software-development)
  - [Source Code Management](#source-code-management)
  - [Continuous Integration and Delivery](#continuous-integration-and-delivery)
  - [Issue Tracking](#issue-tracking)
- [Application Security](#application-security)
  - [Static Application Security Testing](#static-application-security-testing)
  - [Software Composition Analysis](#software-composition-analysis)
  - [Secret Detection](#secret-detection)
  - [Dynamic Testing and Penetration Testing](#dynamic-testing-and-penetration-testing)
  - [Container Image Scanning](#container-image-scanning)
  - [Infrastructure as Code Security](#infrastructure-as-code-security)
  - [Runtime Security Monitoring](#runtime-security-monitoring)
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
  - [Reference Implementation](#reference-implementation)
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

## Analysis and Requirements

This chapter surveys the literature and analyzes the functional domains
relevant to building an application security data platform. Each section
covers one domain, combining theoretical foundations with practical tool
and <span acronym-label="api" acronym-form="singular+short">api</span>
analysis. The focus is on reviewing existing knowledge, observing source
system interfaces, data models, and integration patterns, not on
prescribing a solution. Technology choices for the target platform are
deferred to <a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> and
<a href="#ch:reference-implementation" data-reference-type="autoref"
data-reference="ch:reference-implementation">[ch:reference-implementation]</a>.

<a href="#sec:app-inventory" data-reference-type="autoref"
data-reference="sec:app-inventory">[sec:app-inventory]</a> establishes
the business context underlying all security findings.
<a href="#sec:sw-dev-analysis" data-reference-type="autoref"
data-reference="sec:sw-dev-analysis">[sec:sw-dev-analysis]</a> and
<a href="#sec:appsec-analysis" data-reference-type="autoref"
data-reference="sec:appsec-analysis">[sec:appsec-analysis]</a> examine
the software development and security tooling landscapes as data
sources. <a href="#sec:data-eng-analysis" data-reference-type="autoref"
data-reference="sec:data-eng-analysis">[sec:data-eng-analysis]</a>
covers the data engineering patterns that underpin the framework’s
design. Finally,
<a href="#sec:related-work" data-reference-type="autoref"
data-reference="sec:related-work">[sec:related-work]</a> surveys
existing solutions and identifies the gap this thesis addresses.

### Application Inventory

The application inventory is the foundational data source for any
application security data platform. It establishes the business context
for all security findings. Organizations typically manage this inventory
in a <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> or a custom-built catalog.
Without a reliable catalog of business applications and their mapping to
technical assets, a vulnerability discovered in a repository or a
running service cannot be attributed to an owner, assessed for business
impact, or prioritized against organizational risk criteria.

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
(e.g., PCI DSS, GDPR, SOX) apply to a given application.

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
acronym-form="singular+short">api</span> suite. Jenkins uses an
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

### Application Security

#### Static Application Security Testing

#### Software Composition Analysis

#### Secret Detection

#### Dynamic Testing and Penetration Testing

#### Container Image Scanning

#### Infrastructure as Code Security

#### Runtime Security Monitoring

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

## Reference Implementation

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
