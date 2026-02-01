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
    - [Application Security Literature](#application-security-literature)
      - [Code Security](#code-security)
      - [Software Supply Chain Security](#software-supply-chain-security)
      - [Software Lifecycle Security](#software-lifecycle-security)
      - [Application Penetration Testing](#application-penetration-testing)
      - [Application Security Data Standards](#application-security-data-standards)
    - [Data Modeling and Engineering Literature](#data-modeling-and-engineering-literature)
      - [Data Architecture](#data-architecture)
      - [Data Modeling and Pipelines](#data-modeling-and-pipelines)
    - [Related Work and Gap Analysis](#related-work-and-gap-analysis)
  - [Requirement Analysis and Specification](#requirement-analysis-and-specification)
    - [Personas](#personas)
      - [Application Owners](#application-owners)
      - [Application Developers](#application-developers)
      - [Security Experts](#security-experts)
      - [Development and Security Leadership](#development-and-security-leadership)
    - [Data Sources](#data-sources)
      - [Tools for Software Development and Delivery](#tools-for-software-development-and-delivery)
      - [Runtime Infrastructure Platforms and Security Tools](#runtime-infrastructure-platforms-and-security-tools)
      - [Application Inventory](#application-inventory)
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
    - [Requirement Prioritization](#requirement-prioritization)
  - [Architecture](#architecture)
    - [Architecture Context](#architecture-context)
    - [Architecture Principles and Constraints](#architecture-principles-and-constraints)
    - [Technology Selection](#technology-selection)
    - [High-Level Solution Architecture](#high-level-solution-architecture)
    - [Component Design](#component-design)
      - [Data Ingestion Tier](#data-ingestion-tier)
      - [Data Processing Tier](#data-processing-tier)
        - [Pipeline Architecture](#pipeline-architecture)
        - [Pipeline Orchestration](#pipeline-orchestration)
      - [Data Serving Tier](#data-serving-tier)
    - [Integration Architecture](#integration-architecture)
      - [Connector Strategy](#connector-strategy)
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
    - [Data Serving](#data-serving)
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

MASTER THESIS

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

My sincere thanks go to Ing. Aleš Kotuč for his guidance and valuable
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
three distinct contributions: (1) a requirement specification for an
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

Why I chose this topic:

- my appsec experience, what I see as a problem + back it up with some
  research

- explain that fundamentally, ASPM+VMDR are data problems, and having
  control over the data layer makes sense

- security vendor agnostic solution doesn’t exist (there’s DefectDojo
  but it’s "just" a Django web app without proper data architecture,
  limited scaling abilities, no data pull capability, need to push with
  custom integration or upload results manually - DefectDojo Pro
  required for that)

### Objective

Main goal: design and implement the model and pipeline (needs to be
precisely formulated)

Subgoals:

- Summarize existing literature in ch1

- Analyze appsec domain, expectations from the framework, produce a
  requirements specification in ch2 and include full spec in App A

- In ch3, propose a reusable and extensible framework, domain driven
  design (name things as they are in appsec world), accommodating both
  OLTP and OLAP requirements, streaming for time critical use cases?

- Validate output of ch3 build a reference implementation of the
  framework in Databricks using Claude Code and Databricks AI Assistant

- Evaluate whether feasible/usable as a product + possible future
  improvements

### Methodology

Methodology + outline hypotheses?

- First a quick review of existing literature and resources - include
  vendor documentation as it will need to be referenced later

- Requirement analysis - document req’s for an appsec integration
  framework, what it should have

- Design, implement, evaluate the framework

Outline main results/outcomes of the thesis: business impact is that
security teams can self-service deploy their data and ML pipeline and
not rely on vendors’ proprietary data design

### Structure

## Literature Review

### Software Development Literature

What process/activities are we securing with appsec?

Books like Code Complete, Clean Code, Pragmatic Programmer...

#### Source Code Management

git book, software engineering at Google, ...

#### Software Development Lifecycle

Traditional vs devops and CI/CD pipelines, list books on each

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

#### Application Security Data Standards

Standard data formats for vulnerabilities like <span acronym-label="cve"
acronym-form="singular+short">cve</span>

SARIF, CycloneDX, OCSF

Citing test , ,

<span acronym-label="aspm" acronym-form="singular+short">aspm</span>
mentioned for the first time, <span acronym-label="aspm"
acronym-form="singular+short">aspm</span> mentioned second time.

<span acronym-label="api" acronym-form="singular+short">api</span>

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

## Requirement Analysis and Specification

The goal of this chapter is to produce a requirements specification
which we will later use to...

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

#### Application Inventory

Start with looking at things from a business application perspective

Business application inventory + business impact assessment

source systems: Primary vulnerability discovery tools (secret scanning,
, , ...)

#### Security Testing Tools

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

Important feature of the whole framework

#### Scalability

it’s intended for large enterprises, 10k’s of repos +

#### Performance

Some use cases require low latency

#### Security

Obviously, with this use case

#### Maintainability

SaaS preferred over manual maintenance - Databricks is ideal

All source code versioned in git and following best practices

### Requirement Prioritization

MoSCoW method

## Architecture

generic concepts and open industry standards instead of proprietary
concepts/technology unless necessary

Needs to support both OLTP/OLAP use cases based on requirements

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

I will use <span acronym-label="dltables"
acronym-form="singular+short">dltables</span>, a data engineering
pipeline framework running on top of Delta Lake that combines
incremental ingestion, streamlined ETL, and automated data quality
processes such as expectations . The advantage of
<span acronym-label="dltables"
acronym-form="singular+short">dltables</span> is...

Connectors - dlt, Fivetran?, Databricks Partners?

I use <span acronym-label="dltool"
acronym-form="singular+short">dltool</span> to ingest data from security
tools into the Bronze layer. The code snippet
<a href="#code:github-connector" data-reference-type="ref"
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

Databricks

Unity Catalog

Delta Lake

Python vs Scala vs SQL

### High-Level Solution Architecture

### Component Design

<figure id="fig:pipeline-architecture">

<figcaption>Pipeline Architecture</figcaption>
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
by the author in `Overleaf Online LaTex editor` with logged history of
incremental manual edits. For language revision, Overleaf AI Assist tool
with OpenAI GPT language model was used and customized with following
prompt:

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

All `TikZ` diagrams were generated by Claude Opus 4.5 (Anthropic)
through iterative prompting. The author provided structural
specifications, reviewed outputs, and requested modifications until
diagrams accurately represented the intended architecture. An example
prompt for
Figure <a href="#fig:pipeline-architecture" data-reference-type="ref"
data-reference="fig:pipeline-architecture">3.1</a>:

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
  review, and debugging. Custom skills installed: `vkraus/superpowers`
  fork with embedded BDD skill and Databricks development skill.

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
