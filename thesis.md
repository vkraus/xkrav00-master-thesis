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
- [Software Development](#software-development)
  - [Software Engineering](#software-engineering)
  - [Source Code Management](#source-code-management)
  - [Software Development Lifecycle](#software-development-lifecycle)
- [Application Security](#application-security)
  - [Code Security](#code-security)
  - [Software Supply Chain Security](#software-supply-chain-security)
  - [Software Lifecycle Security](#software-lifecycle-security)
  - [Application Penetration Testing](#application-penetration-testing)
  - [DevSecOps](#devsecops)
  - [Application Security Data Standards](#application-security-data-standards)
- [Data Modeling and Engineering](#data-modeling-and-engineering)
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

This thesis follows a design-science research methodology as presented
by , structured into three phases.

In the first phase, I conduct a **literature review** of academic and
industry sources across three domains: software development, application
security, and data engineering. This review establishes the theoretical
foundation for the framework and includes vendor documentation for the
technologies used in the implementation.

In the second phase, I perform a **requirements analysis and design**. I
analyze the application security landscape to identify the key personas,
data sources, required transformations, and non-functional requirements.
Requirements are prioritized using the MoSCoW method. Based on the
requirements, I propose an architecture and design a data model with a
medallion-based pipeline.

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

<a href="#ch:literature-review" data-reference-type="autoref"
data-reference="ch:literature-review">[ch:literature-review]</a> of the
thesis researches relevant literature on software development,
application security, and data engineering, and identifies the research
gap. <a href="#ch:requirement-analysis" data-reference-type="autoref"
data-reference="ch:requirement-analysis">[ch:requirement-analysis]</a>
defines the personas, data sources, transformations, consumers, and
non-functional requirements, organized in a coherent requirements
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

This chapter presents the literature across three domains fundamental to
this thesis.
<a href="#sec:sw-dev-literature" data-reference-type="autoref"
data-reference="sec:sw-dev-literature">[sec:sw-dev-literature]</a>
reviews software development practices.
<a href="#sec:appsec-literature" data-reference-type="autoref"
data-reference="sec:appsec-literature">[sec:appsec-literature]</a>
examines security testing approaches, tools, and data standards.
<a href="#sec:data-literature" data-reference-type="autoref"
data-reference="sec:data-literature">[sec:data-literature]</a> covers
data architecture and engineering patterns. Finally,
<a href="#sec:related-work" data-reference-type="autoref"
data-reference="sec:related-work">[sec:related-work]</a> analyzes
related work and identifies the gap this thesis addresses.

### Software Development

Before discussing how to secure software, it is necessary to define what
modern software development entails. This section surveys the literature
on software engineering practices and the <span acronym-label="sdlc"
acronym-form="singular+short">sdlc</span>.

#### Software Engineering

and provide comprehensive treatments of the field, covering requirements
engineering, design, testing, and project management. At a more
theoretical level, collect Parnas’s foundational papers on modularity
and information hiding, while offers a rigorous treatment of programming
language design underpinning modern development tools.

On the practical side, provides guidelines for software construction
covering code quality and collaborative practices, proposed principles
of clean, maintainable code widely adopted in industry, and provided a
broader pragmatic philosophy for professional development. present
practitioner essays on elegant solutions to real-world problems,
illustrating the craft nature of software development. These works agree
that software is built collaboratively from source code, organized in
repositories, and deployed through increasingly automated pipelines.

#### Source Code Management

provides a thorough treatment of Git, covering branching strategies,
merging, and distributed workflows, while offers a more recent, visually
oriented introduction. extend this perspective to organizational scale,
describing how Google manages a monolithic repository with tens of
thousands of contributors. For this thesis, repositories are significant
as the primary unit around which security findings are grouped and
tracked, a relationship central to the data model in
<a href="#ch:design" data-reference-type="autoref"
data-reference="ch:design">[ch:design]</a>.

#### Software Development Lifecycle

<span acronym-label="sdlc" acronym-form="singular+short">sdlc</span>
focused literature documents a shift from sequential "waterfall" models
to iterative methodologies and DevOps practices. present empirical
evidence that high-performing teams deploy more frequently with shorter
lead times, achieved largely via <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> automation. complement this
with practical guidance for implementing DevOps at scale, covering
deployment pipelines and feedback loops. The resulting
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
pipeline—an automated sequence of commit, build, test, and deploy
stages—is directly relevant to this thesis: each stage is an integration
point where security tools produce findings that the proposed framework
consolidates.

### Application Security

This section reviews the literature across the application security
domains relevant to this thesis and concludes with data standards for
representing security findings.

provides broad coverage of security engineering, including threat models
and software security. offer a comprehensive textbook on computer
security principles. introduces software security activities like code
review, architectural risk analysis, or penetration testing that should
be embedded throughout the <span acronym-label="sdlc"
acronym-form="singular+short">sdlc</span>, while complement this with
practical guidelines for defensive coding. addresses threat modeling as
a structured approach to identifying security issues early in design.
The OWASP Top 10  is a widely referenced classification of critical web
application security risks that influences how many tools categorize
their findings.

#### Code Security

<span acronym-label="sast" acronym-form="singular+short">sast</span>
examines source code, bytecode, or binary code for vulnerabilities
without executing the program. provide the foundational treatment of
static analysis for security, covering taint analysis, control flow
analysis, and pattern matching to detect injection flaws, buffer
overflows, and insecure data handling.

In practice, <span acronym-label="sast"
acronym-form="singular+short">sast</span> is implemented by tools such
as SonarQube, Checkmarx, Semgrep, and Fortify, which differ in detection
approaches: rule-based pattern matching, data-flow analysis, or
user-defined custom rules. As noted by , a key challenge is the tradeoff
between false positive rates and detection coverage. From a data
integration perspective, each tool produces findings through different
<span acronym-label="api" acronym-form="plural+short">apis</span> and in
different formats, a fragmentation that motivates the normalization
layer proposed in this thesis.

#### Software Supply Chain Security

<span acronym-label="sca" acronym-form="singular+short">sca</span>
addresses vulnerabilities in third-party dependencies. Modern
applications may include hundreds of transitive dependencies, and
discusses the broader implications of supply chain trust, while provide
a systematic review of open-source supply chain attacks including
typosquatting, dependency confusion, and malicious package injection.

<span acronym-label="sca" acronym-form="singular+short">sca</span> tools
such as Snyk, Dependabot, and Mend analyze dependency manifests and
cross-reference resolved versions against the <span acronym-label="nvd"
acronym-form="singular+short">nvd</span>. Several also generate a
<span acronym-label="sbom" acronym-form="singular+short">sbom</span>, a
structured inventory of all software components, increasingly required
by regulatory frameworks . The <span acronym-label="sbom"
acronym-form="singular+short">sbom</span> concept is formalized through
CycloneDX and <span acronym-label="spdx"
acronym-form="singular+short">spdx</span>, discussed further in
<a href="#sec:data-standards" data-reference-type="autoref"
data-reference="sec:data-standards">[sec:data-standards]</a>.

#### Software Lifecycle Security

The software lifecycle itself introduces security risks. Secret exposure
(credentials, <span acronym-label="api"
acronym-form="singular+short">api</span> keys, and tokens committed to
version control) is detected by tools such as GitLeaks, TruffleHog, and
GitHub Secret Scanning, which scan commit history against known
credential patterns and entropy-based heuristics.

<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
pipeline security is another concern: build systems execute arbitrary
code, deployment pipelines hold production credentials, and artifact
registries distribute compiled software. The SLSA framework  provides
progressively stricter requirements for supply chain security, including
build provenance and artifact integrity. These lifecycle tools produce
findings that differ structurally from code-level vulnerabilities,
adding complexity to data consolidation.

#### Application Penetration Testing

<span acronym-label="dast" acronym-form="singular+short">dast</span> and
manual penetration testing examine running systems for exploitable
vulnerabilities. provide a comprehensive treatment of web application
attack techniques, covering injection, authentication bypass, and
business logic vulnerabilities, illustrating the attacker’s perspective
that informs what security data is most important to capture.

Automated <span acronym-label="dast"
acronym-form="singular+short">dast</span> tools such as OWASP ZAP and
Burp Suite complement <span acronym-label="sast"
acronym-form="singular+short">sast</span> by detecting vulnerabilities
that manifest only at runtime. Manual penetration testing produces
findings in unstructured formats, typically PDF reports, presenting a
distinct integration challenge: while automated tools expose findings
through <span acronym-label="api"
acronym-form="plural+short">apis</span>, manual results must be parsed
or entered manually.

#### DevSecOps

The DevSecOps paradigm  extends DevOps by embedding security into every
phase of the <span acronym-label="sdlc"
acronym-form="singular+short">sdlc</span>, commonly called "shifting
security left", integrating <span acronym-label="sast"
acronym-form="singular+short">sast</span>, <span acronym-label="sca"
acronym-form="singular+short">sca</span>, secret scanning, and
<span acronym-label="dast" acronym-form="singular+short">dast</span>
directly into <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> pipelines .

The practical consequence is a significant increase in both volume and
diversity of security data. An organization may operate dozens of tools
across pipeline stages, each producing findings in different formats and
severity models. anticipated this by advocating for security touchpoints
spanning the entire lifecycle, but the tooling landscape has grown far
beyond what a single touchpoint model can accommodate. This
proliferation of fragmented security data is the core problem motivating
the framework proposed in this thesis.

#### Application Security Data Standards

Several standards bring consistency to how security findings are
identified, scored, and exchanged.

For identification and scoring, the <span acronym-label="cve"
acronym-form="singular+short">cve</span> system  provides a standardized
naming scheme for known vulnerabilities. The <span acronym-label="cvss"
acronym-form="singular+short">cvss</span>  scores severity based on
attack vector, complexity, and impact, while the
<span acronym-label="epss" acronym-form="singular+short">epss</span>
complements it by estimating exploitation probability using
<span acronym-label="ml" acronym-form="singular+short">ml</span> models
trained on historical data .

For findings interchange, <span acronym-label="sarif"
acronym-form="singular+short">sarif</span>  defines a
<span acronym-label="json"
acronym-form="singular+short">json</span>-based format for static
analysis results, supported by several <span acronym-label="sast"
acronym-form="singular+short">sast</span> tools and GitHub. CycloneDX 
and <span acronym-label="spdx"
acronym-form="singular+short">spdx</span>  provide schemas for
<span acronym-label="sbom" acronym-form="plural+short">sboms</span> and
associated vulnerability data. The <span acronym-label="ocsf"
acronym-form="singular+short">ocsf</span>  defines a vendor-agnostic
schema for cybersecurity events, though focused on
<span acronym-label="siem" acronym-form="singular+short">siem</span> and
<span acronym-label="soar" acronym-form="singular+short">soar</span>
rather than application security.

No single format covers the full spectrum of application security data.
<span acronym-label="sarif" acronym-form="singular+short">sarif</span>
addresses static analysis but not <span acronym-label="sca"
acronym-form="singular+short">sca</span> or <span acronym-label="dast"
acronym-form="singular+short">dast</span>. CycloneDX and
<span acronym-label="spdx" acronym-form="singular+short">spdx</span>
focus on composition, not code-level vulnerabilities.
<span acronym-label="ocsf" acronym-form="singular+short">ocsf</span>
targets security operations, not application vulnerability management.
This gap, the absence of a unified data model across all tool
categories, is a central motivation for the data modeling in
<a href="#ch:design" data-reference-type="autoref"
data-reference="ch:design">[ch:design]</a>.

### Data Modeling and Engineering

This section examines data engineering patterns and technologies
suitable for consolidating the security data described in
<a href="#sec:appsec-literature" data-reference-type="autoref"
data-reference="sec:appsec-literature">[sec:appsec-literature]</a>.

#### Data Architecture

The literature documents an evolution from data warehouses through data
lakes to the lakehouse paradigm. provide a comprehensive body of
knowledge for data management, establishing the vocabulary and
principles referenced throughout this section.

established the relational model as the theoretical foundation for data
management. The data warehouse, formalized by , is a subject-oriented,
integrated, time-variant collection of data for analytical
decision-making, using a top-down normalized approach. take a
complementary bottom-up approach with dimensional modeling: star schemas
organizing data into fact and dimension tables optimized for queries.
Both approaches assume structured sources with stable schemas, which
does not hold for heterogeneous security tool output.

The data lake  stores raw data in its native format, deferring schema
definition to consumption (schema-on-read). While this addresses format
diversity, it introduces governance challenges; without proper
management, data lakes risk becoming “data swamps” .

The lakehouse architecture  combines data lake flexibility with
warehouse governance. provide a definitive treatment of Delta Lake, the
storage layer adding ACID transactions, schema enforcement, and time
travel on top of lake storage. offer practical guidance for lakehouse
design at enterprise scale. The lakehouse paradigm suits the application
security problem: it accommodates diverse, semi-structured tool output
while providing governance and query performance for both dashboards and
operational lookups.

#### Data Modeling and Pipelines

remain the primary reference for dimensional modeling: fact tables
capture measurable events, dimension tables provide descriptive context.
Security findings naturally map to facts (each with severity, tool
source, and detection date) while repositories, applications, and teams
serve as dimensions. also discuss Data Vault, which prioritizes
auditability and historical tracking relevant for compliance.

cover data engineering fundamentals, including <span acronym-label="etl"
acronym-form="singular+short">etl</span> versus
<span acronym-label="elt" acronym-form="singular+short">elt</span>
patterns. <span acronym-label="etl"
acronym-form="singular+short">etl</span> transforms data before loading,
requiring upfront schema knowledge. <span acronym-label="elt"
acronym-form="singular+short">elt</span> loads raw data first and
transforms in place, aligning well with lakehouse architectures where
engines such as Apache Spark perform transformations at scale .

The medallion architecture  organizes lakehouse transformations into
three layers:

- **Bronze**: Raw data with minimal transformation, preserving original
  schemas.

- **Silver**: Cleaned, validated, and normalized data conforming to a
  unified schema.

- **Gold**: Consumption-ready aggregated metrics and enriched datasets.

discusses this pattern with Delta Lake and Spark, covering schema
evolution and incremental processing. complement with guidance on
catalog organization and compute optimization at scale. The medallion
architecture is adopted as the core pattern for the pipeline in
<a href="#ch:design" data-reference-type="autoref"
data-reference="ch:design">[ch:design]</a>: bronze ingests raw security
data, silver normalizes it into a vendor-agnostic schema, and gold
produces metrics for stakeholder consumption.

### Related Work and Gap Analysis

This section examines existing approaches to security data consolidation
and identifies the gap this thesis addresses.

**Commercial <span acronym-label="aspm"
acronym-form="singular+short">aspm</span> platforms** such as Apiiro,
Cycode, ArmorCode, and Snyk AppRisk aggregate findings into unified
dashboards with correlation and risk scoring. However, they are
proprietary, operate as black boxes, and create vendor lock-in:
organizations cannot customize pipelines, apply their own
<span acronym-label="ml" acronym-form="singular+short">ml</span> models,
or integrate beyond vendor-supported options.

**DefectDojo**  is the most prominent open-source alternative,
supporting imports from over 150 tools. However, it was designed as a
vulnerability management interface, not a data platform. Its PostgreSQL
backend limits enterprise-scale analytics, and pull-based
<span acronym-label="api" acronym-form="singular+short">api</span>
connectors are available only in the commercial Pro offering.

**Industry data models** such as <span acronym-label="ocsf"
acronym-form="singular+short">ocsf</span>  target security operations
(<span acronym-label="siem" acronym-form="singular+short">siem</span>,
<span acronym-label="soar" acronym-form="singular+short">soar</span>)
and do not model application-level entities such as repositories or
development teams. Cloud-native security data lakes like AWS Security
Lake adopt <span acronym-label="ocsf"
acronym-form="singular+short">ocsf</span> for log aggregation but do not
address application security consolidation.

**Academic literature** on application security consolidation as a data
engineering problem is limited, with most work focusing on detection
techniques rather than integrating findings across heterogeneous tools
at scale.

No existing approach satisfies all requirements. Commercial
<span acronym-label="aspm" acronym-form="singular+short">aspm</span>
platforms are proprietary and inflexible. DefectDojo lacks a data-first
architecture for enterprise analytics. <span acronym-label="ocsf"
acronym-form="singular+short">ocsf</span> targets security operations
rather than application security. This thesis fills the gap with an
open, vendor-agnostic framework that treats application security
consolidation as a data engineering problem.

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

The framework serves several distinct stakeholder groups, each with
different data needs and expectations. Understanding these personas is
essential for deriving the requirements that the framework must satisfy.
The following subsections characterize the four primary persona
categories whose needs shape the framework.

#### Application Owners

Application owners are business stakeholders responsible for the overall
risk posture of one or more applications within the enterprise
portfolio. They need aggregated security posture visibility, including
trend data over time and composite risk metrics that communicate the
security state of their applications at a glance. Rather than examining
individual findings, application owners interact with dashboards that
present overall health indicators, remediation progress, and compliance
status. Their need for technical detail is limited; they require
information in the form of actionable business terms. These needs
directly drive the framework’s aggregation and serving layer
requirements, particularly the computation of application-level risk
scores and trend visualizations.

#### Application Developers

Application developers are the engineers who, in the context of our
framework, receive security findings and are responsible for their
remediation. They need clear, actionable vulnerability information
enriched with code-level context such as the affected file, line number,
and remediation guidance. Developers have a low tolerance for false
positives and duplicated noise, as excessive or inaccurate findings
erode trust in the security tooling and reduce remediation flow.
Findings must be presented in a format that integrates naturally into
their existing workflows, whether through issue trackers or
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
pipeline feedback. These needs drive the framework’s normalization,
de-duplication, and data quality requirements, ensuring that only
validated, contextually enriched findings reach developers.

#### Security Experts

Security experts are the security architects and security engineers who
support application teams, auditors responsible for assessing security
compliance on application level, or security analysts seeking context
for a security event or incident. They require access to detailed
findings, complete audit trails, and the ability to drill down into raw
data when performing triage or validating tool output. Security
engineers define and maintain security policies, evaluate tool
effectiveness, and coordinate remediation priorities across teams.
Compliance auditors, a closely related sub-group, need evidence of
security requirement coverage, remediation timelines, and historical
records that demonstrate adherence to organizational and regulatory
standards. These needs drive the framework’s data quality, governance,
and granular access control requirements, as well as the preservation of
full data lineage from source to consumption.

#### Development and Security Leadership

Development and security leadership, including
<span acronym-label="ciso" acronym-form="plural+short">cisos</span>,
engineering managers, and vice presidents, require quantified risk
metrics to inform strategic decisions and resource allocation. Key
indicators include <span acronym-label="mttr"
acronym-form="singular+short">mttr</span>, <span acronym-label="sla"
acronym-form="singular+short">sla</span> compliance rates, vulnerability
density trends, and team-level or portfolio-level comparisons that
reveal where remediation investment is most needed. These stakeholders
consume information through executive dashboards designed for rapid
interpretation rather than detailed investigation. Their decisions
directly affect staffing, tooling budgets, and organizational security
strategy. These needs drive the framework’s gold-layer aggregation and
metric computation requirements, demanding reliable, well-governed data
pipelines that produce trustworthy summary metrics.

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

<span id="ch:conclusion" label="ch:conclusion"></span>

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
