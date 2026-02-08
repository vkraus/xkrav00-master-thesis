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
  - [Literature Review](#literature-review)
- [Software Development Literature](#software-development-literature)
  - [Source Code Management](#source-code-management)
  - [Software Development Lifecycle](#software-development-lifecycle)
  - [Application Security Data Standards](#application-security-data-standards)
- [Application Security Literature](#application-security-literature)
  - [Code Security](#code-security)
  - [Software Supply Chain Security](#software-supply-chain-security)
  - [Software Lifecycle Security](#software-lifecycle-security)
  - [Application Penetration Testing](#application-penetration-testing)
- [Data Modeling and Engineering Literature](#data-modeling-and-engineering-literature)
  - [Data Architecture](#data-architecture)
  - [Data Modeling and Pipelines](#data-modeling-and-pipelines)
- [Related Work and Gap Analysis](#related-work-and-gap-analysis)
  - [Requirement Analysis](#requirement-analysis)
- [Requirements Methodology](#requirements-methodology)
  - [Specification Format](#specification-format)
  - [Requirement Prioritization](#requirement-prioritization)
  - [Test-to-Requirement Linking](#test-to-requirement-linking)
        - [Unit and Integration Tests](#unit-and-integration-tests)
        - [Data Quality Expectations](#data-quality-expectations)
  - [Traceability Generation](#traceability-generation)
- [Personas](#personas)
  - [Application Owners](#application-owners)
  - [Application Developers](#application-developers)
  - [Security Experts](#security-experts)
  - [Development and Security Leadership](#development-and-security-leadership)
- [Data Sources](#data-sources)
  - [Application Inventory](#application-inventory)
  - [Tools for Software Development and Delivery](#tools-for-software-development-and-delivery)
  - [Runtime Infrastructure Platforms and Security Tools](#runtime-infrastructure-platforms-and-security-tools)
  - [Security Testing Tools](#security-testing-tools)
        - [Secret Scanning Tools](#secret-scanning-tools)
        - [Static Application Security Testing (SAST) Tools](#static-application-security-testing-sast-tools)
        - [Software Composition Analysis (SCA) Tools](#software-composition-analysis-sca-tools)
        - [Dynamic Application Security Testing (DAST) Tools](#dynamic-application-security-testing-dast-tools)
        - [Penetration Testing](#penetration-testing)
- [Data Transformations](#data-transformations)
  - [Data Ingestion and Validation](#data-ingestion-and-validation)
  - [Data Normalization](#data-normalization)
  - [Finding Deduplication](#finding-deduplication)
  - [Business Application Mapping](#business-application-mapping)
  - [Triage](#triage)
- [Data Consumers](#data-consumers)
  - [Remediation Tracking Systems](#remediation-tracking-systems)
  - [Application Security Posture Management (ASPM)](#application-security-posture-management-aspm)
  - [SOAR and SIEM](#soar-and-siem)
- [Non-Functional Requirements](#non-functional-requirements)
  - [Data Quality](#data-quality)
  - [Extensibility](#extensibility)
  - [Scalability](#scalability)
  - [Performance](#performance)
  - [Security](#security)
  - [Maintainability](#maintainability)
- [Requirement Specification](#requirement-specification)
  - [Data Ingestion](#data-ingestion)
  - [Data Processing](#data-processing)
  - [Data Serving](#data-serving)
  - [Non-Functional Requirements](#non-functional-requirements-1)
  - [Solution Architecture](#solution-architecture)
- [Architecture Context](#architecture-context)
- [Architecture Principles and Constraints](#architecture-principles-and-constraints)
- [Technology Selection](#technology-selection)
  - [Data Engineering Platform](#data-engineering-platform)
  - [Pipeline Framework](#pipeline-framework)
  - [Connectors](#connectors)
- [High-Level Solution Architecture](#high-level-solution-architecture)
- [Component Design](#component-design)
  - [Data Ingestion Tier](#data-ingestion-tier)
  - [Data Processing Tier](#data-processing-tier)
        - [Pipeline Architecture](#pipeline-architecture)
        - [Pipeline Orchestration](#pipeline-orchestration)
  - [Data Serving Tier](#data-serving-tier)
- [Integration Architecture](#integration-architecture)
  - [Connector Strategy](#connector-strategy)
        - [Application Inventory](#application-inventory-1)
        - [ServiceNow CMDB](#servicenow-cmdb)
        - [](#)
- [Extensibility Architecture](#extensibility-architecture)
- [Security Architecture](#security-architecture)
  - [Pipeline and Model Design](#pipeline-and-model-design)
- [Pipeline Overview](#pipeline-overview)
- [Bronze Layer](#bronze-layer)
  - [Transformations](#transformations)
  - [Schema](#schema)
- [Silver Layer](#silver-layer)
  - [Transformations](#transformations-1)
  - [Schema](#schema-1)
        - [Entities](#entities)
        - [Findings](#findings)
        - [Relationships](#relationships)
- [Gold Layer](#gold-layer)
  - [Transformations](#transformations-2)
        - [ML Enrichment](#ml-enrichment)
  - [Schema](#schema-2)
        - [Aggregations](#aggregations)
        - [Read-Optimized Views](#read-optimized-views)
  - [Implementation](#implementation)
- [Environment Setup](#environment-setup)
- [Connector Implementation](#connector-implementation)
- [Pipeline Implementation](#pipeline-implementation)
- [Pipeline Orchestration](#pipeline-orchestration-1)
- [Data Serving](#data-serving-1)
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

To protect business-critical applications from cybersecurity threats,
security teams need to use a large set of application security tools:
<span acronym-label="sast" acronym-form="singular+short">sast</span>
scanners analyze source code for vulnerabilities,
<span acronym-label="sca" acronym-form="singular+short">sca</span> tools
detect issues in software dependencies, <span acronym-label="dast"
acronym-form="singular+short">dast</span> solutions scan running
applications for exploitable weaknesses, and secret scanning tools
identify exposed credentials in code.

Further detection mechanisms need to be applied to software integration
and deployment pipelines that are prone to their own classes of threats.
Increasingly, security teams employ mechanisms that identify problems
before they even reach the version control system, either in the form of
IDE plugins or as security context tools integrated into AI coding
assistants like Github Copilot or Claude Code.

In large enterprises, there may be dozens of such vulnerability
detection tools, each producing findings through different
<span acronym-label="api" acronym-form="plural+short">apis</span>, data
formats, and integration patterns .

As application security architect in a large organization managing tens
of thousands of code repositories and thousands of developers, I have
witnessed firsthand how challenging it is to keep such a complex
environment secure. Most notably:

- Different detection tools of the same class capture different results
  as they employ different fundamental scanning paradigms

- The same vulnerability may be reported by multiple tools, requiring
  careful deduplication

- Findings lack context regarding business criticality of the software
  project or its threat exposure, both of which are critical
  determinants of how urgently a vulnerability needs to be remediated

- TODO more

I argue that the challenge of consolidating application security data
is, at its core, a data engineering problem. While the industry is
addressing this with commercial products categorized as
<span acronym-label="aspm" acronym-form="singular+short">aspm</span>
that offer dashboards and aggregated views, these solutions are
proprietary, expensive, and inflexible. They introduce vendor lock-in
and limit the ability of security teams to customize data pipelines,
apply their own machine learning models, or integrate with internal
systems on their own terms.

The most notable open-source alternative, DefectDojo, takes a different
approach: it is a Django-based web application designed primarily as a
vulnerability management interface. However, it was not built with a
data-first architecture in mind. Its scaling capabilities are limited by
the constraints of a traditional relational database backend, and its
data ingestion model relies predominantly on push-based integrations or
manual report uploads. Pull-based connectors that actively fetch data
from security tool <span acronym-label="api"
acronym-form="plural+short">apis</span> are available only in the
commercial DefectDojo Pro offering, further fragmenting the landscape
between open and proprietary solutions.

What is missing is a vendor-agnostic, data-first framework that treats
application security data as a first-class data engineering problem. One
that provides a reusable architecture for ingestion, normalization,
deduplication, and serving of security findings at enterprise scale.
This thesis aims to fill that gap.

### Objective

The main goal of this thesis is to design and implement a
vendor-agnostic data integration framework for enterprise application
security. The framework consolidates security findings from
heterogeneous tools into a unified data platform, enabling consistent
normalization, deduplication, triage, and correlation of vulnerabilities
across business applications.

To achieve this goal, I define the following subgoals:

1.  **Literature review**
    (<a href="#ch:literature-review" data-reference-type="autoref"
    data-reference="ch:literature-review">[ch:literature-review]</a>):
    Survey existing literature across three domains: software
    development practices, application security, and data engineering.
    Identify the theoretical foundations and the gap that motivates this
    work.

2.  **Requirement specification**
    (<a href="#ch:requirement-analysis" data-reference-type="autoref"
    data-reference="ch:requirement-analysis">[ch:requirement-analysis]</a>):
    Analyze the application security domain to identify personas, data
    sources, required data transformations, data consumers, and
    non-functional requirements. Produce a requirements specification
    for the framework, with the full specification included in the
    appendix.

3.  **Architecture**
    (<a href="#ch:architecture" data-reference-type="autoref"
    data-reference="ch:architecture">[ch:architecture]</a>): Propose a
    reusable and extensible architecture that satisfies both analytical
    and transactional use cases.

4.  **Pipeline and model design**
    (<a href="#ch:design" data-reference-type="autoref"
    data-reference="ch:design">[ch:design]</a>): Design the data model
    and processing pipeline following the medallion architecture
    pattern .

5.  **Implementation and validation**
    (<a href="#ch:implementation" data-reference-type="autoref"
    data-reference="ch:implementation">[ch:implementation]</a>): Use
    AI-assisted coding to build a reference implementation on the
    Databricks platform  and validate it against the requirements
    specification through automated testing with requirement
    traceability.

### Methodology

This thesis follows a design-science research methodology , structured
into three phases.

In the first phase, I conduct a **literature review** of academic and
industry sources across three domains: software development practices
and lifecycle, application security tools and standards, and data
engineering approaches, including data architecture and pipeline design.
This review establishes the theoretical foundation for the framework and
includes vendor documentation for the technologies used in the
implementation.

In the second phase, I perform a **requirements analysis and design**. I
analyze the application security landscape to identify the key personas,
data sources, required transformations, and non-functional requirements.
Requirements are prioritized using the MoSCoW method. Based on the
requirements, I propose an architecture and design a data model with a
medallion-based processing pipeline.

In the third phase, I build a **reference implementation** on the
Databricks platform to demonstrate feasibility of the proposed design. I
validate the implementation through automated tests with requirement
traceability, mapping individual tests to requirements, and through data
quality expectations enforced by <span acronym-label="dltables"
acronym-form="singular+short">dltables</span>.

The thesis delivers three distinct contributions:

1.  A **requirements specification** for an application security data
    platform that other organizations can adapt to their own needs.

2.  A **reusable design** covering architecture, data model, and
    pipeline that is not tied to a specific platform or vendor.

3.  A **reference implementation** on Databricks that proves the
    feasibility of the design and serves as a starting point for
    production deployments.

### Structure

This thesis is organized as follows.
<a href="#ch:literature-review" data-reference-type="autoref"
data-reference="ch:literature-review">[ch:literature-review]</a> surveys
the relevant literature on software development, application security,
and data engineering, and identifies the research gap.
<a href="#ch:requirement-analysis" data-reference-type="autoref"
data-reference="ch:requirement-analysis">[ch:requirement-analysis]</a>
defines the personas, data sources, transformations, consumers, and
non-functional requirements, culminating in a prioritized requirements
specification. <a href="#ch:architecture" data-reference-type="autoref"
data-reference="ch:architecture">[ch:architecture]</a> presents the
platform architecture, including technology selection and component
design. <a href="#ch:design" data-reference-type="autoref"
data-reference="ch:design">[ch:design]</a> details the medallion-based
data model and pipeline transformations across the bronze, silver, and
gold layers. <a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> describes the
reference implementation on Databricks, covering connector development,
pipeline orchestration, and testing. The Conclusion evaluates the
outcomes against the objectives defined above, discusses limitations,
and suggests directions for future work.

## Literature Review

### Software Development Literature

What process/activities are we securing with appsec?

Books like Code Complete, Clean Code, Pragmatic Programmer...

#### Source Code Management

git book, software engineering at Google, ...

#### Software Development Lifecycle

Traditional vs devops and CI/CD pipelines, list books on each

#### Application Security Data Standards

Standard data formats for vulnerabilities like <span acronym-label="cve"
acronym-form="singular+short">cve</span>

SARIF, CycloneDX, OCSF

Citing test , ,

<span acronym-label="aspm" acronym-form="singular+short">aspm</span>
mentioned for the first time, <span acronym-label="aspm"
acronym-form="singular+short">aspm</span> mentioned second time.

<span acronym-label="api" acronym-form="singular+short">api</span>

### Application Security Literature

In this section we focus on literature which explains the domain in
which we’re solving identified problems.

Books on general appsec

#### Code Security

#### Software Supply Chain Security

#### Software Lifecycle Security

#### Application Penetration Testing

Good source of wisdom for defensive teams - let’s defend against what
the attackers are doing

### Data Modeling and Engineering Literature

What tools do we have to achieve thesis goals?

#### Data Architecture

DWH

Lake

Lakehouse etc

#### Data Modeling and Pipelines

Data Modeling with Snowflake

DAMA-DMBOK

Medallion Architecture

### Related Work and Gap Analysis

Security data integration - who wrote about it

An industry cybersecurity data model exists but only for SOC events, not
for appsec modeling

Does DefectDojo have any useful models?

<span acronym-label="aspm" acronym-form="singular+short">aspm</span>
exists but not data oriented and not very customizable

## Requirement Analysis

The goal of this chapter is to conduct a requirement analysis and
produce a structured requirements specification which we will later use
to design the data framework.

### Requirements Methodology

Requirements are gathered through application security domain analysis,
drawing from my personal experience, consultations with my professional
network, and by having researched literature and industry reports in
<a href="#ch:literature-review" data-reference-type="autoref"
data-reference="ch:literature-review">[ch:literature-review]</a>.

This thesis adopts a test-bound approach to requirements traceability.
Rather than maintaining disconnected requirement documents that are
prone to becoming stale, implementation status is derived directly from
test execution results.

#### Specification Format

Each requirement is assigned a unique identifier following the pattern
`REQ-AREA-NNN`, where:

- `AREA` indicates the functional domain (ING for ingestion, PROC for
  processing, SRV for serving)

- `NNN` is a sequential number within that domain

#### Requirement Prioritization

Requirements are documented with priority using the MoSCoW method (Must
Have, Should Have, Could Have, Won’t Have).

#### Test-to-Requirement Linking

The framework employs two complementary verification mechanisms aligned
with Databricks development patterns.

##### Unit and Integration Tests

Python modules containing connector logic and transformation functions
are tested using pytest with custom requirement markers.
<a href="#code:req-marker" data-reference-type="autoref"
data-reference="code:req-marker">[code:req-marker]</a> demonstrates how
tests reference requirement IDs.

<div class="code">

PythonRequirement Marker Examplecode:req-marker
@pytest.mark.requirement("REQ-ING-002") def test_sonarqube_pagination():
"""Validate pagination handling for large result sets.""" ...

</div>

##### Data Quality Expectations

Data quality requirements are verified using Delta Live Tables
expectations, which execute during pipeline runs.
<a href="#code:dlt-expectation" data-reference-type="autoref"
data-reference="code:dlt-expectation">[code:dlt-expectation]</a> shows
how expectations map to requirements via code comments.

<div class="code">

PythonDLT Expectation Examplecode:dlt-expectation @dlt.table
@dlt.expect_or_fail("valid_severity", "severity IN (’critical’, ’high’,
’medium’, ’low’)") @dlt.expect("has_finding_id", "finding_id IS NOT
NULL") def silver_findings(): \# REQ-NFR-001: Data Quality Validation
return transform_findings(dlt.read("bronze_raw"))

</div>

Expectation results are captured in the pipeline event log and reflected
in requirement status.

#### Traceability Generation

A generator script produces the traceability matrix by:

1.  Scanning test files for `@pytest.mark.requirement` markers

2.  Parsing DLT pipeline code for expectation comments referencing
    requirement IDs

3.  Collecting pytest results and DLT pipeline event logs

4.  Merging with requirement descriptions from specification

Appsec vendors, products and their capabilities, APIs and their
maturity/completeness

Capture data formats and integration patterns of the tools

### Personas

#### Application Owners

#### Application Developers

#### Security Experts

Architects and Engineers assigned to application teams

Including security compliance / auditors

#### Development and Security Leadership

Dashboards, metrics, trends, quantified risk

### Data Sources

#### Application Inventory

Start with looking at things from a business application perspective

Business application inventory + business impact assessment

source systems:

#### Tools for Software Development and Delivery

important data sources for inventory

start with SCM and issue tracking tools

Github, Gitlab, Bitbucket, Azure DevOps

Jira, Azure DevOps, Github and Gitlab issues

CI/CD pipelines - Jenkins, Github Actions, Azure DevOps

#### Runtime Infrastructure Platforms and Security Tools

We need infra portrayed from app angle - what does the app run on, how
is it secure, whats the security context

AWS - EC2, serverless Azure GCP

Also how secure is it (infra VMDR like Qualys, Wiz...) can impact risk
of app vulns if they run on vulnerable infra too

How to get data from Kubernetes, Docker even if on prem

#### Security Testing Tools

Primary vulnerability discovery tools (secret scanning, , , ...)

##### Secret Scanning Tools

##### Static Application Security Testing (SAST) Tools

<span acronym-label="sast" acronym-form="singular+short">sast</span>

##### Software Composition Analysis (SCA) Tools

<span acronym-label="sca" acronym-form="singular+short">sca</span>

##### Dynamic Application Security Testing (DAST) Tools

<span acronym-label="dast" acronym-form="singular+short">dast</span>

##### Penetration Testing

Need a way to upload manual findings, e.g. PDF report from external
pentesters

### Data Transformations

#### Data Ingestion and Validation

Filtering?

#### Data Normalization

Standard format for each object and finding type

#### Finding Deduplication

When 2 tools find the same thing, link it, don’t create 2 issues

#### Business Application Mapping

#### Triage

### Data Consumers

#### Remediation Tracking Systems

Jira, ServiceNow

#### Application Security Posture Management (ASPM)

Can pull from data platform already cleaned data instead of from each
source separately

#### SOAR and SIEM

### Non-Functional Requirements

#### Data Quality

Data validations and transformations on input are critical

#### Extensibility

Important feature of the whole framework, especially on data source
integrations and ML models

#### Scalability

it’s intended for large enterprises, 10k’s of repos +

#### Performance

Some use cases require low latency

#### Security

Obviously, with this use case

#### Maintainability

SaaS preferred over manual maintenance - Databricks is ideal

All source code versioned in git and following best practices

### Requirement Specification

#### Data Ingestion

#### Data Processing

#### Data Serving

#### Non-Functional Requirements

## Solution Architecture

generic concepts and open industry standards instead of proprietary
concepts/technology unless necessary

Needs to support both OLTP/OLAP use cases on data serving tier

### Architecture Context

It will be used to pull data from data sources (those are naturally out
of scope)

It needs to be ready to support an application security management
dashboard with a combination of OLTP and OLAP use cases (dashboard
application also out of scope).

### Architecture Principles and Constraints

### Technology Selection

What I’m choosing and why, what were the alternatives and reasons not to
choose them

#### Data Engineering Platform

Choosing **Databricks** over Snowflake, Fabric, BigQuery

Contains a strong data governance framework - **Unity Catalog**, good
for security non-functional requirement

#### Pipeline Framework

I will use <span acronym-label="dltables"
acronym-form="singular+short">dltables</span>, a "data engineering
pipeline framework running on top of Delta Lake that combines
incremental ingestion, streamlined ETL, and automated data quality
processes such as expectations" .

The advantages of <span acronym-label="dltables"
acronym-form="singular+short">dltables</span> are...

#### Connectors

(general plan, more details in Integration Architecture)

dlt, Fivetran?, Databricks Partners?

<span acronym-label="dltool" acronym-form="singular+short">dltool</span>
is utilized to ingest data from security tools into the Bronze layer.
Source code <a href="#code:github-connector" data-reference-type="ref"
data-reference="code:github-connector">[code:github-connector]</a> shows
an example implementation of a connector for GitHub security data.

<div class="code">

PythonGitHub Security Connector Implementationcode:github-connector
import dlt from dlt.sources.helpers.rest_client import paginate

@dlt.source def github_security_source(org: str, token: str): """Extract
security data from GitHub organization."""

@dlt.resource(write_disposition="merge", primary_key="id") def repos():
"""Repository inventory""" yield from paginate(f"/orgs/org/repos")

@dlt.resource(write_disposition="merge", primary_key="number") def
code_scanning_alerts(): """GitHub Code Scanning (SAST) alerts""" yield
from paginate(f"/orgs/org/code-scanning/alerts")

@dlt.resource(write_disposition="merge", primary_key="number") def
dependabot_alerts(): """Dependabot (SCA) vulnerability alerts""" yield
from paginate(f"/orgs/org/dependabot/alerts")

return repos, code_scanning_alerts, dependabot_alerts

</div>

Unity Catalog

Delta Lake

Python vs Scala vs SQL

### High-Level Solution Architecture

### Component Design

See Figure <a href="#fig:component-design" data-reference-type="ref"
data-reference="fig:component-design">3.1</a>

<figure id="fig:component-design">

<figcaption>Component Design</figcaption>
</figure>

#### Data Ingestion Tier

The various connectors

#### Data Processing Tier

##### Pipeline Architecture

Medallion architecture, see
Chapter <a href="#ch:design" data-reference-type="ref"
data-reference="ch:design">4</a>

<span acronym-label="dltables"
acronym-form="singular+short">dltables</span> for defining
transformations

##### Pipeline Orchestration

Databricks Workflows, don’t think my workflows will be complex enough to
use Airflow DAGs

#### Data Serving Tier

Lakebase

### Integration Architecture

#### Connector Strategy

Different patterns and tools optimal for different data sources

As a service: Fivetran if it satisfies requirements (easiest to do, no
need to reinvent the wheel)

Reuse existing: e.g. from DefectDojo
https://github.com/DefectDojo/django-DefectDojo/tree/master/dojo/tools

Databricks Partner

dlt as default tool for custom connectors to REST APIs

##### Application Inventory

##### ServiceNow CMDB

Call ServiceNow API vs build ServiceNow app

##### 

### Extensibility Architecture

Add new integrations via API

### Security Architecture

## Pipeline and Model Design

### Pipeline Overview

Each medallion layer is implemented as a schema within a single Unity
Catalog.

<figure id="fig:medallion-design">

<figcaption>Medallion Layer Design</figcaption>
</figure>

### Bronze Layer

#### Transformations

Data source request filtering / configuration

Ingestion

#### Schema

by systems

### Silver Layer

#### Transformations

Data Quality

Error handling

Normalization

Deduplication

#### Schema

Vendor-agnostic, unified for each entity and finding

##### Entities

Implemented as dimensions

##### Findings

Implemented as facts?

##### Relationships

(entity-to-entity, finding-to-entity)

### Gold Layer

#### Transformations

##### ML Enrichment

Risk scoring

Triage

#### Schema

##### Aggregations

Metrics, counts, summaries...

Sliced by severity, app, owner, team, etc (requirement of grouping)

SLAs, trends, MTTR - what matters to stakeholders per stakeholder
analysis

##### Read-Optimized Views

For dashboard queries, materialized, cached

## Implementation

### Environment Setup

Databricks on AWS

Workspace config

Users, grouips, catalogs, schemas

### Connector Implementation

Which connector which pattern and technology

Whats the rate limiting on each? This is big data potentially

Authentication, pagination etc, dont forget to mention

### Pipeline Implementation

### Pipeline Orchestration

### Data Serving

### Testing and Validation

## Conclusion

This thesis presented a data integration framework for enterprise
application security...

### Thesis Outcomes and Contributions

Evaluation against objectives from Introduction

Which requirements from Ch2 were met / partially met / not met

What did I deliver extra - ML models beyond requirements?

### Limitations

What was not scoped / validated, constraints (license fees for
commercial tools that don’t give free dev trials)

What was difficult about implementing the design? What could not be
implemented in the technology that I selected?

### Future Work

More data sources / connectors, based on my provided blueprint

ML model improvements and fine-tuning

Potentials as an open source project

# Appendices

## Generative AI Use Disclosure

This appendix contains disclosures on all usage of generative AI tools
for this thesis.

### Text Content

All textual content in this thesis was drafted and written exclusively
by the author in **Overleaf Online LaTex editor** with logged history of
incremental manual edits.

For language revision, Overleaf embedded **AI Assist tool** with
**OpenAI GPT** language model was used with following custom prompt:

```
Article usage rules:
- Omit "the" before: plural nouns used generally, abstract concepts, technology names, proper nouns, section references
- Omit "a/an" when: introducing concepts already understood from context, in technical definitions, after "using/via/through"
- Keep articles only when: specific instance is referenced, first introduction of a countable noun, or omission creates ambiguity
- Examples of preferred style:
  - "Bronze layer stores raw data" (not "The Bronze layer stores the raw data")
  - "Figure 3 shows architecture" (not "Figure 3 shows the architecture")
  - "Data flows through pipeline" (not "The data flows through the pipeline")
```

### Diagrams and Figures

All `TikZ` diagrams were generated by Anthropic **Claude Opus 4.5**
model through iterative prompting. The author provided specifications,
reviewed outputs, and iterated until the outcome met structural and
visual requirements.

An example prompt for
Figure <a href="#fig:component-design" data-reference-type="ref"
data-reference="fig:component-design">3.1</a>:

```
Create a TikZ pipeline architecture diagram with vertical flow:

Components:
1. Data Sources row: GitHub, SonarQube, Snyk, NVD, ...
2. External Fivetran box (outside Databricks boundary)
3. Ingestion tier: Fivetran Connector, dlt Connectors, Custom APIs
4. Processing tier: Bronze, Silver, Gold layers (colored)
5. Serving tier: Lakebase, REST API
6. Data Consumers row: Jira, ASPM, SIEM

Wrap Ingestion/Processing/Serving in Databricks Platform boundary.
Use arrows showing data flow between tiers.
Style: Soft colors, rounded corners, compact layout.
```

### Source Code

Implementation code was written by the author with assistance from:

- **Claude Code** (Anthropic) with Opus 4.5 model for code generation,
  review, and debugging.

- **Databricks AI Assistant** for in-editor code debugging and SQL
  optimization.

All generated code was reviewed, tested, and modified by the author
before inclusion.

### Requirements Specification

Requirements in
Chapter <a href="#ch:requirements" data-reference-type="ref"
data-reference="ch:requirements">[ch:requirements]</a> follow a
test-centric traceability approach. Tests reference requirement IDs via
pytest markers, and a generator script produces the traceability matrix
by scanning test results. Implementation status is derived from test
execution rather than manual tracking.
