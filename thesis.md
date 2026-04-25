<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
## Table of Contents

- [Declaration on the Use of Artificial Intelligence](#declaration-on-the-use-of-artificial-intelligence)
- [Acknowledgements](#acknowledgements)
- [Abstract](#abstract)
  - [Keywords](#keywords)
  - [Introduction](#introduction)
- [Motivation](#motivation)
- [Objective](#objective)
- [Methodology](#methodology)
- [Structure](#structure)
- [External Documentation Site](#external-documentation-site)
  - [Analysis](#analysis)
- [Asset Discovery and Inventory](#asset-discovery-and-inventory)
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
- [Static Application Security](#static-application-security)
  - [Static Application Security Testing](#static-application-security-testing)
  - [Software Composition Analysis](#software-composition-analysis)
  - [Secret Detection](#secret-detection)
- [Dynamic Application Security Testing](#dynamic-application-security-testing)
  - [Dynamic Application Security Testing](#dynamic-application-security-testing-1)
- [Runtime Security](#runtime-security)
  - [Web Application Firewalls](#web-application-firewalls)
  - [Source Integration Summary](#source-integration-summary)
- [Data Engineering](#data-engineering)
  - [Data Platform Architecture](#data-platform-architecture)
  - [Data Integration Patterns](#data-integration-patterns)
  - [Domain Data Model](#domain-data-model)
- [Related Work and Gap Analysis](#related-work-and-gap-analysis)
  - [Existing Approaches](#existing-approaches)
  - [Databricks Lakewatch](#databricks-lakewatch)
  - [Comparative Analysis and Research Gap](#comparative-analysis-and-research-gap)
- [Selected Sources](#selected-sources)
  - [Selection Criteria](#selection-criteria)
  - [The Selected Nine](#the-selected-nine)
  - [Considered and Excluded](#considered-and-excluded)
  - [Cross Source Synthesis](#cross-source-synthesis)
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
  - [Source Synthesis](#source-synthesis)
  - [Schema Patterns](#schema-patterns)
        - [Bronze pattern](#bronze-pattern)
        - [Silver entity pattern](#silver-entity-pattern)
        - [Quarantine scope](#quarantine-scope)
        - [CMDB relationship resolution](#cmdb-relationship-resolution)
        - [Silver finding pattern](#silver-finding-pattern)
        - [Deduplication pattern](#deduplication-pattern)
        - [Relationship pattern](#relationship-pattern)
        - [Gold aggregation pattern](#gold-aggregation-pattern)
  - [Entity Model](#entity-model)
        - [Entity Tables](#entity-tables)
        - [Finding Table](#finding-table)
        - [Reference Tables](#reference-tables)
        - [Relationship Tables](#relationship-tables)
        - [Reference Implementation Scope](#reference-implementation-scope)
  - [Aggregation Model](#aggregation-model)
        - [Application risk scores](#application-risk-scores)
        - [Team metrics](#team-metrics)
        - [Vulnerability trends](#vulnerability-trends)
        - [Coverage analysis](#coverage-analysis)
        - [Extension guide](#extension-guide)
- [Environment and Deployment](#environment-and-deployment)
  - [Deployment Strategy](#deployment-strategy)
  - [Project Structure](#project-structure)
  - [Pipeline Orchestration](#pipeline-orchestration)
  - [Monitoring and Observability](#monitoring-and-observability)
  - [Testing and Validation](#testing-and-validation)
- [Connector Framework](#connector-framework)
  - [Connector Abstraction](#connector-abstraction)
        - [Connector Categories](#connector-categories)
        - [Cross cutting concerns](#cross-cutting-concerns)
        - [Connector Contract](#connector-contract)
        - [Connector Artifacts](#connector-artifacts)
  - [Ingestion Patterns](#ingestion-patterns)
        - [Common landing pattern](#common-landing-pattern)
        - [Bronze table template](#bronze-table-template)
        - [Connector job template](#connector-job-template)
        - [Category specific considerations](#category-specific-considerations)
  - [Transformation Patterns](#transformation-patterns)
        - [Schema mapping](#schema-mapping)
        - [Normalization](#normalization)
        - [Data quality validation](#data-quality-validation)
        - [Deduplication application](#deduplication-application)
        - [Business context attribution](#business-context-attribution)
  - [Testing and Validation](#testing-and-validation-1)
- [Analytics and Serving Framework](#analytics-and-serving-framework)
  - [Analytics Patterns](#analytics-patterns)
        - [Extension blueprint](#extension-blueprint)
        - [Rule Based Analytics](#rule-based-analytics)
        - [ML Driven Analytics](#ml-driven-analytics)
  - [Serving Patterns](#serving-patterns)
        - [Analytical serving](#analytical-serving)
        - [Operational serving](#operational-serving)
        - [Event driven serving](#event-driven-serving)
  - [Testing and Validation](#testing-and-validation-2)
- [A Note on Extension and AI Assistance](#a-note-on-extension-and-ai-assistance)
  - [MVP Implementation](#mvp-implementation)
- [Methodology](#methodology-1)
- [Project Structure](#project-structure-1)
- [Ingestion Category Assignment](#ingestion-category-assignment)
- [Representative Connectors](#representative-connectors)
  - [ServiceNow: Lakeflow Connect Pipeline](#servicenow-lakeflow-connect-pipeline)
  - [GitHub: PyGitHub SDK Module](#github-pygithub-sdk-module)
- [Aggregate Results](#aggregate-results)
- [Discussion](#discussion)
  - [Contract of three categories](#contract-of-three-categories)
  - [Declarative mapping](#declarative-mapping)
  - [Unsanctioned category failure mode](#unsanctioned-category-failure-mode)
  - [Iteration Summary](#iteration-summary)
  - [Conclusion](#conclusion)
- [Thesis Outcomes and Contributions](#thesis-outcomes-and-contributions)
- [Evaluation of the AI Instantiability Claim](#evaluation-of-the-ai-instantiability-claim)
  - [Acceptance rubric](#acceptance-rubric)
  - [Empirical outcome](#empirical-outcome)
  - [Claim defended](#claim-defended)
  - [Provenance](#provenance)
- [Limitations](#limitations)
- [Future Work](#future-work)
- [Appendices](#appendices)
  - [Generative AI Use Disclosure](#generative-ai-use-disclosure)
- [Grammar and Language Style](#grammar-and-language-style)
- [Images and Other Media](#images-and-other-media)
- [Product Documentation (`docs.zip`)](#product-documentation-docszip)
- [Source Code (`mvp.zip`)](#source-code-mvpzip)
- [Supporting Tooling](#supporting-tooling)

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

### Declaration on the Use of Artificial Intelligence

I confirm that artificial intelligence tools were used in the
preparation of the submitted work. Specifically, they were used in the
following ways:

- improvement of grammar, language style, and conciseness of the thesis,
  including review passes that shortened the manuscript by rephrasing
  longer prose and relocating detail into the attached product
  documentation,

- generation of images and other media in the thesis,

- generation of product documentation attached to the thesis
  (`docs.zip`),

- generation of source code attached to the thesis (`mvp.zip`),

- assistance with supporting tooling not submitted with the thesis, such
  as LaTeX build and continuous integration configuration and prose
  migration scripts.

=1.5em Each use of any of the above methods is separately documented in
an appendix to the thesis, which provides a more detailed explanation of
which tool was used in which specific part of the work; the author’s own
contribution is highlighted.

I confirm that:

- my work is original and was prepared in accordance with ethical
  standards, in particular the Code of Ethics of the Prague University
  of Economics and Business; that all information sources used are
  properly cited in the work; and that any generated content has been
  verified by me;

- I accept full responsibility for the entire content of the thesis.

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

To protect business critical applications, security teams rely on a
large variety of tools: <span acronym-label="sast"
acronym-form="singular+short">sast</span> scanners analyze source code,
<span acronym-label="sca" acronym-form="singular+short">sca</span> tools
check software dependencies, <span acronym-label="dast"
acronym-form="singular+short">dast</span> probes running applications,
and secret scanners flag exposed credentials in code .

Further detection runs against build and deployment pipelines, which
face their own classes of threats such as malicious dependencies
published to public package registries, compromised build agents
injecting code into release artifacts, tampered container base images,
or leaked <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> credentials used to push
unauthorized changes . Security teams also deploy
<span acronym-label="ide" acronym-form="singular+short">ide</span>
plugins and security context tools integrated into
<span acronym-label="ai" acronym-form="singular+short">ai</span> coding
assistants such as Claude Code or GitHub Copilot to catch problems
before code reaches version control .

In large enterprises, dozens of such tools produce findings through
different data formats and integration patterns . As application
security architect in a large organization with thousands of developers
and tens of thousands of repositories, I have seen firsthand how hard
this environment is to secure. Two classes of difficulty dominate.

The first is **detection heterogeneity**. Tools in the same category
scan differently and produce different results, so a single tool is
rarely sufficient . Running multiple tools in parallel improves coverage
but creates the opposite problem: the same vulnerability is reported
several times, and findings must be deduplicated before they can be
triaged or counted .

The second is **data consolidation**. Findings lack the business context
needed for prioritization: the owning application, its criticality tier,
and its regulatory scope live in a separate <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span>, not in the security tool .
Correlation within the findings themselves is nontrivial:
<span acronym-label="sast" acronym-form="singular+short">sast</span>
results point to a repository, file, and line, while
<span acronym-label="dast" acronym-form="singular+short">dast</span>
results point to a <span acronym-label="url"
acronym-form="singular+short">url</span> or host, so cross tool
correlation requires additional deployment and inventory metadata .
Integration patterns compound the problem. Push based models, where
scanners upload reports into a vulnerability management interface,
fragment data and do not scale across dozens of tools, and robust pull
based <span acronym-label="api" acronym-form="singular+short">api</span>
connectors, where they exist, are usually gated behind commercial
tiers .

Consolidating application security data is a data engineering problem.
Industry addresses it with commercial <span acronym-label="aspm"
acronym-form="singular+short">aspm</span> products offering dashboards
and aggregated views , but these are proprietary and inflexible. They
create vendor lockin and prevent security teams from customizing
pipelines, applying their own <span acronym-label="ml"
acronym-form="singular+short">ml</span> models, or integrating with
internal systems.

The most notable open source alternative, DefectDojo, is a Django based
vulnerability management web application , not a data first platform.
Its relational backend limits scale, and ingestion relies mostly on push
based integrations or manual uploads. Pull based
<span acronym-label="api" acronym-form="singular+short">api</span>
connectors exist only in the commercial DefectDojo Pro tier.

Databricks Lakewatch, announced in March 2026, is a lakehouse native
<span acronym-label="siem" acronym-form="singular+short">siem</span> .
It runs on the same lakehouse platform this thesis adopts but addresses
a different domain: runtime threat detection, alert triage, and log
analytics, not application security posture. The distinction is
discussed in <a href="#sec:lakewatch" data-reference-type="autoref"
data-reference="sec:lakewatch">[sec:lakewatch]</a>.

What is missing is a vendor agnostic framework that approaches
application security as a data engineering problem, providing a reusable
architecture for ingestion, normalization, deduplication, and serving at
enterprise scale. The pace of tool adoption outstrips the engineering
effort available to write connectors for each one. A framework that
encodes integration logic declaratively, as schemas, a connector
contract, and a catalog of skills an <span acronym-label="ai"
acronym-form="singular+short">ai</span> coding agent can execute,
**should reduce onboarding a new source to a four step procedure**
(<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a>) rather
than a pipeline redesign, with the cost per source bounded by the cost
of invoking the skill catalog under supervision.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> and
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> examine how far this
reduction holds under the empirical methodology actually exercised.

This raises the central research question: **how can heterogeneous
enterprise application security findings be consolidated into a unified,
vendor agnostic data platform that serves the analytical and operational
needs of security teams?**

### Objective

The main goal is to specify, design, and implement a data integration
framework for enterprise application security that consolidates findings
from tools into a unified platform, enabling consistent normalization,
deduplication, triage, and correlation across business applications.

The subgoals are:

1.  **Analysis** (<a href="#ch:analysis" data-reference-type="autoref"
    data-reference="ch:analysis">[ch:analysis]</a>): Survey the
    application security domain and its adjacent data sources.
    Characterize asset inventories, software development platforms,
    static and dynamic security tooling, and the relevant data
    engineering patterns. Review related work, identify the research
    gap, and select source systems to carry forward. The
    <span acronym-label="api" acronym-form="singular+short">api</span>
    analysis per source grounding these findings is collected on the
    external [documentation
    site](https://vkraus.github.io/appsec-docs/).

2.  **Framework** (<a href="#ch:framework" data-reference-type="autoref"
    data-reference="ch:framework">[ch:framework]</a>): Formalize the
    requirements specification and propose a reusable blueprint covering
    solution architecture, a medallion based data model (bronze, silver,
    gold) , a connector framework, and an analytics and serving
    framework. The blueprint targets the Databricks lakehouse  while
    separating general patterns from platform specific choices. The
    technology rationale is given
    in <a href="#sec:tech-stack" data-reference-type="autoref"
    data-reference="sec:tech-stack">[sec:tech-stack]</a>.

3.  **Implementation**
    (<a href="#ch:implementation" data-reference-type="autoref"
    data-reference="ch:implementation">[ch:implementation]</a>): Produce
    a reference implementation on Databricks that instantiates the
    framework for the nine selected sources, with two built as full
    connectors covering the path from source API to silver and the
    remaining seven resolved as declared schema and mapping artifacts.
    The intended methodology is to drive generation by invoking the
    published skill catalog against each source.
    <a href="#sec:ai-eval" data-reference-type="autoref"
    data-reference="sec:ai-eval">[sec:ai-eval]</a> reports where this
    held empirically and where supervised direct coding was required.
    The deliverable is a minimum viable product that instantiates the
    framework end to end on a representative sample chosen to cover the
    ingestion and integration patterns the framework must support,
    rather than an exhaustive integration of every security tool an
    enterprise might deploy. Validation runs through automated tests
    with requirement traceability and through <span acronym-label="ldp"
    acronym-form="singular+short">ldp</span> data quality expectations.

The scope is application security posture across three tiers of
detection. **Static testing** covers preexecution analysis of source,
dependencies, configuration, and build artifacts:
<span acronym-label="sast" acronym-form="singular+short">sast</span>,
<span acronym-label="sca" acronym-form="singular+short">sca</span>,
secret scanning, container and <span acronym-label="iac"
acronym-form="singular+short">iac</span> scanning, and supply chain
integrity checks. **Dynamic testing** covers active probing of running
applications: <span acronym-label="dast"
acronym-form="singular+short">dast</span> (OWASP ZAP ) and penetration
testing. **Runtime security** covers observational and protective
telemetry from production systems. One representative source is
included, AWS WAF sampled requests , to demonstrate that the correlation
model links runtime findings to applications via deployment metadata.
Broader runtime security operations (general threat detection, incident
response, log analytics) remain out of scope. In all three tiers,
findings are correlated to business applications, owners, and
criticality.

<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> and
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> are framed against the
full <span acronym-label="aspm"
acronym-form="singular+short">aspm</span> scope.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> instantiates
the framework against the nine sources selected in
<a href="#sec:selected-sources" data-reference-type="autoref"
data-reference="sec:selected-sources">[sec:selected-sources]</a>. Two
are built as full connectors that exercise the two ends of the category
range from source API to silver. The remaining seven are resolved as
declared schema and mapping artifacts. Extending to them repeats the
procedure per source described in
<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a> and
does not require changes to the framework.

The intended audience is application security architects and data
platform engineers who need to consolidate security findings at scale
without vendor lockin.

### Methodology

This thesis follows the design science research methodology of  in three
phases aligned with the three main chapters. The **analysis** phase
combines a literature review with a systematic study of source systems,
then identifies the research gap. The **framework** phase derives
requirements and designs the architecture, data model, connector
contract, and analytics and serving patterns. The **implementation**
phase targets an <span acronym-label="ai"
acronym-form="singular+short">ai</span> instantiable reference
implementation, intended to be produced by invoking the skills cataloged
on the documentation site.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> records which
sources were built and
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> records the empirical
deviation: the delivered code was produced by <span acronym-label="ai"
acronym-form="singular+short">ai</span> assisted direct coding against
the framework contract and the external requirements specification, not
by invoking the published skill catalog. Validation runs through
automated tests with requirement traceability and through
<span acronym-label="ldp" acronym-form="singular+short">ldp</span> data
quality expectations.

The thesis delivers three contributions: a **requirements
specification**, a **reusable framework** covering architecture, data
model, connector contract, and analytics and serving patterns, and an
**<span acronym-label="ai" acronym-form="singular+short">ai</span>
instantiable reference implementation** on Databricks.

### Structure

<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> surveys the problem
domain and closes with related work, a gap analysis, and source system
selection. <a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> presents the framework:
solution architecture, data model, connector framework, and analytics
and serving framework.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> reports on
the MVP reference implementation, produced by <span acronym-label="ai"
acronym-form="singular+short">ai</span> assisted direct coding against
the framework contract, which instantiates two of the nine selected
sources as full connectors from source API to silver and the remaining
seven as declared schema and mapping artifacts. The Conclusion evaluates
outcomes against the objectives, defends the <span acronym-label="ai"
acronym-form="singular+short">ai</span> instantiability claim in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>, discusses limitations,
and suggests future work.
<a href="#app:genai" data-reference-type="autoref"
data-reference="app:genai">[app:genai]</a> discloses the use of
generative <span acronym-label="ai"
acronym-form="singular+short">ai</span> tooling.
<a href="#fig:contribution-flow" data-reference-type="autoref"
data-reference="fig:contribution-flow">[fig:contribution-flow]</a>
summarizes the contribution flow.

<figure id="fig:contribution-flow">

<figcaption>Thesis contribution flow. <a href="#ch:analysis"
data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> (Analysis) and <a
href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> (Framework) each
contribute material to the Requirements Specification published at <a
href="https://vkraus.github.io/appsec-docs/"
class="uri">https://vkraus.github.io/appsec-docs/</a>. <a
href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> (MVP
Implementation) consumes the specification. Invocations of the published
skill catalog required iterative amendment at every connector and are
evaluated in <a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>. Implementation results
populate the Implementation reports per source on the specification
(dashed return arrow).</figcaption>
</figure>

### External Documentation Site

The full requirements specification is published as an external
documentation site rather than inline in this thesis. It is structured
into four sections (Requirements, Functional Specification, Design,
Tests) generated with MkDocs Material from
<span class="mark">docs/</span> in the project repository and deployed
via GitHub Pages. Normative language
(<span class="smallcaps">shall</span>,
<span class="smallcaps">should</span>) is preserved on the site.

<div class="center">

**Documentation site:** <https://vkraus.github.io/appsec-docs/>  
**Source:** <https://github.com/vkraus/appsec-docs>

</div>

Where the main chapters name a page on the documentation site, they link
to it directly via an inline hyperlink. The top level sections of the
site relevant to the thesis are the [per category capability
matrix](https://vkraus.github.io/appsec-docs/platform/reference/source-capability-matrix/),
the [canonical mapping
requirements](https://vkraus.github.io/appsec-docs/platform/reference/canonical-mapping/),
the [connectors reference
hub](https://vkraus.github.io/appsec-docs/connectors/), and the
[requirement catalog and traceability
matrix](https://vkraus.github.io/appsec-docs/platform/reference/catalog/).

Offline copies of both the reference implementation and the
documentation site are attached to this submission as `mvp.zip` (source
code) and `docs.zip` (MkDocs sources and a prerendered static site under
`docs/site/index.html`). The attachments are snapshots of the repository
at the commit from which this <span acronym-label="pdf"
acronym-form="singular+short">pdf</span> was built. The live version
remains at the URL above.

## Analysis

This chapter analyzes the functional domains relevant to building an
application security data platform. Each section combines theoretical
foundations with practical tool and <span acronym-label="api"
acronym-form="singular+short">api</span> analysis, focusing on source
system interfaces, data models, and integration patterns. Technology
choices are deferred to
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> and
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>.

### Asset Discovery and Inventory

Asset discovery and inventory is the foundational data source for any
application security data platform. Organizations maintain application
inventories in a <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> or custom catalog, while cloud
providers and container orchestrators expose asset inventories through
<span acronym-label="api" acronym-form="plural+short">apis</span>.
Without this context, a vulnerability cannot be attributed to an owner,
scored for business impact, or prioritized.

#### Application Portfolio Management

Enterprise organizations maintain catalogs of their business
applications with metadata such as application name, description,
ownership information, lifecycle status, and relationships to other
assets .

These registries also capture security relevant attributes. Information
security is commonly assessed along the <span acronym-label="cia"
acronym-form="singular+short">cia</span> triad: confidentiality
(preventing unauthorized disclosure), integrity (preventing unauthorized
modification), and availability (ensuring authorized access) . Business
impact assessments evaluate all three <span acronym-label="cia"
acronym-form="singular+short">cia</span> dimensions to produce
criticality ratings, commonly structured as tiers: Tier 1 for mission
critical applications, Tier 2 for important supporting systems, and
Tier 3 for noncritical internal tools . Regulatory scope flags identify
which compliance frameworks apply to a given application.

For data integration, the most important attribute is the mapping
between business applications and their technical assets. A single
business application may span multiple repositories, microservices,
infrastructure components, and deployment environments. When the
framework ingests a vulnerability from a <span acronym-label="sast"
acronym-form="singular+short">sast</span> scanner linked to a specific
repository, this mapping determines which business application is
affected, who owns it, and how critical it is, so that prioritization
reflects risk.

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
the <span class="mark">cmdb_ci</span> base table. Each subclass inherits
base attributes (name, <span class="mark">sys_id</span> , operational
status, environment) and adds domain specific fields. For application
inventory purposes, the most relevant class is
<span class="mark">cmdb_ci_business_app</span> (Business Application),
which extends the base <span acronym-label="ci"
acronym-form="singular+short">ci</span> with attributes such as version,
business unit, used for classification, and references to the owning
support group . The <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> pipeline ingests this class
together with <span class="mark">cmdb_rel_ci</span> .

Beyond the application record itself, the <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> captures relationships between
<span acronym-label="ci" acronym-form="plural+short">cis</span> through
a dedicated relationship table ( <span class="mark">cmdb_rel_ci</span>
). These model dependencies such as “runs on” (application to server),
“depends on” (application to database), and “hosted on” (application to
cloud service). The most valuable relationships for the framework are
those linking business applications to technical assets corresponding to
entities in the security data: repository names, deployment targets, and
infrastructure components. ServiceNow allows custom attributes and
relationship types, so available fields vary between deployments.

#### Integration Options

Integrating <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> data requires choosing between
two strategies: pulling data from ServiceNow via its
<span acronym-label="api" acronym-form="plural+short">apis</span>, or
pushing data from a custom ServiceNow application to an external target.

##### ServiceNow APIs

ServiceNow exposes two complementary <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> for <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> data extraction. The Table
<span acronym-label="api" acronym-form="singular+short">api</span>
provides generic CRUD operations against any ServiceNow table through
the endpoint <span class="mark">/api/now/table/{tableName}</span>  .
Responses are <span acronym-label="json"
acronym-form="singular+short">json</span> formatted, with support for
server side filtering ( <span class="mark">sysparm_query</span> ), field
selection ( <span class="mark">sysparm_fields</span> ), and pagination
via <span class="mark">sysparm_limit</span> and
<span class="mark">sysparm_offset</span> (default maximum of
10 000 records per request). The
<span class="mark">sysparm_display_value</span> parameter resolves
reference fields to human readable names instead of internal
<span class="mark">sys_id</span> values.

The <span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
Instance <span acronym-label="api"
acronym-form="singular+short">api</span> (
<span class="mark">/now/cmdb/instance/{className}</span> ) provides a
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
aware alternative that understands the <span acronym-label="ci"
acronym-form="singular+short">ci</span> class hierarchy . It retrieves a
<span acronym-label="ci" acronym-form="singular+short">ci</span> with
its relationships in a single call, reducing <span acronym-label="api"
acronym-form="singular+short">api</span> calls needed to reconstruct the
mapping from application to asset, but is more constrained in query
capabilities than the Table <span acronym-label="api"
acronym-form="singular+short">api</span>.

Both <span acronym-label="api" acronym-form="plural+short">apis</span>
require authentication, typically Basic Authentication with a service
account granted the <span class="mark">rest_service</span> or
<span class="mark">cmdb_read</span> role, or OAuth 2.0 for more security
conscious deployments . Rate limits are governed by platform transaction
quotas rather than per endpoint limits. For incremental extraction, the
<span class="mark">sys_updated_on</span> timestamp present on all
records serves as a reliable high water mark .

Any pull based integration must handle authentication, pagination, rate
limiting, and incremental state management. Tooling choices specific to
each source are documented on the [ServiceNow source reference
page](https://vkraus.github.io/appsec-docs/connectors/cmdb/servicenow/).

##### ServiceNow Application

An alternative is to push data from the source. ServiceNow supports
scoped applications running on the platform. A custom application can
use Outbound REST Messages to send <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> data to an external target (a
cloud storage bucket or a <span acronym-label="rest"
acronym-form="singular+short">rest</span> endpoint) on a schedule
defined through Scheduled Jobs or Flow Designer. It can also expose a
Scripted <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> : a custom endpoint that
formats data exactly as the consumer needs it, prejoining application
records with relationships and custom attributes in a single response.

The advantage is full access to ServiceNow’s scripting, relationship
traversal, and business logic without external <span acronym-label="api"
acronym-form="singular+short">api</span> call overhead. The disadvantage
is that development and maintenance happen inside ServiceNow, requiring
platform expertise and a separate deployment lifecycle, with schema or
logic changes coordinated across two platforms. This approach suits
organizations with mature ServiceNow development teams that prefer to
own export logic on the source side.

##### Integration Challenges

The application inventory is the least standardized integration among
all data sources. Security testing tools converge around common
<span acronym-label="api" acronym-form="singular+short">api</span>
patterns and formats, but each organization structures its application
inventory differently: hierarchy, granularity of asset mapping, and
captured attributes vary substantially . This makes the inventory
connector hardest to generalize and most likely to require
customization.

Data quality in <span acronym-label="cmdb"
acronym-form="plural+short">cmdbs</span> is a persistent concern .
Records are often incomplete or stale. A common case is a decommissioned
application still listed as active with no current owner. Integrations
must account for these issues through validation rules and defaults that
flag problems without blocking the pipeline.

Despite these difficulties, the application inventory is indispensable:
without its business context, findings lack organizational meaning for
prioritization and governance.

Alternative platforms include BMC Helix, Device42, and the open source
Ralph. Cloud native services such as AWS Config and Azure Resource Graph
expose equivalent inventories for cloud resources, consumed through
provider native <span acronym-label="api"
acronym-form="plural+short">apis</span> with IAM scoped credentials. The
bronze ingestion pattern
(<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>) applies to any source
with an inventory <span acronym-label="api"
acronym-form="singular+short">api</span>.

### Software Development

Modern software is built collaboratively from source code, organized in
repositories, and deployed through automated pipelines . Repositories,
build pipelines, and issue trackers form the second major data source
category for the framework. These platforms share a common integration
pattern: <span acronym-label="rest"
acronym-form="singular+short">rest</span> over
<span acronym-label="json" acronym-form="singular+short">json</span>,
authentication via OAuth tokens, <span acronym-label="pat"
acronym-form="plural+short">pats</span>, or service accounts, offset or
cursor pagination, and rate limits that require backoff. This
consistency enables shared connector logic.

#### Source Code Management

provide a thorough treatment of Git, covering branching, merging, and
distributed workflows. offers a more recent visual introduction. extend
this to organizational scale, describing how large teams manage
repositories with thousands of contributors. For this thesis, the
repository is the primary entity around which findings are grouped, as
detailed in <a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>.

Development teams host Git repositories on cloud based
<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms. GitHub is dominant, with over 150 million developers and
adoption by 92% of Fortune 100 companies . The 2025 Stack Overflow
Developer Survey reports GitHub at 81% adoption for code collaboration,
followed by GitLab at 36% . Bitbucket and Azure DevOps serve smaller but
significant enterprise segments. Most large organizations run multiple
platforms through acquisitions, team preferences, or regulatory splits.
Multi platform ingestion is therefore a practical requirement.

Beyond source code, <span acronym-label="scm"
acronym-form="singular+short">scm</span> platforms expose security
relevant metadata: primary language, creation and last activity dates,
visibility, and archive status. Branch protection rules indicate
development process maturity. Team and contributor assignments establish
ownership feeding into the mapping from application to team from
<a href="#sec:app-inventory" data-reference-type="autoref"
data-reference="sec:app-inventory">[sec:app-inventory]</a>.

GitHub exposes two <span acronym-label="api"
acronym-form="plural+short">apis</span> : <span acronym-label="rest"
acronym-form="singular+short">rest</span> (v3) with resource oriented
endpoints and page based pagination, and GraphQL (v4) with selective
field retrieval and cursor pagination. Both share authentication (OAuth
tokens or <span acronym-label="pat"
acronym-form="plural+short">pats</span>) and a rate limit of 5 000
requests per hour . All use token based authentication and
<span acronym-label="json" acronym-form="singular+short">json</span>
responses, enabling shared connector logic.

Other enterprise <span acronym-label="scm"
acronym-form="singular+short">scm</span> platforms expose comparable
<span acronym-label="rest" acronym-form="singular+short">rest</span>
(and sometimes GraphQL) <span acronym-label="api"
acronym-form="plural+short">apis</span>:
[GitLab](https://vkraus.github.io/appsec-docs/connectors/scm/gitlab/),
Bitbucket, and Azure DevOps Repos. Details for each of the selected nine
sources are on the [connectors reference
hub](https://vkraus.github.io/appsec-docs/connectors/). Other tools
named in this survey do not have dedicated reference pages.

#### Continuous Integration and Delivery

<span acronym-label="sdlc" acronym-form="singular+short">sdlc</span>
practices have shifted from sequential models to iterative methodologies
and DevOps. present empirical evidence that high performing teams deploy
more frequently with shorter lead times through
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
automation. provide practical guidance for implementing DevOps pipelines
at scale. The <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> pipeline is relevant because
each stage can integrate security tools.

GitHub Actions is the most adopted <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> platform, used by 62% of
developers for personal projects and 41% in organizational settings .
Jenkins remains prevalent in enterprises at 28% organizational adoption,
followed by GitLab CI at 19%. 32% of organizations use two or more
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
tools and 9% use at least three, reinforcing the multiplatform
integration challenge seen with <span acronym-label="scm"
acronym-form="singular+short">scm</span> platforms.

<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
platforms provide contextual data about security scans. Pipeline
definitions reveal which tools run. Build results show whether gates
passed. Execution metadata records commit, timing, and duration. This is
operational context rather than a primary finding source: a repository
whose last scan ran three months ago, or whose scans consistently fail,
signals coverage gaps and tool health.

Integration patterns vary more across <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> platforms than across
<span acronym-label="scm" acronym-form="singular+short">scm</span>
tools. GitHub Actions and Azure Pipelines expose
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="plural+short">apis</span> with
<span acronym-label="json" acronym-form="singular+short">json</span>
responses, Jenkins uses an <span acronym-label="xml"
acronym-form="singular+short">xml</span> based <span acronym-label="api"
acronym-form="singular+short">api</span> with a different authentication
model, and GitLab CI piggybacks on the GitLab <span acronym-label="api"
acronym-form="singular+short">api</span>. Despite these differences,
retrieved data is structurally similar: pipeline identifiers, run
statuses, timestamps, and commit references. None of these
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
platforms is built as a connector in the reference implementation.
Details for each of the selected nine sources are on the [connectors
reference hub](https://vkraus.github.io/appsec-docs/connectors/). Other
tools named in this survey do not have dedicated reference pages.

#### Issue Tracking

Issue trackers record remediation status. When a finding is assigned for
remediation, an issue is created in the tracker for the team manually or
through automation. The framework reads issue status to determine
whether a finding is under active remediation, who is responsible, and
whether it has been resolved within the <span acronym-label="sla"
acronym-form="singular+short">sla</span> window.

Jira is the dominant enterprise issue tracker. The 2025 Stack Overflow
Developer Survey reports Jira at 46% adoption, behind only GitHub (81%)
and ahead of GitLab (36%) . Azure DevOps Work Items serves the Microsoft
ecosystem. GitHub Issues and GitLab Issues provide lightweight built in
tracking tied to their <span acronym-label="scm"
acronym-form="singular+short">scm</span> platforms. Many organizations
use multiple trackers across teams.

These platforms expose <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> with <span acronym-label="json"
acronym-form="singular+short">json</span> responses and paginated
results, and most support webhooks for real time status change
notifications. None is built as a connector in the reference
implementation. Details for each of the selected nine sources are on the
[connectors reference
hub](https://vkraus.github.io/appsec-docs/connectors/). Other tools
named in this survey do not have dedicated reference pages.

Integration is bidirectional: the framework reads remediation status and
may create new issues when findings require attention. This raises
idempotency concerns (avoiding duplicate issue creation) and state
synchronization (keeping the view of the framework consistent with the
tracker).

### Static Application Security

Application security encompasses practices and tools for identifying
vulnerabilities throughout the software lifecycle . advocated for
security touchpoints spanning development. The DevSecOps paradigm 
realizes this by embedding security testing into
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
pipelines. <span acronym-label="sast"
acronym-form="singular+short">sast</span> examines source code,
<span acronym-label="sca" acronym-form="singular+short">sca</span>
checks third party dependencies, secret scanners flag leaked
credentials, and <span acronym-label="dast"
acronym-form="singular+short">dast</span> probes running applications.
These tools produce large volumes of data in different
<span acronym-label="api" acronym-form="plural+short">apis</span>,
formats, and severity models. The <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> Top 10 classifies common web
application risks  but does not define a data interchange standard.

Several cross cutting standards bring partial consistency. The
<span acronym-label="cve" acronym-form="singular+short">cve</span>
system assigns unique identifiers to known vulnerabilities .
<span acronym-label="cwe" acronym-form="singular+short">cwe</span>
classifies weakness types . <span acronym-label="cvss"
acronym-form="singular+short">cvss</span> scores attack vector,
complexity, and impact on a 0–10 scale . <span acronym-label="epss"
acronym-form="singular+short">epss</span> adds a predictive signal : the
<span acronym-label="ml" acronym-form="singular+short">ml</span>
computed probability that a vulnerability will be exploited within
30 days. <span acronym-label="cisa"
acronym-form="singular+short">cisa</span> maintains the
<span acronym-label="kev" acronym-form="singular+short">kev</span>
catalog , which adds a third signal: confirmed active exploitation from
real world incidents.

For data interchange, <span acronym-label="sarif"
acronym-form="singular+short">sarif</span> defines a
<span acronym-label="json" acronym-form="singular+short">json</span>
based format for static analysis results . CycloneDX and
<span acronym-label="spdx" acronym-form="singular+short">spdx</span>
provide <span acronym-label="sbom"
acronym-form="singular+short">sbom</span> schemas .
<span acronym-label="ocsf" acronym-form="singular+short">ocsf</span>
standardizes security event exchange for <span acronym-label="siem"
acronym-form="singular+short">siem</span> and <span acronym-label="soar"
acronym-form="singular+short">soar</span> use cases . No single format
covers all tool categories:

- <span acronym-label="sarif" acronym-form="singular+short">sarif</span>
  addresses static analysis but not <span acronym-label="sca"
  acronym-form="singular+short">sca</span> or runtime findings.

- CycloneDX and <span acronym-label="spdx"
  acronym-form="singular+short">spdx</span> cover software composition,
  not code level vulnerabilities.

- <span acronym-label="ocsf" acronym-form="singular+short">ocsf</span>
  serves security operations, not application security posture.

This gap motivates the normalization model in
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>.

Static analysis tools examine source code and build artifacts without
executing the application. Their findings point to repositories, files,
and lines, so developers own them directly. Mobile application security
testing is excluded, as the framework targets web applications and
backend services.

#### Static Application Security Testing

<span acronym-label="sast" acronym-form="singular+short">sast</span>
examines source code, bytecode, or binary code without executing the
program. cover taint analysis, control flow analysis, and pattern
matching for detecting injection flaws, buffer overflows, and insecure
data handling. Broader rule sets catch more issues and generate more
noise . That is the central <span acronym-label="sast"
acronym-form="singular+short">sast</span> tradeoff.

SonarQube exposes a <span acronym-label="rest"
acronym-form="singular+short">rest</span> Web <span acronym-label="api"
acronym-form="singular+short">api</span> ([source
reference](https://vkraus.github.io/appsec-docs/connectors/sast/sonarqube/)),
and Semgrep runs as a <span acronym-label="cli"
acronym-form="singular+short">cli</span> tool producing
<span acronym-label="json" acronym-form="singular+short">json</span> or
<span acronym-label="sarif" acronym-form="singular+short">sarif</span>
output with an optional Cloud Platform <span acronym-label="api"
acronym-form="singular+short">api</span> ([source
reference](https://vkraus.github.io/appsec-docs/connectors/sast/semgrep/)).
<span acronym-label="scm" acronym-form="singular+short">scm</span>
integrated scanners such as GitHub Code Scanning (CodeQL) and GitLab
<span acronym-label="sast" acronym-form="singular+short">sast</span>
report through the host <span acronym-label="scm"
acronym-form="singular+short">scm</span> <span acronym-label="api"
acronym-form="singular+short">api</span>. Commercial alternatives
include Checkmarx and Fortify, both exposing <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span>. Details for each of the
selected nine sources are on the [connectors reference
hub](https://vkraus.github.io/appsec-docs/connectors/). Other tools
named in this survey do not have dedicated reference pages. When
platform native and standalone tools scan the same repository, the
overlap requires deduplication in the normalization layer.

Findings typically include a rule identifier, affected file path and
line number, severity, code snippet, and remediation guidance. Severity
models differ. SonarQube uses a five level scale (blocker, critical,
major, minor, info). Semgrep and Checkmarx use high, medium, and low,
sometimes with a numerical score. Severity normalization is therefore a
core transformation.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> resolves
SonarQube and Semgrep to ingestion categories and publishes their
reference pages per source. Only the ServiceNow and GitHub connectors
are built as working code at <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> time.

#### Software Composition Analysis

<span acronym-label="sca" acronym-form="singular+short">sca</span>
identifies known vulnerabilities in third party dependencies. Modern
applications pull in hundreds of transitive dependencies , any of which
can introduce a vulnerability. provide a systematic review of supply
chain attacks including typosquatting, dependency confusion, and
malicious package injection. <span acronym-label="sca"
acronym-form="singular+short">sca</span> tools analyze dependency
manifests, resolve the full tree, and cross reference versions against
vulnerability databases such as the <span acronym-label="nvd"
acronym-form="singular+short">nvd</span>.

<span acronym-label="owasp" acronym-form="singular+short">owasp</span>
Dependency-Track is an open source platform that ingests
<span acronym-label="sbom" acronym-form="plural+short">sboms</span> in
CycloneDX or <span acronym-label="spdx"
acronym-form="singular+short">spdx</span> format and exposes a
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span>
([source
reference](https://vkraus.github.io/appsec-docs/connectors/sca/dependency-track/)).
Snyk exposes a <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span>, and Dependabot exposes alerts
through the GitHub GraphQL <span acronym-label="api"
acronym-form="singular+short">api</span>. Details for each of the
selected nine sources are on the [connectors reference
hub](https://vkraus.github.io/appsec-docs/connectors/). Other tools
named in this survey do not have dedicated reference pages. Many
<span acronym-label="sca" acronym-form="singular+short">sca</span> tools
also generate <span acronym-label="sbom"
acronym-form="plural+short">sboms</span> , increasingly required by
regulators . <a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> resolves
Dependency-Track to <span acronym-label="dltool"
acronym-form="singular+short">dltool</span>, and GitHub Dependabot and
GitLab dependency scanning are reached through their respective platform
<span acronym-label="api" acronym-form="plural+short">apis</span>. Only
the ServiceNow and GitHub connectors are built as working code at
<span acronym-label="mvp" acronym-form="singular+short">mvp</span> time.

<span acronym-label="sca" acronym-form="singular+short">sca</span>
output is more standardized than other categories. The data comes from
shared public databases (<span acronym-label="cve"
acronym-form="singular+short">cve</span>, <span acronym-label="nvd"
acronym-form="singular+short">nvd</span>). Findings include the
vulnerable dependency name and version, a <span acronym-label="cve"
acronym-form="singular+short">cve</span> identifier, a
<span acronym-label="cvss" acronym-form="singular+short">cvss</span>
score, the fixed version when available, and exploitability metadata.
Tools may resolve the same dependency tree differently, so two scanners
flag inconsistent <span acronym-label="cve"
acronym-form="plural+short">cves</span>. The framework handles this
during deduplication, recognizing that the same
<span acronym-label="cve" acronym-form="singular+short">cve</span>
reported by multiple tools against the same repository likely represents
a single issue.

<span acronym-label="sca" acronym-form="singular+short">sca</span> tools
also detect license violations (e.g., GPL licensed code in proprietary
applications). The <span acronym-label="slsa"
acronym-form="singular+short">slsa</span> framework  complements
<span acronym-label="sca" acronym-form="singular+short">sca</span>.
<span acronym-label="sca" acronym-form="singular+short">sca</span>
checks whether dependencies contain known vulnerabilities.
<span acronym-label="slsa" acronym-form="singular+short">slsa</span>
verifies the integrity and provenance of build artifacts.

<span acronym-label="owasp" acronym-form="singular+short">owasp</span>
Dependency-Check, a <span acronym-label="cli"
acronym-form="singular+short">cli</span> oriented alternative that
writes <span acronym-label="json"
acronym-form="singular+short">json</span> or <span acronym-label="xml"
acronym-form="singular+short">xml</span> reports from
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
runs, fits the same <span acronym-label="cli"
acronym-form="singular+short">cli</span> artifact ingestion pattern as
Semgrep’s <span acronym-label="cli"
acronym-form="singular+short">cli</span> mode. Details for each of the
selected nine sources are on the [connectors reference
hub](https://vkraus.github.io/appsec-docs/connectors/). Other tools
named in this survey do not have dedicated reference pages.

#### Secret Detection

Secret detection tools scan version control history for credentials,
<span acronym-label="api" acronym-form="singular+short">api</span> keys,
tokens, and other sensitive material. Once committed, a secret persists
in Git history even after deletion from the working tree. Two techniques
apply: regex patterns against known credential formats, and entropy
scoring against unusually random strings. The entropy approach catches
novel formats at higher false positive rates.

TruffleHog is a <span acronym-label="cli"
acronym-form="singular+short">cli</span> tool combining pattern and
entropy analysis with live credential verification, producing
<span acronym-label="json" acronym-form="singular+short">json</span>
output parsed as an artifact ([source
reference](https://vkraus.github.io/appsec-docs/connectors/secrets/trufflehog/)).
GitLeaks and detect-secrets are similar <span acronym-label="cli"
acronym-form="singular+short">cli</span> oriented alternatives, and
commercial offerings such as GitGuardian expose
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="plural+short">apis</span> for
centralized management. Details for each of the selected nine sources
are on the [connectors reference
hub](https://vkraus.github.io/appsec-docs/connectors/). Other tools
named in this survey do not have dedicated reference pages.

Scanners integrated into the platform differ. GitHub Secret Scanning
exposes alerts through the GitHub <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> with webhook notifications ,
and GitLab Secret Detection reports through GitLab’s security dashboard
and <span acronym-label="api" acronym-form="singular+short">api</span>.
These are simpler to integrate because they reuse platform
<span acronym-label="api" acronym-form="plural+short">apis</span> but
cover only repositories on their own platforms.

There is no standard output format. Each tool defines its own
<span acronym-label="json" acronym-form="singular+short">json</span>
schema, and none supports <span acronym-label="sarif"
acronym-form="singular+short">sarif</span>. Findings include secret
type, file path, commit reference, and sometimes validity status, but
field names and structures vary.

### Dynamic Application Security Testing

Dynamic application security testing operates on running applications by
actively issuing requests and evaluating responses. Unlike static
analysis, it requires a deployed instance and detects flaws that
manifest only at execution time: authentication bypass, server
misconfiguration, and certain injection classes. This section covers
active scanning.
<a href="#sec:runtime-security" data-reference-type="autoref"
data-reference="sec:runtime-security">[sec:runtime-security]</a> covers
passive telemetry. The cross cutting standards from
<a href="#sec:static-appsec" data-reference-type="autoref"
data-reference="sec:static-appsec">[sec:static-appsec]</a> apply equally
to dynamic findings.

#### Dynamic Application Security Testing

<span acronym-label="dast" acronym-form="singular+short">dast</span>
tests running applications by sending crafted <span acronym-label="http"
acronym-form="singular+short">http</span> requests and analyzing
responses for vulnerability indicators . Unlike
<span acronym-label="sast" acronym-form="singular+short">sast</span>,
<span acronym-label="dast" acronym-form="singular+short">dast</span>
requires a deployed application and detects vulnerabilities that
manifest only at runtime, such as authentication bypass, server
misconfiguration, and certain injection flaws.

<span acronym-label="owasp" acronym-form="singular+short">owasp</span>
<span acronym-label="zap" acronym-form="singular+short">zap</span> is
the most widely used open source <span acronym-label="dast"
acronym-form="singular+short">dast</span> tool, exposing a
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span> for
scan management and alert retrieval ([source
reference](https://vkraus.github.io/appsec-docs/connectors/dast/owasp-zap/)).
Burp Suite Enterprise exposes a <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span>, while the Professional edition
is a desktop tool without programmatic access. Details for each of the
selected nine sources are on the [connectors reference
hub](https://vkraus.github.io/appsec-docs/connectors/). Other tools
named in this survey do not have dedicated reference pages. Findings
include the target <span acronym-label="url"
acronym-form="singular+short">url</span>, affected
<span acronym-label="http" acronym-form="singular+short">http</span>
parameter, vulnerability type mapped to <span acronym-label="cwe"
acronym-form="singular+short">cwe</span> , exploitation evidence, and
confidence rating.

The core integration challenge is that <span acronym-label="dast"
acronym-form="singular+short">dast</span> findings are
<span acronym-label="url" acronym-form="singular+short">url</span>
based, not code based. Mapping <span acronym-label="url"
acronym-form="singular+short">url</span> based findings to source
repositories requires deployment metadata or inventory data from
<a href="#sec:app-inventory" data-reference-type="autoref"
data-reference="sec:app-inventory">[sec:app-inventory]</a>. Without
this, <span acronym-label="dast"
acronym-form="singular+short">dast</span> findings can be attributed to
applications but not to development teams or code locations.

### Runtime Security

Runtime security covers passive telemetry from production workloads,
sitting alongside the active scanning in
<a href="#sec:dynamic-appsec" data-reference-type="autoref"
data-reference="sec:dynamic-appsec">[sec:dynamic-appsec]</a> and
completing the three detection tiers the framework uses: static,
dynamic, and runtime. The representative tool in this tier is the
<span acronym-label="waf" acronym-form="singular+short">waf</span>. It
does not execute scans. It inspects live <span acronym-label="http"
acronym-form="singular+short">http</span> traffic and emits events when
rules fire, marking exploitation attempts against a workload or endpoint
and linking to applications through deployment metadata rather than
source code coordinates. Broader runtime operations such as
<span acronym-label="siem" acronym-form="singular+short">siem</span>
driven incident response and general log analytics are adjacent but out
of scope. The framework treats runtime security as one input tier among
three, correlated with static and dynamic findings through the shared
application inventory.

#### Web Application Firewalls

<span acronym-label="waf" acronym-form="plural+short">wafs</span>
operate at the network perimeter, inspecting inbound
<span acronym-label="http" acronym-form="singular+short">http</span>
traffic against rule sets such as the <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> Core Rule Set . They log
blocked and flagged requests with matched rule, request details, and
action taken. <span acronym-label="aws"
acronym-form="singular+short">aws</span> WAF exposes the
<span class="mark">GetSampledRequests</span> <span acronym-label="api"
acronym-form="singular+short">api</span> as the primary interface, with
CloudWatch Logs as an opt in extension for deployments requiring full
fidelity logging ([source
reference](https://vkraus.github.io/appsec-docs/connectors/waf/aws-waf/)).
Cloudflare and Akamai expose comparable <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> for log retrieval and
configuration. Details for each of the selected nine sources are on the
[connectors reference
hub](https://vkraus.github.io/appsec-docs/connectors/). Other tools
named in this survey do not have dedicated reference pages.

These platforms bundle <span acronym-label="ddos"
acronym-form="singular+short">ddos</span> protection alongside
<span acronym-label="waf" acronym-form="singular+short">waf</span>
capabilities. <span acronym-label="ddos"
acronym-form="singular+short">ddos</span> mitigation logs traffic
patterns, attack signatures, and mitigation actions, providing
availability impact data that complements vulnerability findings.

<span acronym-label="waf" acronym-form="plural+short">wafs</span> emit
event streams, not discrete findings. The framework consumes aggregated
patterns, not raw logs.

#### Source Integration Summary

The [source characteristics reference
page](https://vkraus.github.io/appsec-docs/platform/reference/source-characteristics/)
tabulates integration characteristics across the AppSec source landscape
surveyed for the thesis.

Several patterns emerge. <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> with <span acronym-label="json"
acronym-form="singular+short">json</span> responses are dominant, but
<span acronym-label="xml" acronym-form="singular+short">xml</span>,
GraphQL, <span acronym-label="cli"
acronym-form="singular+short">cli</span> output parsing, and manual
uploads are all necessary. Standardization varies:
<span acronym-label="sca" acronym-form="singular+short">sca</span>
benefits from the <span acronym-label="cve"
acronym-form="singular+short">cve</span>/<span acronym-label="nvd"
acronym-form="singular+short">nvd</span> ecosystem,
<span acronym-label="sast" acronym-form="singular+short">sast</span> is
partially standardized through <span acronym-label="sarif"
acronym-form="singular+short">sarif</span>, and secret scanning has no
standard format. Update frequencies range from continuous dependency
monitoring to periodic penetration tests. These characteristics define
what the ingestion layer in
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> must accommodate.

### Data Engineering

Consolidating the heterogeneous sources analyzed above into a unified
analytical platform is a data integration problem. This section surveys
the architectural paradigms and engineering patterns relevant to solving
it.

#### Data Platform Architecture

The literature documents a progression from data warehouses through data
lakes to the lakehouse. provide the data management body of knowledge.
The data warehouse, formalized by , stores subject oriented, integrated
data using a normalized approach. take a bottom up path with dimensional
modeling: star schemas of fact and dimension tables. Both approaches
assume structured, stable sources. Security tool output is neither.

The data lake  stores raw data in its native format, deferring schema to
consumption time (schema on read). This accommodates format diversity
but risks “data swamps” without governance .

The lakehouse  combines data lake flexibility with warehouse governance
through open table formats adding <span acronym-label="acid"
acronym-form="singular+short">acid</span> transactions, schema
enforcement, and time travel on top of lake storage . It accepts semi
structured tool output and gives the governance and fast queries needed
for both dashboards and operational lookups.

The medallion architecture  organizes lakehouse data into three layers:

- **Bronze**: Raw data with minimal transformation, preserving original
  source schemas.

- **Silver**: Cleaned, validated, and normalized data conforming to a
  unified schema.

- **Gold**: aggregated metrics and enriched datasets ready for queries.

This maps naturally to security data integration. Bronze captures raw
tool output in source native schemas, silver normalizes findings into a
vendor agnostic model, and gold computes aggregated risk metrics and
enriched datasets stakeholders consume.

A security data platform must serve two access patterns.
<span acronym-label="olap" acronym-form="singular+short">olap</span>
queries power dashboards and trend analysis over large aggregated
datasets. <span acronym-label="oltp"
acronym-form="singular+short">oltp</span> access supports operational
workflows such as issue tracker integration and real time risk lookups,
where low latency reads and writes to individual records are essential.
Both inform the serving architecture in
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>.

#### Data Integration Patterns

distinguish <span acronym-label="etl"
acronym-form="singular+short">etl</span> from <span acronym-label="elt"
acronym-form="singular+short">elt</span>. <span acronym-label="etl"
acronym-form="singular+short">etl</span> transforms data before loading,
requiring upfront schema knowledge. <span acronym-label="elt"
acronym-form="singular+short">elt</span> loads raw data first and
transforms in place, aligning with lakehouse architectures where
distributed compute engines perform transformations at scale . Security
tool output varies and evolves, so upfront transformation breaks.
<span acronym-label="elt" acronym-form="singular+short">elt</span> fits.

Full reingestion does not scale across thousands of repositories and
dozens of tools. Incremental ingestion pulls only new or changed
records. The high water mark pattern tracks a timestamp or cursor per
source. <span acronym-label="cdc"
acronym-form="singular+short">cdc</span> captures changes at the source
level, propagating inserts, updates, and deletes as events .

Source <span acronym-label="api" acronym-form="plural+short">apis</span>
and formats change regularly, so rigid schemas break pipelines on every
upstream change. Schema on read stores raw data in its original
structure and applies schema at query time. Additive evolution accepts
new fields , and existing queries keep working.

Reruns are idempotent so retries and replays do not duplicate. Each
layer validates: schema at ingest, value ranges at normalization,
referential integrity at aggregation. Records that fail validation go to
quarantine tables .

#### Domain Data Model

The security domains analyzed above produce data about a common set of
entities and relationships. A vendor agnostic conceptual model must
precede physical schemas. The domain model has five primary entities:

- **Applications** carry business context from asset inventories
  (<a href="#sec:app-inventory" data-reference-type="autoref"
  data-reference="sec:app-inventory">[sec:app-inventory]</a>): name,
  owning team, criticality tier, lifecycle status, and compliance scope.
  An application represents a business level unit that may span multiple
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
  acronym-form="singular+short">cve</span> identified issues enriched
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

More entities add development and supply chain context:

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

- **Dependencies** represent third party libraries identified through
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
analytical model. Supporting entities provide development process and
supply chain context.

<figure id="fig:domain-model">

<figcaption>Conceptual Domain Model</figcaption>
</figure>

The mapping from app to repo is the key relationship. It links findings
to business context and is many to many: shared libraries serve multiple
applications, and microservice applications span multiple repositories.
Teams own applications, establishing the chain from organizational
accountability through business applications to technical assets and
findings. Dependencies bridge repositories and vulnerabilities: an
<span acronym-label="sca" acronym-form="singular+short">sca</span>
finding links a specific library version to a known
<span acronym-label="cve" acronym-form="singular+short">cve</span>.
Issues track remediation.

The structure maps to dimensional modeling . Findings are facts.
Applications, repositories, and teams are dimensions. Commits, pull
requests, and pipeline runs add temporal and process dimensions. Cross
tool deduplication collapses related findings while preserving
traceability to each source.

Stakeholders consume this data through different patterns:

- Application owners need aggregated risk dashboards showing finding
  counts by severity, remediation progress, and compliance status.

- Developers need actionable findings with code level context, delivered
  through issue trackers.

- Security experts need drill down access to raw findings, audit trails,
  and cross tool correlation for triage.

- Leadership needs executive metrics: <span acronym-label="mttr"
  acronym-form="singular+short">mttr</span>, <span acronym-label="sla"
  acronym-form="singular+short">sla</span> compliance, vulnerability
  density trends, and portfolio level comparisons.

These span the <span acronym-label="olap"
acronym-form="singular+short">olap</span> and <span acronym-label="oltp"
acronym-form="singular+short">oltp</span> requirements from
<a href="#sec:data-architecture" data-reference-type="autoref"
data-reference="sec:data-architecture">[sec:data-architecture]</a> and
drive the serving architecture in
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>.

### Related Work and Gap Analysis

No standard approach exists for consolidating security tool output into
a unified data platform. Organizations face a fragmented landscape of
partial solutions.

#### Existing Approaches

define <span acronym-label="aspm"
acronym-form="singular+short">aspm</span> as tools that continuously
manage application risk through collection, analysis, and prioritization
of security issues across the software lifecycle. Commercial platforms
such as Apiiro, Cycode, ArmorCode, and Snyk AppRisk aggregate findings
into unified dashboards with correlation and risk scoring, but they are
proprietary. Pipelines cannot be customized, custom
<span acronym-label="ml" acronym-form="singular+short">ml</span> cannot
be added, and integrations are limited to what the vendor supports.

Platform native features cover only their own ecosystem. GitHub Advanced
Security provides code scanning via CodeQL, secret scanning, and
dependency review . GitLab bundles <span acronym-label="sast"
acronym-form="singular+short">sast</span>, <span acronym-label="dast"
acronym-form="singular+short">dast</span>, dependency scanning,
container scanning, and a security dashboard . Organizations using
multiple <span acronym-label="scm"
acronym-form="singular+short">scm</span> platforms or third party tools
cannot consolidate through them.

DefectDojo  is the most prominent open source alternative, supporting
imports from over 150 tools through format specific parsers. It was
designed as a vulnerability management interface rather than a data
platform. Its PostgreSQL backend limits enterprise scale analytics, and
advanced <span acronym-label="api"
acronym-form="singular+short">api</span> connectors are commercial only.
<span acronym-label="ocsf" acronym-form="singular+short">ocsf</span> 
standardizes security event schemas for <span acronym-label="siem"
acronym-form="singular+short">siem</span> and <span acronym-label="soar"
acronym-form="singular+short">soar</span> but does not model application
level entities such as repositories, applications, or teams.

Many enterprises build ad hoc integrations: custom scripts,
<span acronym-label="etl" acronym-form="singular+short">etl</span>
pipelines, and dashboards from manual exports. These lack schema
governance, break on <span acronym-label="api"
acronym-form="singular+short">api</span> changes, and persist as
institutional knowledge in unmaintained scripts.

#### Databricks Lakewatch

Databricks announced Lakewatch in March 2026 as an open, agentic
<span acronym-label="siem" acronym-form="singular+short">siem</span>
built on the Databricks lakehouse . It unifies security,
<span acronym-label="it" acronym-form="singular+short">it</span>, and
business data in a single governed environment powered by Delta Lake and
Unity Catalog, with agentic triage, Detection as Code, and integrations
from Wiz, Palo Alto Networks, Okta, and Zscaler.

Lakewatch focuses on runtime security operations: threat detection,
incident response, alert triage, and log analytics. This framework
focuses on application security posture: findings from
<span acronym-label="sast" acronym-form="singular+short">sast</span>,
<span acronym-label="sca" acronym-form="singular+short">sca</span>,
<span acronym-label="dast" acronym-form="singular+short">dast</span>,
secret scanning, container scanning, and <span acronym-label="iac"
acronym-form="singular+short">iac</span> tools, combined with
remediation tracking and risk aggregation. The two are complementary.
Shared lakehouse infrastructure enables data exchange: Lakewatch could
consume application risk scores for incident triage, and the framework
could ingest Lakewatch’s runtime detections as a finding source.

#### Comparative Analysis and Research Gap

<a href="#tab:related-work-comparison" data-reference-type="autoref"
data-reference="tab:related-work-comparison">[tab:related-work-comparison]</a>
compares the surveyed approaches against criteria from the preceding
analysis.

<div id="tab:related-work-comparison">

| **Criterion**            | **ASPM** | **Platform native** | **DefectDojo** | **Lakewatch** | **This thesis** |
|:-------------------------|:--------:|:-------------------:|:--------------:|:-------------:|:---------------:|
| Open source              |    –     |          –          |      Yes       |       –       |       Yes       |
| Vendor agnostic model    |    –     |          –          |    Partial     |       –       |       Yes       |
| Extensible connectors    |    –     |          –          |      Yes       |    Partial    |       Yes       |
| Lakehouse architecture   |    –     |          –          |       –        |      Yes      |       Yes       |
| OLAP + OLTP serving      |    –     |          –          |       –        |       –       |       Yes       |
| Data quality enforcement |    –     |          –          |       –        |       –       |       Yes       |
| AppSec specific model    |   Yes    |       Partial       |      Yes       |       –       |       Yes       |
| Enterprise scalability   |   Yes    |       Partial       |       –        |      Yes      |       Yes       |

Comparison of Existing Approaches

</div>

*Note.* Yes indicates full support, Partial indicates acknowledged but
not demonstrated, – indicates out of scope or not addressed. Source:
author synthesis of cited products’ public documentation, accessed
2026-04.

No existing approach satisfies all criteria. Commercial
<span acronym-label="aspm" acronym-form="singular+short">aspm</span> is
proprietary. Platform native aggregations are ecosystem locked.
DefectDojo lacks the data architecture for enterprise scale analytics.
Lakewatch addresses runtime operations rather than application security
posture. Academic work on application security consolidation as a data
engineering problem is limited, focusing on detection techniques rather
than cross tool integration at scale.

### Selected Sources

The reference implementation in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> instantiates
the framework against nine source systems chosen to cover the ingestion
and integration patterns the framework must support, while keeping the
sample tractable. The selection spans all three detection tiers: static
testing, dynamic testing, and runtime security.

#### Selection Criteria

The nine sources are selected against five criteria:

1.  **Open source or free tier available.** The reference implementation
    must be reproducible without commercial licenses.

2.  **Full domain coverage across three detection tiers.** The nine
    together must cover every domain in the framework:
    <span acronym-label="cmdb"
    acronym-form="singular+short">cmdb</span>, <span acronym-label="scm"
    acronym-form="singular+short">scm</span>, and the three detection
    tiers, namely static testing (<span acronym-label="sast"
    acronym-form="singular+short">sast</span>, <span acronym-label="sca"
    acronym-form="singular+short">sca</span>, secrets), dynamic testing
    (<span acronym-label="dast"
    acronym-form="singular+short">dast</span>), and runtime security
    (<span acronym-label="waf"
    acronym-form="singular+short">waf</span>).

3.  **<span acronym-label="api" acronym-form="singular+short">api</span>
    heterogeneity.** The selection deliberately includes
    <span acronym-label="rest" acronym-form="singular+short">rest</span>
    (ServiceNow, SonarQube, Dependency-Track, GitHub, GitLab, OWASP ZAP,
    AWS WAF), GraphQL (GitHub, GitLab), and <span acronym-label="cli"
    acronym-form="singular+short">cli</span> wrapped (Semgrep,
    TruffleHog) sources so the connector contract is exercised across
    integration styles.

4.  **Heterogeneity bound at nine for scope control.** The nine sources
    cover the ingestion and integration patterns the framework must
    support. A wider sample would dilute pattern coverage without
    strengthening the framework claim.

5.  **Industry adoption.** Each tool is in widespread enterprise use.

Incremental strategy heterogeneity across the Selected Nine is
summarized in
<a href="#tab:incremental-strategies" data-reference-type="autoref"
data-reference="tab:incremental-strategies">[tab:incremental-strategies]</a>.

<div id="tab:incremental-strategies">

| **Source**                                 | **Incremental strategy**                                                  |
|:-------------------------------------------|:--------------------------------------------------------------------------|
| ServiceNow                                 | Native                                                                    |
| SonarQube, Semgrep Cloud, Dependency-Track | Native high water mark column (SonarQube                                  |
| GitHub, GitLab                             | Webhook                                                                   |
| Semgrep Docker, TruffleHog                 | Commit <span acronym-label="sha" acronym-form="singular+short">sha</span> |
| OWASP ZAP                                  | Scan lifecycle retrieval                                                  |
| AWS WAF                                    | Event time windowed sampled retrieval                                     |

Pairings of source and incremental strategy

</div>

*Note.* Classification synthesized from the medallion pattern treatment
in and the Lakeflow Declarative Pipelines operations guidance in .
Pairings of source and strategy are author attributions based on the API
capability matrix per source.

#### The Selected Nine

- **ServiceNow**: <span acronym-label="cmdb"
  acronym-form="singular+short">cmdb</span>. Dominant enterprise
  <span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
  with a free developer instance, <span acronym-label="rest"
  acronym-form="singular+short">rest</span> Table and CMDB Instance
  <span acronym-label="api" acronym-form="plural+short">apis</span>, and
  native <span class="mark">sys_updated_on</span> high water mark.

- **GitHub**: <span acronym-label="scm"
  acronym-form="singular+short">scm</span> plus
  <span acronym-label="sast" acronym-form="singular+short">sast</span>,
  <span acronym-label="sca" acronym-form="singular+short">sca</span>,
  and secrets scanning integrated into the platform.
  <span acronym-label="rest" acronym-form="singular+short">rest</span>
  and GraphQL <span acronym-label="api"
  acronym-form="plural+short">apis</span>, rich webhook coverage, cursor
  pagination.

- **GitLab**: <span acronym-label="scm"
  acronym-form="singular+short">scm</span> plus security integrated into
  the platform. <span acronym-label="rest"
  acronym-form="singular+short">rest</span> and GraphQL
  <span acronym-label="api" acronym-form="plural+short">apis</span>,
  keyset and offset pagination, webhook coverage. Security findings
  require Ultimate tier or pipeline artifacts.

- **SonarQube**: <span acronym-label="sast"
  acronym-form="singular+short">sast</span> (static testing). Mature
  server product with a <span acronym-label="rest"
  acronym-form="singular+short">rest</span> Web
  <span acronym-label="api" acronym-form="singular+short">api</span>,
  well documented severity scale, <span class="mark">updateDate</span>
  high water mark, and a scan completion webhook that complements
  scheduled polling.

- **Semgrep**: <span acronym-label="sast"
  acronym-form="singular+short">sast</span> (static testing). Modern
  engine with both a <span acronym-label="cli"
  acronym-form="singular+short">cli</span> deployment
  (<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
  embedded) and a hosted Cloud Platform <span acronym-label="api"
  acronym-form="singular+short">api</span>. Exercises the dual
  <span acronym-label="cli" acronym-form="singular+short">cli</span>
  artifact and server <span acronym-label="api"
  acronym-form="singular+short">api</span> ingestion pattern.

- **Dependency-Track**: <span acronym-label="sca"
  acronym-form="singular+short">sca</span> (static testing).
  <span acronym-label="owasp" acronym-form="singular+short">owasp</span>
  project with a <span acronym-label="rest"
  acronym-form="singular+short">rest</span> <span acronym-label="api"
  acronym-form="singular+short">api</span>, <span acronym-label="sbom"
  acronym-form="singular+short">sbom</span> centric (CycloneDX, SPDX)
  vulnerability correlation across multiple advisory sources.

- **TruffleHog**: secrets (static testing). <span acronym-label="cli"
  acronym-form="singular+short">cli</span> tool with no server
  <span acronym-label="api" acronym-form="singular+short">api</span>,
  distinguished by live credential verification that populates the
  canonical <span class="mark">validity_status</span> field.

- **OWASP ZAP**: <span acronym-label="dast"
  acronym-form="singular+short">dast</span> (dynamic testing). Open
  source dynamic scanner operated as a long running daemon with a
  <span acronym-label="rest" acronym-form="singular+short">rest</span>
  <span acronym-label="api" acronym-form="singular+short">api</span> 
  for scan orchestration and alert retrieval. <span acronym-label="url"
  acronym-form="singular+short">url</span> based findings represent the
  dynamic testing tier and exercise the on demand scan lifecycle
  integration pattern.

- **AWS WAF**: <span acronym-label="waf"
  acronym-form="singular+short">waf</span> (runtime security). Managed
  web application firewall exposing matched request samples through the
  <span class="mark">GetSampledRequests</span> <span acronym-label="api"
  acronym-form="singular+short">api</span> , with full event logs
  available via CloudWatch. Event based findings linked to workloads by
  <span acronym-label="arn" acronym-form="singular+short">arn</span> and
  tag represent the runtime security tier and exercise the time window
  sampled retrieval pattern.

Details for each of the selected nine sources are on the [connectors
reference hub](https://vkraus.github.io/appsec-docs/connectors/). Other
tools named in this survey do not have dedicated reference pages.

#### Considered and Excluded

<a href="#tab:considered-excluded" data-reference-type="autoref"
data-reference="tab:considered-excluded">[tab:considered-excluded]</a>
enumerates the principal tools that were considered and the criterion
that excluded each. Tools marked **within scope, deferred** pass all
criteria but sit outside the cap in Criterion 4. Onboarding them is a
repeat of the procedure per source in
<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a>.

<div id="tab:considered-excluded">

| **Tool**        | **Category**                                                                                                                              | **Excl. by** | **Note**                                                                                                                   |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------|:-------------|:---------------------------------------------------------------------------------------------------------------------------|
| Checkmarx       | <span acronym-label="sast" acronym-form="singular+short">sast</span>                                                                      | C1           | commercial only, no permissive tier                                                                                        |
| Fortify         | <span acronym-label="sast" acronym-form="singular+short">sast</span>                                                                      | C1           | commercial, OpenText                                                                                                       |
| Burp Enterprise | <span acronym-label="dast" acronym-form="singular+short">dast</span>                                                                      | C1           | commercial. Community edition is manual only                                                                               |
| Snyk            | <span acronym-label="sca" acronym-form="singular+short">sca</span> / <span acronym-label="sast" acronym-form="singular+short">sast</span> | C4           | **within scope, deferred** (overlap with Dependency-Track and Semgrep)                                                     |
| GitGuardian     | secrets                                                                                                                                   | C4           | **within scope, deferred** (overlap with TruffleHog)                                                                       |
| GitLeaks        | secrets                                                                                                                                   | C4           | **within scope, deferred** (overlap with TruffleHog)                                                                       |
| Dependabot      | <span acronym-label="sca" acronym-form="singular+short">sca</span>                                                                        | C4           | **within scope, deferred**. GitHub native, overlap with Dependency-Track                                                   |
| Jira            | issue tracker                                                                                                                             | C2           | issue tracking is out of the <span acronym-label="aspm" acronym-form="singular+short">aspm</span> data scope               |
| Azure DevOps    | <span acronym-label="scm" acronym-form="singular+short">scm</span> / <span acronym-label="cicd" acronym-form="singular+short">cicd</span> | C4           | **within scope, deferred** (overlap with GitHub and GitLab)                                                                |
| Bitbucket Cloud | <span acronym-label="scm" acronym-form="singular+short">scm</span>                                                                        | C4           | **within scope, deferred**                                                                                                 |
| Jenkins         | <span acronym-label="cicd" acronym-form="singular+short">cicd</span>                                                                      | C2           | CI orchestrator, does not produce <span acronym-label="aspm" acronym-form="singular+short">aspm</span> findings on its own |
| GitHub Actions  | <span acronym-label="cicd" acronym-form="singular+short">cicd</span>                                                                      | C4           | **within scope, deferred**                                                                                                 |
| Cloudflare WAF  | <span acronym-label="waf" acronym-form="singular+short">waf</span>                                                                        | C4           | **within scope, deferred** (overlap with AWS WAF)                                                                          |
| Akamai WAF      | <span acronym-label="waf" acronym-form="singular+short">waf</span>                                                                        | C1           | commercial, no free tier                                                                                                   |

Considered and excluded sources. Each row names the tool, the category
it would have populated, and the criterion that excluded it (C1 open
source or free tier, C2 full domain coverage, C3
<span acronym-label="api" acronym-form="singular+short">api</span>
heterogeneity, C4 heterogeneity cap, C5 industry adoption).

</div>

#### Cross Source Synthesis

Across the nine sources, four patterns recur: ticket like, resource
like, finding like, and event like. Severity scales span three to six
levels with overlapping but not identical vocabularies. Status
vocabularies diverge more sharply, with scanner specific states that
rarely map one to one with a common lifecycle. Five pagination
strategies appear: offset (ServiceNow, SonarQube, Dependency-Track),
cursor (GitHub <span acronym-label="rest"
acronym-form="singular+short">rest</span>, Semgrep Cloud), GraphQL
cursor (GitHub and GitLab GraphQL), keyset (GitLab
<span acronym-label="rest" acronym-form="singular+short">rest</span>),
and none (<span acronym-label="cli"
acronym-form="singular+short">cli</span> based sources, AWS WAF sampled
requests). The sources also split on an **operational pattern** axis.
Periodic global scanners (SonarQube, Dependency-Track, Semgrep Cloud)
are polled via <span class="mark">updated_at</span> cursors.
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
step scanners (Semgrep Docker, TruffleHog) run per commit and are
indexed by commit <span acronym-label="sha"
acronym-form="singular+short">sha</span>. On demand dynamic scanners
(OWASP ZAP) are read via the scan lifecycle <span acronym-label="api"
acronym-form="singular+short">api</span>. Runtime telemetry sources (AWS
WAF) are sampled over time windows. Together these exercise all five
ingestion strategies the framework prescribes.

The [source capability matrix reference
page](https://vkraus.github.io/appsec-docs/platform/reference/source-capability-matrix/)
tabulates the nine sources against the capabilities that matter for
connector design. This matrix drives the derivations in
<a href="#sec:data-model" data-reference-type="autoref"
data-reference="sec:data-model">[sec:data-model]</a>: the Silver Entity
and Silver Finding patterns must accommodate sources varying across
every column, and the connector framework rules in
<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>
must commit to defaults that work uniformly.

This thesis fills the gap with a vendor agnostic framework for
application security data. It applies lakehouse architecture and the
medallion pattern to ingest tool output, normalize it into a domain
model, and serve it through <span acronym-label="olap"
acronym-form="singular+short">olap</span> and <span acronym-label="oltp"
acronym-form="singular+short">oltp</span> interfaces. A new source needs
only a connector module.
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> presents the framework,
and <a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> demonstrates
its implementation.

## Framework

<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> analyzed the sources,
patterns, and gaps in enterprise application security data integration.
This chapter presents the proposed framework: a reusable blueprint
defining the architecture, data model, and patterns an organization
follows to build its own implementation. The framework targets the
Databricks Lakehouse, separating general patterns from platform
specifics. <a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> then
demonstrates a concrete implementation.

### Solution Architecture

This section presents the framework architecture at three levels:
technology stack, component design, and data layer. The architecture
addresses the requirements from domain analysis: heterogeneous source
ingestion, vendor agnostic normalization, dual
<span acronym-label="olap"
acronym-form="singular+short">olap</span>/<span acronym-label="oltp"
acronym-form="singular+short">oltp</span> data serving, and
extensibility for new data sources and analytics.

A further design principle applies to the framework artifacts: every
template defined in this chapter (schema patterns, mappings, connector
contract) is declarative rather than procedural, so that an
<span acronym-label="ai" acronym-form="singular+short">ai</span> coding
agent reading the specification has enough material to produce a
candidate implementation. The published skill catalog, which sits on the
external specification site and wraps these templates into executable
prompts, is evaluated separately in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>.

#### Technology Stack

The framework targets the Databricks platform on
<span acronym-label="aws" acronym-form="singular+short">aws</span>.
Databricks separates storage from compute: data resides in object
storage and compute scales independently. This reduces costs for uneven
workloads typical for security data integration .

##### Delta Lake

Delta Lake is an open table format that adds <span acronym-label="acid"
acronym-form="singular+short">acid</span> transactions, schema
enforcement, and time travel to cloud object storage . It provides the
storage layer for all three medallion tiers. Schema evolution lets
bronze tables absorb new source fields without pipeline changes. Time
travel enables auditing and rollback, critical for a security data
platform where data integrity and reproducibility are essential. showed
that lakehouse combines warehouse governance with data lake flexibility.

##### Unity Catalog

Unity Catalog provides unified data governance across the lakehouse . It
manages a three level namespace (
<span class="mark">catalog.schema.table</span> ) that maps to the
medallion layer organization: one catalog per environment, schemas for
each source (bronze) and each domain (silver, gold). Fine grained access
control enforces least privilege access to security data, which often
contains sensitive vulnerability details. Automated lineage tracking
records data flow from source through transformations to consumption,
supporting auditability. Column level tags classify sensitive fields
such as <span acronym-label="cve"
acronym-form="singular+short">cve</span> descriptions and remediation
guidance.

##### Lakeflow Declarative Pipelines

<span acronym-label="ldp" acronym-form="singular+short">ldp</span> is
the pipeline framework for batch and streaming transformations .
Pipelines are declared as Python or <span acronym-label="sql"
acronym-form="singular+short">sql</span> functions with explicit
dependencies. The framework resolves execution order automatically. Data
quality expectations are embedded directly in pipeline definitions as
declarative constraints (e.g. “severity must be critical, high, medium,
or low”). Records which violate expectations are quarantined and the
pipeline keeps running. This follows the quarantine pattern from
<a href="#sec:data-integration-patterns" data-reference-type="autoref"
data-reference="sec:data-integration-patterns">[sec:data-integration-patterns]</a>.
<span acronym-label="ldp" acronym-form="singular+short">ldp</span>
handles incremental processing natively through change data feed,
reducing the cost of reprocessing for large datasets.

##### Lakebase

Lakebase is a serverless PostgreSQL database that provides the
<span acronym-label="oltp" acronym-form="singular+short">oltp</span>
serving layer . It shares the underlying storage layer with the
lakehouse, exposing gold layer tables as <span acronym-label="oltp"
acronym-form="singular+short">oltp</span> queryable without data
duplication. This satisfies the dual serving requirement from
<a href="#sec:data-architecture" data-reference-type="autoref"
data-reference="sec:data-architecture">[sec:data-architecture]</a>:
<span acronym-label="olap" acronym-form="singular+short">olap</span>
queries go through <span acronym-label="sql"
acronym-form="singular+short">sql</span> warehouses for dashboards, and
<span acronym-label="oltp" acronym-form="singular+short">oltp</span>
queries go through Lakebase for issue tracker integration, state
lookups, and serving <span acronym-label="api"
acronym-form="singular+short">api</span>. Lakebase scales to zero,
reducing cost for workload spikes. Instant database branching creates
isolated copies for development and testing without duplicating data.

##### Platform Synergies

Running all components on a single platform provides governance,
lineage, and compute benefits that would require significant integration
effort across disparate tools. Unity Catalog governs access uniformly
across bronze, silver, and gold. The shared compute and storage model
eliminates data movement between analytical and operational stores.

The platform also enables integration with Lakewatch, the Databricks
<span acronym-label="siem" acronym-form="singular+short">siem</span>
analyzed in <a href="#sec:lakewatch" data-reference-type="autoref"
data-reference="sec:lakewatch">[sec:lakewatch]</a>. Both systems share
Delta Lake storage and Unity Catalog governance. The gold layer outputs
of the framework (application risk scores, remediation status) can serve
as enrichment signals for Lakewatch threat detection, while Lakewatch
runtime security events could feed back as an additional finding source.
This lines up with the finding in
<a href="#sec:lakewatch" data-reference-type="autoref"
data-reference="sec:lakewatch">[sec:lakewatch]</a>.

#### Component Design

The framework is organized into five tiers, illustrated in
<a href="#fig:component-design" data-reference-type="autoref"
data-reference="fig:component-design">[fig:component-design]</a>. Data
flows from top to bottom, i.e. from sources through the platform to
consumers.

<figure id="fig:component-design">

<figcaption>Component Design</figcaption>
</figure>

**Data sources** are the external systems analyzed in
<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a>: application inventories,
<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms, <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> tools, security scanners, and
vulnerability databases. They are outside the framework boundary. The
framework consumes their <span acronym-label="api"
acronym-form="plural+short">apis</span> but does not control them.

**Ingestion tier** contains connectors that extract data from sources
and store it in the bronze layer. Three connector categories serve
different integration scenarios. Lakeflow Connect uses a declarative
managed ingestion pattern. <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> connectors use source provided
client libraries for programmatic extraction. <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> connectors use the open source
<span acronym-label="dltool" acronym-form="singular+short">dltool</span>
library for sources which lack Lakeflow Connect or dedicated
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>. All
connectors share common concerns: authentication, pagination, rate
limiting, and incremental state. The connector framework in
<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>
defines these patterns.

**Processing tier** implements the medallion architecture
(<a href="#sec:medallion-arch" data-reference-type="autoref"
data-reference="sec:medallion-arch">[sec:medallion-arch]</a>). Delta
Lake provides the storage layer. <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> orchestrates the
transformations. Bronze stores raw ingested data in source native
schemas. Silver normalizes it into the vendor agnostic entity and
finding model defined in
<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a>. Gold
computes aggregated metrics, <span acronym-label="ml"
acronym-form="singular+short">ml</span> enriched scores, and consumption
ready datasets. Unity Catalog governs access and tracks lineage across
all three layers.

**Serving tier** exposes processed data to downstream consumers.
<span acronym-label="sql" acronym-form="singular+short">sql</span>
warehouses serve <span acronym-label="olap"
acronym-form="singular+short">olap</span> queries for dashboards and
analytics. Lakebase serves <span acronym-label="oltp"
acronym-form="singular+short">oltp</span> workloads: low latency lookups
and operational <span acronym-label="api"
acronym-form="plural+short">apis</span>. A <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> layer provides
<span acronym-label="http" acronym-form="singular+short">http</span>
access to the <span acronym-label="oltp"
acronym-form="singular+short">oltp</span> store.

**Data consumers** are external systems reading from the serving tier:
issue trackers (Jira, ServiceNow), <span acronym-label="siem"
acronym-form="singular+short">siem</span>/<span acronym-label="soar"
acronym-form="singular+short">soar</span> platforms, and custom
reporting tools. Like data sources, consumers are outside the framework
boundary.

#### Medallion Architecture

The processing tier applies the medallion architecture pattern from
<a href="#sec:data-architecture" data-reference-type="autoref"
data-reference="sec:data-architecture">[sec:data-architecture]</a>. Each
layer is a Delta Lake schema within a single Unity Catalog, providing
unified governance and cross layer lineage.
<a href="#fig:medallion-design" data-reference-type="autoref"
data-reference="fig:medallion-design">[fig:medallion-design]</a>
illustrates the layer structure and transformations between them.

<figure id="fig:medallion-design">

<figcaption>Medallion Layer Design</figcaption>
</figure>

##### Bronze Layer

The bronze layer stores raw data from each source with minimal
transformation. Each connector writes to its own schema (e.g.,
<span class="mark">github</span> , <span class="mark">servicenow</span>
, <span class="mark">sonarqube</span> ), preserving the native source
structure. Records are appended with standard metadata columns:
ingestion timestamp, source system identifier, and batch identifier. No
business logic is applied. The goal is an exact, auditable copy of
source data.

Bronze tables use schema on read. New fields from source
<span acronym-label="api" acronym-form="singular+short">api</span>
changes are accepted through additive schema evolution without breaking
pipelines. Partitioning by ingestion date enables efficient time range
queries. Records failing structural validation at ingestion (malformed
<span acronym-label="json" acronym-form="singular+short">json</span>,
missing required fields) are routed to quarantine tables per source with
diagnostic metadata.

##### Silver Layer

The silver layer is the system of record. Silver transformations
normalize heterogeneous source data into the vendor agnostic domain
model from <a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a>. Three table
categories make up this layer:

- **Entity tables** store normalized dimension data: applications,
  repositories, teams, commits, pull requests, pipeline runs,
  dependencies, and branch protection policies. Each entity table uses a
  surrogate key, a natural key from the source system, and
  <span class="mark">valid_from</span> /
  <span class="mark">valid_to</span> timestamps for change tracking.

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

- **Relationship tables** store many to many mappings from application
  to repository, from finding to <span acronym-label="cve"
  acronym-form="singular+short">cve</span>, and cross tool deduplication
  links.

The silver layer applies the data quality patterns from
<a href="#sec:data-integration-patterns" data-reference-type="autoref"
data-reference="sec:data-integration-patterns">[sec:data-integration-patterns]</a>:
severity harmonization, entity normalization, timestamp standardization,
and deduplication. <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> expectations enforce
constraints declaratively. Records which violate expectations go to
quarantine.

##### Gold Layer

The gold layer computes consumption ready datasets from silver data. Two
categories of gold tables serve distinct purposes:

- **Aggregation tables** compute metrics at defined levels: application
  risk scores, team remediation rates, <span acronym-label="mttr"
  acronym-form="singular+short">mttr</span> by severity,
  <span acronym-label="sla" acronym-form="singular+short">sla</span>
  compliance percentages, and time series trends. These tables power the
  dashboards and executive reports consumed through the
  <span acronym-label="olap" acronym-form="singular+short">olap</span>
  serving path.

- **<span acronym-label="ml" acronym-form="singular+short">ml</span>
  enriched tables** store model outputs: composite risk scores, false
  positive predictions, and remediation time estimates. These scores
  augment the aggregation tables with predictive signals. The
  <span acronym-label="ml" acronym-form="singular+short">ml</span>
  workflow patterns are detailed in
  <a href="#sec:analytics-patterns" data-reference-type="autoref"
  data-reference="sec:analytics-patterns">[sec:analytics-patterns]</a>.

Gold tables use incremental refresh where possible: new silver records
trigger recomputation of only the affected aggregations. Full refresh is
meant for metrics requiring global recomputation, such as cross
application percentiles.

### Data Model

This section maps the conceptual domain model from
<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a> to physical
table designs across the three medallion layers. Reusable schema
patterns are applied to produce the concrete entity, finding, and
aggregation tables that the framework provides.

#### Source Synthesis

The schema patterns are derived from the <span acronym-label="api"
acronym-form="plural+short">apis</span> of the nine sources introduced
in <a href="#sec:selected-sources" data-reference-type="autoref"
data-reference="sec:selected-sources">[sec:selected-sources]</a>, not
chosen in advance. The [per category capability
matrix](https://vkraus.github.io/appsec-docs/platform/reference/source-capability-matrix/)
consolidates the observations relevant to schema design at the category
level. The [connectors reference
hub](https://vkraus.github.io/appsec-docs/connectors/) provides facts
for each source. This section maps the consolidated capabilities onto
concrete Entity, Finding, and Relationship schemas.

#### Schema Patterns

Schema patterns are reusable templates that standardize how tables are
created at each medallion layer. They ensure consistency and prepare the
model for new entities or sources. Four patterns cover the framework
needs. <a href="#fig:record-lifecycle" data-reference-type="autoref"
data-reference="fig:record-lifecycle">[fig:record-lifecycle]</a> walks a
single SonarQube <span acronym-label="sast"
acronym-form="singular+short">sast</span> finding through the four
layers that the subsections below define, and concretizes the metadata
envelope that
<a href="#sec:bronze-pattern" data-reference-type="autoref"
data-reference="sec:bronze-pattern">[sec:bronze-pattern]</a> prescribes.

<figure id="fig:record-lifecycle">

<figcaption>Lifecycle of a single SonarQube <span
data-acronym-label="sast" data-acronym-form="singular+short">sast</span>
finding from API response through Bronze ingestion with the metadata
envelope with five columns, Silver normalization into <span><span>
<mark>silver.findings</mark> </span></span> with category discriminator,
and Gold aggregation into <span><span> <mark>app_risk_scores</mark>
</span></span> . The same logical record appears in each medallion layer
with additional metadata and normalized fields added at each
transition.</figcaption>
</figure>

##### Bronze pattern

Every bronze table carries a uniform metadata envelope: four columns
shared across connectors (
<span class="mark">\_ingestion_timestamp</span> ,
<span class="mark">\_source_system</span> ,
<span class="mark">\_batch_id</span> ,
<span class="mark">\_raw_payload</span> ) and a fifth (
<span class="mark">\_hwm_value</span> ) on incremental only tables (see
<a href="#sec:ingestion-patterns" data-reference-type="autoref"
data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>).
For connectors whose bronze schema is framework owned (artifact path
sources such as OWASP ZAP and Semgrep), the
<span class="mark">src/common/bronze_schema.py</span> helper stamps the
envelope immediately before the write. For connectors whose bronze
schema is owned by an ingestion managed service (Lakeflow Connect, as in
the ServiceNow case), the envelope is published by a downstream SQL view
that projects the five columns on top of the managed table using the
ingestion service’s own run identifier and timestamp metadata. The net
contract is identical to downstream readers: every bronze row exposes
the same envelope columns regardless of which of the three ingestion
paths produced it.

Additional columns from the source native schema are included alongside
the raw payload via schema on read. New fields are accepted through
additive schema evolution. Tables are partitioned by ingestion date for
retention policies and efficient time range queries.

##### Silver entity pattern

Entity tables store normalized dimension data. The pattern is derived
from the entity emitting sources in the selection (ServiceNow
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
records, <span acronym-label="scm"
acronym-form="singular+short">scm</span> repositories and commits, team
references). The field derivation table per source is published
externally at
<https://vkraus.github.io/appsec-docs/platform/reference/canonical-mapping/#silver-entity-mapping-requirements>,
showing how each target field unions over the native fields these
sources expose.

The natural key plus source system uniquely identifies a record origin.
The surrogate key provides a stable reference for foreign keys even when
source identifiers change.

##### Quarantine scope

The transformation from Bronze to Silver for entity tables quarantines
records under three conditions. First, records failing
<span acronym-label="json" acronym-form="singular+short">json</span>
parse at Bronze landing. Second, records failing required field null
checks at the Bronze to Silver step (
<span class="mark">natural_key</span> ,
<span class="mark">source_system</span> ,
<span class="mark">valid_from</span> ). Third, records where a mandatory
lookup (for example, severity or status for finding related joins)
yields no match. Optional field nulls and type casts with safe fallbacks
are accepted with a data quality warning logged to the pipeline event
table but are not quarantined. This rule applies uniformly to finding
tables in <a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>.

##### CMDB relationship resolution

The ServiceNow <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> exposes
inter-<span acronym-label="ci" acronym-form="singular+short">ci</span>
relationships through a separate <span class="mark">cmdb_rel_ci</span>
table and reference fields on the <span acronym-label="ci"
acronym-form="plural+short">cis</span> themselves. Related
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
tables ( <span class="mark">cmdb_rel_ci</span> , referenced group and
user tables) are ingested as separate Bronze tables and joined in Silver
rather than resolved at ingestion via relationship
<span acronym-label="api" acronym-form="plural+short">apis</span>. This
keeps <span class="mark">ingest.py</span> stateless (it does not follow
<span acronym-label="api" acronym-form="singular+short">api</span>
links), makes relationship logic testable without
<span acronym-label="api" acronym-form="singular+short">api</span>
mocks, and localizes <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> schema changes to the
transformation layer.

##### Silver finding pattern

The single Silver Finding table (
<span class="mark">silver.findings</span> , whose design rationale
appears in
<a href="#sec:silver-findings-design" data-reference-type="autoref"
data-reference="sec:silver-findings-design">[sec:silver-findings-design]</a>)
stores normalized fact data for all finding categories. The pattern is
derived from the four finding emitting sources (SonarQube, Semgrep,
Dependency-Track, TruffleHog) plus the scanners integrated into the
platform on GitHub and GitLab. The derivation tables per source for code
level and package/platform sources are published externally at
<https://vkraus.github.io/appsec-docs/platform/reference/canonical-mapping/#silver-finding-mapping-requirements>.
Each target field unions over the native fields of these sources and
inapplicable fields are marked “N/A”.

Standard fields marked “N/A” for a source are stored as
<span class="mark">NULL</span> in records from that source. This is the
union over sources behavior. The <span class="mark">mapping.yml</span>
per source
(<a href="#sec:transformation-patterns" data-reference-type="autoref"
data-reference="sec:transformation-patterns">[sec:transformation-patterns]</a>)
makes each mapping explicit, including the
<span class="mark">category</span> discriminator for each record.

##### Deduplication pattern

When multiple tools scan the same artifact, overlapping findings must be
identified and linked rather than collapsed. Deduplication is applied
within <span class="mark">silver.findings</span> using a category
conditional exact match tuple selected by the
<span class="mark">category</span> value of each record:

- <span acronym-label="sast" acronym-form="singular+short">sast</span>
  findings ( <span class="mark">category = ’sast’</span> ):
  <span class="mark">(repository_id, file_path, rule_id,
  line_number)</span> . A match across two <span acronym-label="sast"
  acronym-form="singular+short">sast</span> tools links the two findings
  via a <span class="mark">dedup_links</span> relationship record.

- <span acronym-label="sca" acronym-form="singular+short">sca</span>
  findings ( <span class="mark">category = ’sca’</span> ):
  <span class="mark">(repository_id, package_name, cve_id)</span> . Two
  <span acronym-label="sca" acronym-form="singular+short">sca</span>
  tools reporting the same <span acronym-label="cve"
  acronym-form="singular+short">cve</span> on the same package are
  duplicates.

- Secret findings ( <span class="mark">category = ’secret’</span> ):
  <span class="mark">(repository_id, commit_sha, secret_type,
  file_path)</span> . Secrets emitted per commit are deliberately
  retained per commit rather than collapsed by secret value.

No fuzzy matching is performed. If two tools diverge on line numbers
(for example, due to file preamble differences), both findings are
retained. They are grouped at Gold via a
<span class="mark">finding_group_id</span> clustering findings sharing
<span class="mark">(repository_id, file_path, rule_id)</span>
independent of line number.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> instantiates
this logic verbatim, without additional heuristics.

##### Relationship pattern

Relationship tables store many to many mappings between entities. Each
contains foreign keys to both sides, a source system indicator, and
<span class="mark">valid_from</span> /
<span class="mark">valid_to</span> timestamps tracking when the
relationship was active. No payload columns are included. The sole
purpose of the table is to link entities. Examples include mappings from
application to repository, from finding to <span acronym-label="cve"
acronym-form="singular+short">cve</span>, and cross tool deduplication
links.

##### Gold aggregation pattern

Aggregation tables follow a grain, metric, period structure:

- **Grain columns** define the level of detail: the entity key
  (application, team, repository) and time period (day, week, month).

- **Metric columns** store computed values: finding counts by severity,
  <span acronym-label="mttr" acronym-form="singular+short">mttr</span>,
  <span acronym-label="sla" acronym-form="singular+short">sla</span>
  compliance percentage, risk score.

- **Period columns** store the time window:
  <span class="mark">period_start</span> and
  <span class="mark">period_end</span> (<span acronym-label="utc"
  acronym-form="singular+short">utc</span>).

- **Refresh metadata**: <span class="mark">computed_at</span> timestamp
  and refresh strategy indicator (incremental or full).

This structure enables consistent querying across gold tables: filter by
grain, aggregate over periods, compare across entities.

#### Entity Model

The silver layer instantiates the schema patterns as concrete tables,
organized by category: entities (dimensions), findings (facts),
reference data, and relationships.

<a href="#fig:silver-erd" data-reference-type="autoref"
data-reference="fig:silver-erd">[fig:silver-erd]</a> presents a
representative subset that exercises every relationship type across the
four categories. The full table inventory follows in the subsections
below.

<figure id="fig:silver-erd">

<figcaption>Silver layer entity relationship diagram. Representative
subset: <strong>8</strong> of the <strong>15</strong> silver tables.
Four groupings are visible through background shading: entities,
findings, reference, and relationship tables. The remaining 7 tables
follow the same schema patterns.</figcaption>
</figure>

##### Entity Tables

<a href="#tab:entity-tables" data-reference-type="autoref"
data-reference="tab:entity-tables">[tab:entity-tables]</a> lists the
entity tables and their key domain specific columns. All tables include
the standard silver entity pattern columns (
<span class="mark">id</span> , <span class="mark">natural_key</span> ,
<span class="mark">source_system</span> ,
<span class="mark">valid_from</span> /
<span class="mark">valid_to</span> ).

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

##### Finding Table

All security findings land in a single Silver table,
<span class="mark">silver.findings</span> , distinguished by a
<span class="mark">category</span> discriminator column taking values
<span class="mark">sast</span> , <span class="mark">sca</span> ,
<span class="mark">secret</span> , <span class="mark">dast</span> ,
<span class="mark">container</span> , or <span class="mark">iac</span> .
Category specific attributes are carried as nullable columns, populated
only for records where the category defines them.
<a href="#tab:finding-columns" data-reference-type="autoref"
data-reference="tab:finding-columns">[tab:finding-columns]</a> lists the
category specific columns. Every finding references its repository
through <span class="mark">repository_id</span> . Business application
context is derived through relationship tables rather than stored
directly on findings, preserving the many to many mapping from
application to repository without duplicating finding records.

<div id="tab:finding-columns">

| **Category** | **Category specific columns**                                     |
|:-------------|:------------------------------------------------------------------|
| sast         | file_path, line_start, line_end, cwe_id, language                 |
| sca          | package_name, installed_version, fixed_version, cve_id, ecosystem |
| secret       | secret_type, file_path, commit_sha, validity_status               |
| dast         | url, http_method, parameter, attack_type                          |
| container    | image_name, image_tag, layer, cve_id                              |
| iac          | resource_type, resource_name, file_path, policy_id, benchmark     |

Category specific columns of <span class="mark">silver.findings</span> .
Each record populates the columns applicable to its
<span class="mark">category</span> . Unused columns are
<span class="mark">NULL</span> .

</div>

*Note.* Column list abstracted from the silver layer schema definition.
The full specification is on the [silver table ownership reference
page](https://vkraus.github.io/appsec-docs/platform/reference/silver-table-ownership/).

2.25ex 1ex .2ex 1ex .2ex Single table rationale The Silver Finding
mapping is already a union over sources. A physical split into
<span class="mark">silver.sast_findings</span> ,
<span class="mark">silver.sca_findings</span> , and so on would force
<span class="mark">UNION ALL</span> queries for cross category
analytics, fragment the per category dedup routing keyed on
<span class="mark">category</span> , and distort the category
partitioned requirement traceability matrix. Sparse nullable columns are
the accepted cost. At the target deployment scale, Delta Lake’s columnar
compression makes NULLs cheap. The full design rationale is on the
[single table findings rationale
page](https://vkraus.github.io/appsec-docs/platform/reference/single-silver-findings-rationale/).

##### Reference Tables

Reference tables store external intelligence used for enrichment:

- **vulnerabilities**: <span acronym-label="cve"
  acronym-form="singular+short">cve</span> records with description,
  published date, and <span acronym-label="cvss"
  acronym-form="singular+short">cvss</span> base score from the
  <span acronym-label="nvd" acronym-form="singular+short">nvd</span>.

- **epss_scores**: daily <span acronym-label="epss"
  acronym-form="singular+short">epss</span> probabilities per
  <span acronym-label="cve" acronym-form="singular+short">cve</span>,
  enabling time series analysis of exploitation likelihood.

- **kev_entries**: <span acronym-label="cisa"
  acronym-form="singular+short">cisa</span> <span acronym-label="kev"
  acronym-form="singular+short">kev</span> catalog entries indicating
  confirmed active exploitation, with the date added.

These tables are refreshed on schedule from their external sources.
Findings link to them through <span acronym-label="cve"
acronym-form="singular+short">cve</span> identifiers, forming the three
signal enrichment model described in
<a href="#sec:static-appsec" data-reference-type="autoref"
data-reference="sec:static-appsec">[sec:static-appsec]</a>.

##### Relationship Tables

Three relationship tables implement the key mappings identified in the
domain model:

- **app_repo_mapping**: links applications to repositories (many to
  many). This is the most critical relationship for business context
  attribution.

- **finding_cve_mapping**: links findings to <span acronym-label="cve"
  acronym-form="singular+short">cve</span> records, enabling
  vulnerability enrichment.

- **dedup_links**: links findings identified as duplicates across tools,
  preserving traceability to each source report while establishing a
  reference finding.

Silver tables and connectors do not line up one to one. Each table can
be fed by multiple connectors and each connector feeds multiple tables.
The full mapping is on the [silver table ownership reference
page](https://vkraus.github.io/appsec-docs/platform/reference/silver-table-ownership/),
which turns new source onboarding into a checklist of target tables.

##### Reference Implementation Scope

The fifteen table inventory above defines the full silver layer of the
framework. The reference implementation in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> realizes a
named subset sufficient to demonstrate every framework concept end to
end without carrying all fifteen tables into production:
<span class="mark">applications</span> and
<span class="mark">repositories</span> as entity tables,
<span class="mark">findings</span> as the fact table, and
<span class="mark">app_repo_mapping</span> as the critical relationship.
The remaining entity tables ( <span class="mark">teams</span> ,
<span class="mark">commits</span> ,
<span class="mark">pull_requests</span> ,
<span class="mark">pipeline_runs</span> ,
<span class="mark">dependencies</span> ,
<span class="mark">branch_policies</span> ), the reference tables (
<span class="mark">vulnerabilities</span> ,
<span class="mark">epss_scores</span> ,
<span class="mark">kev_entries</span> ), and the derived relationship
tables ( <span class="mark">finding_cve_mapping</span> ,
<span class="mark">dedup_links</span> ) follow the same schema patterns
and are left to follow on work in
<a href="#sec:future-work" data-reference-type="autoref"
data-reference="sec:future-work">[sec:future-work]</a>. The reference
implementation also realizes the silver entity columns as
<span acronym-label="scd" acronym-form="singular+short">scd</span>-1
(overwrite on update) rather than the <span acronym-label="scd"
acronym-form="singular+short">scd</span>-2 pattern (
<span class="mark">valid_from</span> /
<span class="mark">valid_to</span> ) documented for the framework, since
the <span acronym-label="mvp" acronym-form="singular+short">mvp</span>
scenarios do not exercise historical queries at a point in time.

#### Aggregation Model

The gold layer computes consumption ready metrics from silver data using
the aggregation pattern. Each gold table targets a specific stakeholder
need identified in
<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a>.

##### Application risk scores

The <span class="mark">app_risk_scores</span> table computes a composite
risk metric per application per period. Grain columns are
<span class="mark">application_id</span> and time period. Metrics
include: open finding counts by severity, weighted risk score (combining
severity, <span acronym-label="epss"
acronym-form="singular+short">epss</span> probability, and application
criticality tier), <span acronym-label="sla"
acronym-form="singular+short">sla</span> compliance percentage, and a
trend indicator (improving, stable, degrading). It serves application
owners who need a single view of the security posture for their
application.

##### Team metrics

The <span class="mark">team_metrics</span> table aggregates remediation
performance per team per period. Metrics include:
<span acronym-label="mttr" acronym-form="singular+short">mttr</span> by
severity, finding closure rate, new vs. resolved finding ratio, and
<span acronym-label="sla" acronym-form="singular+short">sla</span>
breach count. Leadership uses these metrics for cross team comparisons
and resource allocation decisions.

##### Vulnerability trends

The <span class="mark">vulnerability_trends</span> table provides time
series data at configurable intervals (daily, weekly, monthly). Metrics
include: new findings introduced, findings resolved, net open count,
severity distribution shifts, and mean age of open findings. These
trends power the longitudinal dashboards that track organizational
progress.

##### Coverage analysis

The <span class="mark">coverage_analysis</span> table identifies gaps in
security tool coverage. For each repository, it records which tool
categories have produced findings or scan records and which have not.
Missing coverage is flagged per category: a repository with no
<span acronym-label="sast" acronym-form="singular+short">sast</span>
findings and no <span acronym-label="sast"
acronym-form="singular+short">sast</span> pipeline runs likely lacks
static analysis integration. This lets security teams prioritize tooling
rollout.

##### Extension guide

Adding a new gold table follows a consistent process: define the grain
(entity and time period), specify the metrics, write a
<span acronym-label="ldp" acronym-form="singular+short">ldp</span>
transformation from silver to gold, and configure the refresh strategy.
The aggregation pattern ensures all gold tables share a common query
interface, so dashboards and reporting tools can consume new tables
without structural changes.

### Environment and Deployment

Before the components and data structures defined above can be populated
with connectors or analytics, the deployment environment must be
provisioned and the codebase organized. **This section assumes a working
Databricks environment.** Account onboarding, workspace creation,
networking, and <span acronym-label="iam"
acronym-form="singular+short">iam</span> federation are outside scope.
The scope of the framework begins at the workspace level and divides its
own deployment into two tiers: workspace scoped resources are
provisioned with Terraform, and application artifacts run inside the
workspace as Databricks Asset Bundles. The rest of this section covers
those two tiers, the project structure they organize, pipeline
orchestration, monitoring, and deployment level verification. These are
one time decisions that establish the platform. Repeatable patterns for
extending the framework follow in
<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>
and <a href="#sec:analytics-serving" data-reference-type="autoref"
data-reference="sec:analytics-serving">[sec:analytics-serving]</a>.

#### Deployment Strategy

The framework deploys in two tiers. The **workspace tier** provisions
workspace scoped resources with Terraform via the Databricks Terraform
provider : catalog creation (one per environment, per
<a href="#sec:tech-stack" data-reference-type="autoref"
data-reference="sec:tech-stack">[sec:tech-stack]</a>), cluster policies,
secret scopes for the source credentials in
<a href="#sec:selected-sources" data-reference-type="autoref"
data-reference="sec:selected-sources">[sec:selected-sources]</a>,
service principal identities, and coarse permission grants. A single
<span class="mark">workspace-bootstrap/</span> module captures the full
set, so one <span class="mark">terraform apply</span> recreates the
workspace state for a new environment or disaster recovery target. The
**application tier** deploys everything inside the provisioned
workspace. It uses Databricks Asset Bundles  as the deployment unit: a
single <span class="mark">databricks.yml</span> at the project root
declares jobs, <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> pipelines, notebooks,
permissions, and cluster attachments together with the source code that
implements them.

One bundle exists per target. Three targets structure the promotion
path: development, staging, and production. Each target overrides the
bundle parameters that differ between environments: the Unity Catalog
catalog name supplied by the workspace tier, the secret scope that
resolves <span acronym-label="api"
acronym-form="singular+short">api</span> credentials, and the compute
target for jobs and pipelines. Development uses smaller clusters and
relaxed permissions for rapid iteration. Staging mirrors production for
prerelease validation. Production enforces strict access controls and
scheduled execution. Because both the workspace module and the bundle
are declarative, the same promotion flow moves a change through the
three environments without hand editing any resource after the first
deployment. The framework prescribes only this two tier boundary.
Organizations that prefer Pulumi, OpenTofu, or direct Databricks
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span> calls
can substitute those at the workspace tier without changing the
application tier. DAB and the Databricks Terraform provider are selected
for the reference implementation because they are Databricks native and
integrate with the audit and lineage story of the platform.

#### Project Structure

The project follows a monorepo layout with four top level directories:
<span class="mark">src/</span> for pipeline source code,
<span class="mark">tests/</span> for the test suite,
<span class="mark">config/</span> for lookup tables, and the bundle
files at the root. The Unity Catalog layout mirrors the three medallion
layers from <a href="#sec:medallion-arch" data-reference-type="autoref"
data-reference="sec:medallion-arch">[sec:medallion-arch]</a>, with one
catalog per environment as established in
<a href="#sec:deployment-strategy" data-reference-type="autoref"
data-reference="sec:deployment-strategy">[sec:deployment-strategy]</a>:
<span class="mark">appsec_dev</span> ,
<span class="mark">appsec_staging</span> , and
<span class="mark">appsec_prod</span> . Within a catalog, source
specific bronze and silver tables live in schemas per source named
<span class="mark">bronze\_\<source\></span> and
<span class="mark">silver\_\<source\></span> (for example,
<span class="mark">bronze_github</span> and
<span class="mark">silver_servicenow</span> ). Cross source silver
tables (finding aggregation, cross entity joins, framework control
tables) live in an unqualified <span class="mark">silver</span> schema,
and gold analytics live in an unqualified <span class="mark">gold</span>
schema whose table names encode the analytic rather than a source. A
production ServiceNow business applications row therefore lives at
<span class="mark">appsec_prod.silver_servicenow.business_applications</span>
. The cross source finding aggregation lives at
<span class="mark">appsec_prod.silver.findings</span> . The app risk
score analytic lives at
<span class="mark">appsec_prod.gold.app_risk_scores</span> . Pipeline
names mirror their source module as
<span class="mark">ingest\_\<source\></span> and
<span class="mark">transform\_\<source\>\_silver</span> . Column names
use <span class="mark">snake_case</span> throughout. These conventions
let governance rules target tables and pipelines by name pattern rather
than by enumeration.

Every connector module under
<span class="mark">src/connectors/{source}/</span> carries the same four
artifacts, so adding a source amounts to filling in the blanks.
<span class="mark">ingest.py</span> implements the connector contract
from <a href="#sec:connector-abstraction" data-reference-type="autoref"
data-reference="sec:connector-abstraction">[sec:connector-abstraction]</a>
against the source <span acronym-label="api"
acronym-form="singular+short">api</span>.
<span class="mark">transform.py</span> maps bronze records to the target
silver entity or finding table. <span class="mark">mapping.yml</span>
declares the column expressions from bronze to silver and references the
severity and status lookups from
<a href="#sec:transformation-patterns" data-reference-type="autoref"
data-reference="sec:transformation-patterns">[sec:transformation-patterns]</a>.
<span class="mark">config.yml</span> records source specific parameters:
base <span acronym-label="url" acronym-form="singular+short">url</span>
and endpoints, pagination strategy, high water mark column, and target
bronze table. A colocated
<span class="mark">tests/connectors/{source}/</span> subfolder carries
the fixtures and assertions from
<a href="#sec:connector-testing" data-reference-type="autoref"
data-reference="sec:connector-testing">[sec:connector-testing]</a>.
Transformations from silver to gold are grouped by analytic rather than
by source, since a single gold table can consume data from multiple
connectors.

Configuration is split by sensitivity. Secrets such as
<span acronym-label="api" acronym-form="singular+short">api</span>
tokens and service account credentials are stored in the platform secret
scope and referenced by name in pipeline code, so they never appear in
source files or bundle configuration. Nonsensitive settings sit under
<span class="mark">config/</span> : severity lookups at
<span class="mark">config/severity/{source}.yml</span> and status
lookups at <span class="mark">config/status/{source}.yml</span> .
<span acronym-label="sla" acronym-form="singular+short">sla</span>
thresholds and scheduling intervals are out of scope for the
<span acronym-label="mvp" acronym-form="singular+short">mvp</span>
configuration. Tuning any of these values is a configuration change, not
a code change. The full layout with a worked example is on the [project
layout reference
page](https://vkraus.github.io/appsec-docs/platform/reference/project-layout/).

#### Pipeline Orchestration

Lakeflow Jobs schedules and coordinates pipeline execution . A job
groups related tasks into a <span acronym-label="dag"
acronym-form="singular+short">dag</span> with explicit dependencies. The
engine executes tasks in dependency order and handles retries on
failure. Jobs are defined in the bundle configuration alongside the
resources they operate on, making scheduling version controlled and
promotable via the deployment path from
<a href="#sec:deployment-strategy" data-reference-type="autoref"
data-reference="sec:deployment-strategy">[sec:deployment-strategy]</a>.

The framework assigns one job per connector. Each connector job contains
two sequential tasks: an ingestion task that extracts data from the
source <span acronym-label="api"
acronym-form="singular+short">api</span> into bronze, and a
transformation task that normalizes bronze records into silver. This
isolation gives each connector an independent failure domain: a GitHub
<span acronym-label="api" acronym-form="singular+short">api</span>
outage does not block ServiceNow ingestion. Gold layer analytics run as
separate jobs listing their upstream connector jobs as dependencies. The
scheduler starts a gold job only after all required silver data is
fresh. <span acronym-label="ml" acronym-form="singular+short">ml</span>
model retraining runs on independent schedules, decoupled from the
ingestion cycle.

Source characteristics drive scheduling frequency. High change sources
(<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms, security scanners with frequent new findings) run hourly.
Stable sources (application inventory from the
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>)
run daily. External enrichment sources follow their update cadences:
<span acronym-label="nvd" acronym-form="singular+short">nvd</span> and
<span acronym-label="epss" acronym-form="singular+short">epss</span>
update daily, <span acronym-label="cisa"
acronym-form="singular+short">cisa</span> <span acronym-label="kev"
acronym-form="singular+short">kev</span> updates on weekdays. Gold
analytics trigger after upstream connector jobs complete via explicit
dependencies. Where strict ordering adds unnecessary complexity (e.g.,
daily reporting), a schedule offset from the expected ingestion window
is acceptable.

Each task has a retry count and backoff interval for transient failures.
If retries exhaust, the task fails and downstream tasks in the same job
do not execute. Job level alerts notify operators of persistent failures
through configured channels (email, messaging webhooks). Since connector
jobs are independent, a single connector degradation does not cascade.
Jobs run in parallel on ephemeral clusters created at job start and
terminated at completion.

#### Monitoring and Observability

Scheduling handles when pipelines run. Monitoring handles whether they
are working over time. The platform provides system tables that record
job execution history, pipeline events, and compute utilization . The
framework builds on these to track three dimensions. **Data freshness**
compares the last successful ingestion timestamp on each bronze table
(and last transformation run on each silver table) against thresholds
derived from the scheduling frequency in
<a href="#sec:orchestration" data-reference-type="autoref"
data-reference="sec:orchestration">[sec:orchestration]</a>. An hourly
connector idle for two hours or a daily enrichment source idle for 36
hours flags as stale. **Pipeline health** aggregates job execution
metrics: success rate over a rolling window, mean run duration and its
trend, task level retry frequency, and quarantine volume. A rising
quarantine rate precedes data quality issues in silver. **Data quality
trends** track violations of <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> expectations over time. Alerts
fire at two levels. Job level alerts cover individual failures or
threshold breaches. System level alerts cover aggregate degradation such
as multiple connectors stale simultaneously or gold tables not refreshed
within their expected window. Thresholds and delivery channels (email,
messaging webhooks, incident management integrations) are defined as
configuration, so operators tune sensitivity without redeploying
pipelines.

#### Testing and Validation

Deployment level verification covers the environment and codebase.
Component level patterns live in
<a href="#sec:connector-testing" data-reference-type="autoref"
data-reference="sec:connector-testing">[sec:connector-testing]</a> and
<a href="#sec:analytics-testing" data-reference-type="autoref"
data-reference="sec:analytics-testing">[sec:analytics-testing]</a>.
Before deployment, the <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> pipeline enforces linting,
formatting, and unit tests over isolated helpers such as severity
mapping lookups, timestamp parsers, and schema mapping logic. After
deployment, smoke tests confirm Unity Catalog objects, compute
resources, secret scopes, and <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> pipelines exist with the
expected configuration. Failures block pipeline execution until
corrected.

The framework uses pytest markers to link tests to requirement
identifiers. Each test function carries a marker referencing a specific
requirement from the [requirement
catalog](https://vkraus.github.io/appsec-docs/platform/reference/catalog/),
such as
<span class="mark">@pytest.mark.requirement("REQ-TRF-SEV")</span> . A
traceability matrix is generated automatically from test results and
published at
<https://vkraus.github.io/appsec-docs/platform/reference/catalog/#per-source-traceability-matrix>,
applying uniformly across environment, connector
(<a href="#sec:connector-testing" data-reference-type="autoref"
data-reference="sec:connector-testing">[sec:connector-testing]</a>), and
analytics
(<a href="#sec:analytics-testing" data-reference-type="autoref"
data-reference="sec:analytics-testing">[sec:analytics-testing]</a>)
testing.

Four templates complete the framework. Environment and deployment
(above). Data model
(<a href="#sec:data-model" data-reference-type="autoref"
data-reference="sec:data-model">[sec:data-model]</a>). Connector
contract and job template
(<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>).
Analytics blueprint
(<a href="#sec:analytics-serving" data-reference-type="autoref"
data-reference="sec:analytics-serving">[sec:analytics-serving]</a>).
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> instantiates
each verbatim. The reference implementation contains no design decisions
beyond selecting which sources to onboard and which analytics to build.

### Connector Framework

The connector framework defines how data moves from the sources analyzed
in <a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> into the medallion layers
from <a href="#sec:medallion-arch" data-reference-type="autoref"
data-reference="sec:medallion-arch">[sec:medallion-arch]</a>.
<a href="#sec:component-design" data-reference-type="autoref"
data-reference="sec:component-design">[sec:component-design]</a>
introduced three connector categories (Lakeflow Connect,
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>, and
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span> with
<span acronym-label="dltool"
acronym-form="singular+short">dltool</span>). This section specifies the
common abstraction they share, the patterns for landing data in bronze,
and the patterns for transforming it to silver. The goal is a repeatable
recipe: adding a new source implements a well defined set of concerns
against a new <span acronym-label="api"
acronym-form="singular+short">api</span>, not a pipeline redesign.

<a href="#fig:data-plane-flow" data-reference-type="autoref"
data-reference="fig:data-plane-flow">[fig:data-plane-flow]</a> gives the
end to end view refined by the subsections below: ingest and transform
tasks along the spine, quarantine branches where validation can fail,
and the state and dedup annotations that the framework commits to.

<figure id="fig:data-plane-flow">

<figcaption>Data plane flow within the framework: ingestion with
auditable high water mark state (right), quarantine on the Bronze side
and on the Silver side for records that fail structural or required
field validation (left), SCD2 tracking on entity tables, and
materialization from Silver to Gold with cross tool
deduplication.</figcaption>
</figure>

#### Connector Abstraction

Every connector handles the same cross cutting concerns, but the three
categories from
<a href="#sec:component-design" data-reference-type="autoref"
data-reference="sec:component-design">[sec:component-design]</a> differ
in how much work the developer performs versus the platform or library.

##### Connector Categories

**Lakeflow Connect connectors** use the managed ingestion service of the
platform. They are declarative: configured through the bundle
definition, not coded. Authentication, pagination, incremental state,
and schema inference are handled by the platform. This suits sources
with supported Lakeflow Connect integrations where full table ingestion
meets requirements. The trade off is limited flexibility: custom
transformation logic, selective field extraction, and nonstandard
pagination cannot be injected. It ranks first in the preference order
because no connector code is written for any of the five cross cutting
concerns defined below. The concerns migrate off the connector. The
connector becomes a declaration that cannot drift from the framework
contract.

**<span acronym-label="sdk" acronym-form="singular+short">sdk</span>
connectors** use a source provided client library (e.g., the
<span acronym-label="aws" acronym-form="singular+short">aws</span>
<span acronym-label="sdk" acronym-form="singular+short">sdk</span> for
Python, PyGitHub, python-gitlab) for programmatic extraction. These
<span acronym-label="sdk" acronym-form="plural+short">sdks</span>
encapsulate authentication, pagination, rate limiting, and object model
mapping, letting the developer work with high level methods rather than
raw <span acronym-label="http" acronym-form="singular+short">http</span>
requests. This suits sources that offer an official
<span acronym-label="sdk" acronym-form="singular+short">sdk</span> with
good endpoint coverage. The developer controls extraction logic. The
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>
handles transport level concerns. It ranks second because when Lakeflow
Connect does not apply, the vendor <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> is the remaining option that
keeps transport, pagination, and rate limit logic in library code
maintained by parties closer to the source than the connector author. It
is typed against the source object model, so upstream
<span acronym-label="api" acronym-form="singular+short">api</span>
changes appear as library upgrades rather than silent breakage in a hand
written binding.

**<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span>
connectors with <span acronym-label="dltool"
acronym-form="singular+short">dltool</span>** use the open source
<span acronym-label="dltool" acronym-form="singular+short">dltool</span>
library to build ingestion pipelines against sources lacking a dedicated
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>. The
library provides prebuilt authentication, pagination, and incremental
loading components composed declaratively against the source
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span>. It
handles mechanical concerns (request construction, response parsing,
state management) while the developer specifies endpoints, schema
mapping, and extraction parameters. It ranks third because it delegates
the mechanical concerns to tested library components rather than hand
written <span acronym-label="http"
acronym-form="singular+short">http</span> code. That is why it is the
last sanctioned category, not a custom client. The developer must now
identify endpoints, describe the response structure, and configure
incremental loading. More connector code is written. More connector
review is required.

The ordering works cumulatively. Each step moves one or more of the five
concerns from platform custody into code per connector. Those concerns
are auth, pagination, retry and back off, incremental state, and schema
drift. More concerns in connector code means more places for defects and
more code to track on upgrades. The preference order follows directly:
use Lakeflow Connect if a supported integration exists and meets
requirements, use the <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> for the source when one covers
the needed endpoints, and fall back to <span acronym-label="dltool"
acronym-form="singular+short">dltool</span> for sources with only a
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span>.
<span acronym-label="http" acronym-form="singular+short">http</span>
clients written by hand sit outside the order entirely and are not a
sanctioned category, because they reintroduce every concern the three
categories above delegate. The five responsibilities defined below form
the full contract. <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> connectors implement them
through <span acronym-label="dltool"
acronym-form="singular+short">dltool</span> components.
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>
connectors delegate them to the client library. Lakeflow Connect
connectors satisfy them through platform configuration.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> demonstrates
all three categories.

<a href="#fig:connector-decision" data-reference-type="autoref"
data-reference="fig:connector-decision">[fig:connector-decision]</a>
summarizes the selection.

<figure id="fig:connector-decision">

<figcaption>Connector category selection. Terminal panels show how the
five cross cutting concerns are handled: <strong>platform</strong>
(managed), <strong>library</strong> (SDK or dlt), or
<strong>developer</strong> (code per connector).</figcaption>
</figure>

##### Cross cutting concerns

2.25ex 1ex .2ex 1ex .2ex Authentication Security tool
<span acronym-label="api" acronym-form="plural+short">apis</span> use
several authentication mechanisms: <span acronym-label="pat"
acronym-form="plural+short">pats</span>, OAuth 2.0 client credentials,
and service account keys. Credentials are externalized through a
platform secret scope. Each connector declares which credential type it
requires. The framework resolves it at runtime. This keeps secrets out
of pipeline code and enables credential rotation without redeploying
connectors.

2.25ex 1ex .2ex 1ex .2ex Pagination
<a href="#sec:source-integration-summary" data-reference-type="autoref"
data-reference="sec:source-integration-summary">[sec:source-integration-summary]</a>
shows <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> are the dominant integration
style. These return results in pages. Two strategies cover most sources:
offset based (page number and size parameters) and cursor based (an
opaque token returned with each response). The connector abstraction
hides pagination. Downstream code gets a stream of records. GraphQL
based sources such as the GitHub <span acronym-label="api"
acronym-form="singular+short">api</span> use cursor based pagination
exclusively.

2.25ex 1ex .2ex 1ex .2ex Rate limiting Source <span acronym-label="api"
acronym-form="plural+short">apis</span> enforce rate limits, typically
expressed as requests per time window. The connector implements adaptive
backoff: on <span acronym-label="http"
acronym-form="singular+short">http</span> 429, it pauses for the
duration in the response headers before retrying. For sources without
rate limit headers, configurable rate limits per source prevent
exceeding undocumented thresholds. Transient errors
(<span acronym-label="http" acronym-form="singular+short">http</span>
5xx) trigger exponential backoff with a configurable maximum retry
count.

2.25ex 1ex .2ex 1ex .2ex Incremental state Full re-ingestion does not
scale at enterprise volumes
(<a href="#sec:data-integration-patterns" data-reference-type="autoref"
data-reference="sec:data-integration-patterns">[sec:data-integration-patterns]</a>).
Each connector maintains a high water mark: the timestamp or cursor of
the last successfully ingested record. Subsequent runs resume from this
position, fetching only new or changed records. The high water mark is
persisted in a state table within the bronze schema, colocated with the
data it tracks. For sources supporting <span acronym-label="cdc"
acronym-form="singular+short">cdc</span> (e.g., a
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>’s
update set mechanism), the connector consumes change events directly.

Two operational patterns drive the choice of high water mark type.
**Periodic global** sources (server based scanners,
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
platforms, SCM platforms polling <span class="mark">updated_at</span> )
use a timestamp high water mark: the maximum
<span class="mark">updated_at</span> observed in the last run. **CI/CD
step** sources (scanners invoked per commit or per pull request,
typically as containerized <span acronym-label="cli"
acronym-form="singular+short">cli</span> tools) use a per repository
commit <span acronym-label="sha"
acronym-form="singular+short">sha</span> or run identifier: the
connector records the last ingested commit per repository in the state
table, and on the next run processes only scan artifacts whose commit
<span acronym-label="sha" acronym-form="singular+short">sha</span> is
newer. Both patterns use the same state table schema. They differ only
in the semantics of the high water mark value.

##### Connector Contract

Every connector module exposes two entry points.
<span class="mark">ingest</span> accepts a run identifier and a state
object, pulls new records from the source <span acronym-label="api"
acronym-form="singular+short">api</span>, and returns a batch descriptor
listing the rows landed and the advanced high water mark value.
<span class="mark">transform</span> accepts a bronze dataframe matching
the schema of the connector and returns a silver dataframe conforming to
the entity or finding pattern
(<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>). Neither
writes to silver itself. The pipeline runner persists the returned
dataframe. This keeps the connector free of storage concerns and makes
both entry points testable with in memory fixtures. For artifact path
connectors whose source specific ingestion primitive already occupies
the <span class="mark">ingest</span> symbol (OWASP ZAP, Semgrep
<span acronym-label="cli" acronym-form="singular+short">cli</span>), the
contract wrapper is exposed as <span class="mark">ingest_contract</span>
. Both names resolve to the same framework behaviour.

The state object has a fixed structure across categories: the high water
mark value (timestamp or cursor) last committed by a successful run, the
source system identifier, and optional backfill parameters for bounded
replays. The runner loads state from the state table per source before
<span class="mark">ingest</span> and persists the returned state after a
successful write, giving consistent resume semantics regardless of
whether the connector is built on Lakeflow Connect, a source
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>, or
<span acronym-label="dltool"
acronym-form="singular+short">dltool</span>. Lakeflow Connect connectors
satisfy the contract through platform configuration.
<span acronym-label="sdk" acronym-form="singular+short">sdk</span> and
<span acronym-label="rest"
acronym-form="singular+short">rest</span>-<span acronym-label="api"
acronym-form="singular+short">api</span> connectors implement the two
operations directly and delegate cross cutting concerns to the
corresponding library or helper.

##### Connector Artifacts

Adding a connector produces a fixed set of artifacts that instantiate
the contract and populate the module layout from
<a href="#sec:project-structure" data-reference-type="autoref"
data-reference="sec:project-structure">[sec:project-structure]</a>. The
list is identical for all three categories. Differences appear only in
how individual artifacts are populated:

1.   <span class="mark">src/connectors/{source}/config.yml</span> :
    source parameters, namely the base <span acronym-label="url"
    acronym-form="singular+short">url</span>, endpoints, pagination
    strategy (offset or cursor), rate limit, the high water mark column
    name, and the target bronze table name.

2.  A secret scope entry (platform level, not a file) registering the
    credential the connector requires. The entry name is referenced from
    <span class="mark">config.yml</span> . Credentials never appear in
    source files.

3.   <span class="mark">src/connectors/{source}/ingest.py</span> :
    implementation of <span class="mark">ingest(run_id, state) -\>
    batch</span> . Lakeflow Connect connectors leave this file empty and
    declare the ingestion resource in the bundle fragment instead.
    <span acronym-label="sdk" acronym-form="singular+short">sdk</span>
    connectors delegate transport concerns to the client library.
    <span acronym-label="dltool"
    acronym-form="singular+short">dltool</span> connectors compose
    prebuilt authentication and pagination components.

4.   <span class="mark">src/connectors/{source}/transform.py</span> :
    implementation of <span class="mark">transform(bronze_df) -\>
    silver_df</span> targeting the silver table owned by the connector
    category (<a href="#sec:entity-model" data-reference-type="autoref"
    data-reference="sec:entity-model">[sec:entity-model]</a>).

5.   <span class="mark">src/connectors/{source}/mapping.yml</span> :
    declarative column expressions from bronze to silver consumed by
    <span class="mark">transform.py</span> , referencing the severity
    and status lookups below.

6.   <span class="mark">config/severity/{source}.yml</span> and
    <span class="mark">config/status/{source}.yml</span> : severity and
    status lookups per source, maintained as configuration rather than
    code so that vocabulary updates do not require a pipeline redeploy.

7.  A bundle fragment under <span class="mark">resources/</span>
    defining the connector job in the standard two task layout specified
    in <a href="#sec:ingestion-patterns" data-reference-type="autoref"
    data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>.

8.   <span class="mark">tests/connectors/{source}/</span> : ingestion
    and transformation tests with the fixture layout specified in
    <a href="#sec:connector-testing" data-reference-type="autoref"
    data-reference="sec:connector-testing">[sec:connector-testing]</a>.

Silver and gold do not change. The silver tables from
<a href="#sec:entity-model" data-reference-type="autoref"
data-reference="sec:entity-model">[sec:entity-model]</a> take the new
source through the schema mapping. Gold analytics keep working.

#### Ingestion Patterns

Ingestion moves data from source <span acronym-label="api"
acronym-form="plural+short">apis</span> into bronze. All connectors
follow the same landing pattern, with source type specific variations
below.

##### Common landing pattern

Every ingestion run produces append only writes to the target bronze
table. The full <span acronym-label="api"
acronym-form="singular+short">api</span> response is preserved in
<span class="mark">\_raw_payload</span> alongside the metadata columns
from the bronze schema pattern
(<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>):
ingestion timestamp, source system identifier, and batch identifier. No
field filtering or transformation occurs. Bronze is an exact copy of
source data.

The batch identifier enables idempotent replays. If a run fails partway
through, reexecuting the same batch overwrites only the records of that
batch, preventing duplicates. For sources where merge semantics are
appropriate (e.g., <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> entity snapshots), the
connector uses upsert writes keyed on the natural identifier of each
source record.

Records failing structural validation at landing, such as malformed
<span acronym-label="json" acronym-form="singular+short">json</span> or
responses with unexpected schema changes, are routed to quarantine
tables per source. Each quarantine record includes the raw payload,
error description, and batch identifier. No record is silently dropped.
Every retrieved record either lands or goes to quarantine with a failure
reason .

##### Bronze table template

Every bronze table instantiates the same standard structure extending
the schema pattern from
<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>. The
incremental only <span class="mark">\_hwm_value</span> column introduced
in <a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a> carries
the high water mark value of the connector for the batch. This makes the
resume position auditable per record and supports targeted rebuilds that
replay ingestion from a chosen point without rereading the state table.
Tables are partitioned by ingestion date to bound scan cost and enforce
retention policies at the partition level. The naming convention
<span class="mark">appsec\_\<env\>.bronze\_\<source\>.\<entity\></span>
aligns with the Unity Catalog layout from
<a href="#sec:project-structure" data-reference-type="autoref"
data-reference="sec:project-structure">[sec:project-structure]</a>: for
example,
<span class="mark">appsec_prod.bronze_github.code_scanning_alerts</span>
or
<span class="mark">appsec_prod.bronze_servicenow.cmdb_ci_application</span>
. A connector author fills in three blanks per entity: source name,
entity name, and high water mark source field.

##### Connector job template

Every connector instantiates the same Lakeflow Job layout from
<a href="#sec:orchestration" data-reference-type="autoref"
data-reference="sec:orchestration">[sec:orchestration]</a>: a two task
<span acronym-label="dag" acronym-form="singular+short">dag</span> where
an ingest task produces bronze records and a transform task consumes
them to produce silver. The transform task declares a hard dependency on
the ingest task, so a failed ingest short circuits the job without
leaving silver partially refreshed. Retry configuration is identical
across connectors (three attempts, capped exponential backoff),
isolating transient source faults from pipeline faults. The bundle
fragment exposes a fixed set of parameters: source name (used throughout
resource naming), target catalog (environment scoped), a high water mark
reset flag for manual backfills, and the schedule cron expression. The
full bundle fragment is on the [connector job template reference
page](https://vkraus.github.io/appsec-docs/platform/reference/connector-job-template/).
Each new connector copies it verbatim and substitutes the source name
and credential reference.

##### Category specific considerations

Ingestion details by AppSec category are on the [per category capability
matrix](https://vkraus.github.io/appsec-docs/platform/reference/source-capability-matrix/).
Incremental strategy preference order for <span acronym-label="scm"
acronym-form="singular+short">scm</span>. Three scanner deployment
styles (server based, <span acronym-label="cli"
acronym-form="singular+short">cli</span> based, integrated into the
platform). The <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> relationship traversal rule.
The common landing pattern and bronze table template above apply
uniformly across all categories. Parameters per connector live in
<span class="mark">src/connectors/{source}/config.yml</span> .

#### Transformation Patterns

Transformations move data from bronze to the silver entity and finding
tables from <a href="#sec:entity-model" data-reference-type="autoref"
data-reference="sec:entity-model">[sec:entity-model]</a>. Each
transformation is a <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> pipeline reading from one or
more bronze tables and writing to a silver table. Five patterns compose
the path from bronze to silver.

##### Schema mapping

Each connector has a schema mapping extracting typed columns from the
bronze raw payload. The mapping defines which <span acronym-label="json"
acronym-form="singular+short">json</span> fields correspond to which
silver columns, applies type casts (e.g., string timestamps to
<span acronym-label="utc" acronym-form="singular+short">utc</span>
datetime), and assigns the surrogate key. Mappings are declared as
column expressions in the <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> pipeline, making them easy to
review and update when source schemas change.

The <span class="mark">mapping.yml</span> for every connector has the
same structure: a target table declaration and a list of named column
blocks where each block names a target Silver column, the
<span acronym-label="json" acronym-form="singular+short">json</span>
path into <span class="mark">\_raw_payload</span> , and a type cast.
Severity and status lookups live separately at
<span class="mark">config/severity/{source}.yml</span> and
<span class="mark">config/status/{source}.yml</span> as key-value maps
from source to target, so vocabulary updates do not require a pipeline
redeploy. A worked example for one source (SonarQube) is published at
<https://vkraus.github.io/appsec-docs/connectors/sast/sonarqube/#mapping-example>.

##### Normalization

Three normalization rules bring heterogeneous source data to a common
form:

- **Severity harmonization.** Tools use different severity scales,
  catalogued in
  <a href="#sec:selected-sources" data-reference-type="autoref"
  data-reference="sec:selected-sources">[sec:selected-sources]</a> and
  detailed per source on the [connectors reference
  hub](https://vkraus.github.io/appsec-docs/connectors/). The framework
  maps the native scale of each tool to the canonical four level model
  (critical, high, medium, low) through per tool lookup tables. The
  <span class="mark">severity_lookup.yml</span> for each source must map
  every documented source value to a canonical level. Undocumented
  values fall through to a configurable default (
  <span class="mark">medium</span> unless overridden in the
  <span class="mark">config.yml</span> for the connector) and trigger a
  data quality warning. A null or missing severity is mapped to
  <span class="mark">medium</span> and flagged. These lookup tables are
  maintained as configuration, not code, enabling vocabulary updates
  without pipeline changes.

- **Status normalization.** Finding lifecycle states vary across tools
  (e.g., SonarQube’s “confirmed” vs. GitHub’s “open”). A per tool status
  mapping translates the states of each tool to the canonical five state
  model (open, confirmed, resolved, false_positive, wontfix).

- **Timestamp standardization.** All timestamps are converted to
  <span acronym-label="utc" acronym-form="singular+short">utc</span>.
  Source specific formats (ISO 8601, Unix epoch, tool specific strings)
  are parsed during schema mapping and stored as
  <span acronym-label="utc" acronym-form="singular+short">utc</span>
  datetime columns.

##### Data quality validation

<span acronym-label="ldp" acronym-form="singular+short">ldp</span>
expectations enforce constraints on every record entering silver.
Expectations are declared alongside the transformation and checked at
runtime. Examples: severity must be one of four canonical values, status
must be one of five canonical states, repository foreign keys must
reference an existing silver entity, and timestamps must fall within a
plausible range. Violating records are quarantined rather than
propagated, consistent with the quarantine pattern at ingestion.

##### Deduplication application

Deduplication keys are defined in the Silver Finding pattern
(<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>): exact
match on <span class="mark">(repository_id, file_path, rule_id,
line_number)</span> for <span acronym-label="sast"
acronym-form="singular+short">sast</span>, on
<span class="mark">(repository_id, package_name, cve_id)</span> for
<span acronym-label="sca" acronym-form="singular+short">sca</span>, and
on <span class="mark">(repository_id, commit_sha, secret_type,
file_path)</span> for secrets. The transformation step applies these
keys: every silver finding enters a post mapping dedup pass that writes
<span class="mark">dedup_links</span> records for every overlapping pair
among records sharing a <span class="mark">repository_id</span> .
Deduplicated findings are not deleted. The link record preserves
traceability to each source report while establishing the reference
finding for aggregation. No fuzzy matching is performed. Line number
divergence is handled at Gold via
<span class="mark">finding_group_id</span>
(<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>).
Deduplication pairs are enumerated per tool combination in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>.

##### Business context attribution

The final transformation step links findings to business applications.
The <span class="mark">app_repo_mapping</span> relationship table maps
repositories to applications. Since this is many to many (one
application may span multiple repositories, and one repository may serve
multiple applications), findings inherit application context through a
join rather than a direct foreign key. This enables the gold layer
aggregations in
<a href="#sec:aggregation-model" data-reference-type="autoref"
data-reference="sec:aggregation-model">[sec:aggregation-model]</a> to
compute per application metrics. The mapping is sourced from the
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
connector and can be supplemented by automated inference from repository
to application in the <span acronym-label="ml"
acronym-form="singular+short">ml</span> workflows from
<a href="#sec:analytics-patterns" data-reference-type="autoref"
data-reference="sec:analytics-patterns">[sec:analytics-patterns]</a>.

#### Testing and Validation

Connector tests live beside the connector they cover, at
<span class="mark">tests/connectors/{source}/</span> , not in a central
suite. <span class="mark">test_ingest.py</span> covers the ingestion
contract, <span class="mark">test_transform.py</span> covers the
transformation from bronze to silver, and
<span class="mark">fixtures/</span> holds the <span acronym-label="json"
acronym-form="singular+short">json</span> inputs both consume. Fixture
filenames follow <span class="mark">{endpoint}\_{scenario}.json</span>
so regression cases are discoverable without opening each file. Fixtures
are recorded once from a representative source instance and then frozen,
which removes dependence on any particular tenant or tool build. The
same test suite runs against any deployment, in
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
without network access, and a fixture change becomes an auditable diff
rather than a silent environmental drift. The stack adds three libraries
on top of pytest: an <span acronym-label="http"
acronym-form="singular+short">http</span> mocking library (
<span class="mark">responses</span> or
<span class="mark">requests-mock</span> ), a PySpark DataFrame assertion
library ( <span class="mark">chispa</span> ), and
<span acronym-label="ldp" acronym-form="singular+short">ldp</span>
expectations for runtime data quality checks. Each test carries a
<span class="mark">@pytest.mark.requirement(...)</span> marker so the
traceability matrix links results to the connector framework
requirements below.

-  <span class="mark">REQ-ING-AUTH</span> : authentication and
  credential resolution against the platform secret scope.

-  <span class="mark">REQ-ING-PAG</span> : pagination traversal without
  data loss or duplication across at least two pages.

-  <span class="mark">REQ-ING-RL</span> : <span acronym-label="http"
  acronym-form="singular+short">http</span> 429 handling and backoff
  according to the configured retry policy.

-  <span class="mark">REQ-ING-HWM</span> : high water mark resume across
  two consecutive runs with a midrun data change.

-  <span class="mark">REQ-TRF-MAP</span> : schema mapping for every
  ingested endpoint.

-  <span class="mark">REQ-TRF-SEV</span> : severity normalization
  covering every source specific severity value, including edge cases.

-  <span class="mark">REQ-TRF-STS</span> : status normalization covering
  every source specific lifecycle state.

-  <span class="mark">REQ-TRF-TS</span> : timestamp normalization for
  every source specific format.

-  <span class="mark">REQ-DQ</span> : at least one
  <span acronym-label="ldp" acronym-form="singular+short">ldp</span>
  expectation per target silver table, with one violating and one valid
  record.

-  <span class="mark">REQ-DEDUP</span> : deduplication for every
  applicable tool overlap pair (omitted when the connector category does
  not participate in dedup).

New connectors do not merge until every applicable marker above passes
in <span acronym-label="cicd" acronym-form="singular+short">cicd</span>.

### Analytics and Serving Framework

This section addresses the final stage: computing consumption ready
insights from silver data and delivering them to stakeholders.
<a href="#sec:aggregation-model" data-reference-type="autoref"
data-reference="sec:aggregation-model">[sec:aggregation-model]</a>
defined **which** gold tables the framework provides. This section
defines **how** those computations are structured and how results reach
consumers through analytical, operational, and event driven channels.

#### Analytics Patterns

Gold layer computations fall into two categories: rule based analytics
applying deterministic formulas to silver data, and
<span acronym-label="ml" acronym-form="singular+short">ml</span> driven
analytics learning patterns from historical data. Both produce outputs
following the gold aggregation pattern from
<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>.

##### Extension blueprint

Adding a new analytics workflow follows a consistent process. First,
define the business question and identify the stakeholder. Second,
choose rule based or <span acronym-label="ml"
acronym-form="singular+short">ml</span>: rule based suits well
understood relationships with clear formulas, and
<span acronym-label="ml" acronym-form="singular+short">ml</span> suits
pattern recognition over complex, high dimensional data. Third,
implement the computation as a <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> pipeline (rule based) or MLflow
tracked experiment (<span acronym-label="ml"
acronym-form="singular+short">ml</span>). Fourth, wire the output to a
gold table following the aggregation pattern, configure the refresh
strategy, and register the table in Unity Catalog for governance and
lineage.

The process produces a fixed set of artifacts under
<span class="mark">src/analytics/{name}/</span> , mirroring the
connector layout from
<a href="#sec:project-structure" data-reference-type="autoref"
data-reference="sec:project-structure">[sec:project-structure]</a>:

1.   <span class="mark">src/analytics/{name}/pipeline.py</span> : the
    <span acronym-label="ldp" acronym-form="singular+short">ldp</span>
    pipeline (rule based) or MLflow experiment entry point
    (<span acronym-label="ml" acronym-form="singular+short">ml</span>)
    that produces the gold table.

2.   <span class="mark">src/analytics/{name}/ddl.sql</span> : the gold
    table schema declaration, conforming to the grain, metric, period
    structure from
    <a href="#sec:schema-patterns" data-reference-type="autoref"
    data-reference="sec:schema-patterns">[sec:schema-patterns]</a>.

3.   <span class="mark">src/analytics/{name}/config.yml</span> : refresh
    strategy (incremental or full), the aggregation grain, and the
    upstream silver dependencies.

4.  A bundle fragment under <span class="mark">resources/</span> that
    wires the pipeline into the orchestration described in
    <a href="#sec:orchestration" data-reference-type="autoref"
    data-reference="sec:orchestration">[sec:orchestration]</a>,
    declaring dependencies on the connector jobs that populate the
    upstream silver tables.

5.   <span class="mark">tests/analytics/{name}/</span> : gold layer
    computation tests with known silver inputs and expected gold
    outputs. <span acronym-label="ml"
    acronym-form="singular+short">ml</span> workflows add model
    training, validation, and drift tests per
    <a href="#sec:analytics-testing" data-reference-type="autoref"
    data-reference="sec:analytics-testing">[sec:analytics-testing]</a>.

Authoring a new analytic never requires connector edits, and introducing
a connector never requires analytics edits: silver is the stable
boundary between the two.

##### Rule Based Analytics

Rule based analytics implement deterministic business logic as
<span acronym-label="sql" acronym-form="singular+short">sql</span>
transformations or <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> pipelines. Three computation
patterns cover what the framework needs.

**Composite scoring** combines multiple signals into a single metric.
The application risk score, for example, weights open finding counts by
severity, multiplies by <span acronym-label="epss"
acronym-form="singular+short">epss</span> exploitation probability, and
factors in the criticality tier of the application. The formula is
configurable: organizations assign weights based on their risk appetite.
<span acronym-label="sla" acronym-form="singular+short">sla</span>
compliance follows the same pattern, comparing finding ages against
severity specific thresholds to produce a compliance percentage.

**Time series aggregation** rolls up finding data at daily, weekly, and
monthly intervals. Each roll up computes period metrics (new findings,
resolved findings, net open count) and derived indicators (period over
period change, moving averages, severity distribution shifts). These
power the trend dashboards tracking organizational progress over time.

**Threshold classification** assigns categorical labels based on metric
values. Risk tiers (critical, high, medium, low) are assigned to
applications by composite score. Coverage gaps are flagged when a
repository lacks scan records for a tool category.
<span acronym-label="sla" acronym-form="singular+short">sla</span>
breaches are marked when open finding age exceeds the severity specific
threshold. These classifications enable filtering and alerting
downstream.

Two refresh strategies apply. **Incremental refresh** recomputes only
partitions affected by new silver records. This suits most aggregations
where each record maps to a single grain partition (e.g., one
application, one time period). **Full refresh** recomputes the entire
table. It is necessary for metrics depending on global state, such as
cross application percentile rankings or organization wide severity
distributions.

##### ML Driven Analytics

<span acronym-label="ml" acronym-form="singular+short">ml</span> driven
analytics learn patterns from historical silver and gold data to produce
predictive signals rule based formulas cannot capture. The framework
supports four use cases: **composite risk scoring** learns which
combinations of findings and development activity signals have preceded
security incidents rather than using predefined weights, **false
positive prediction** estimates the probability that a new finding is a
false positive from historical triage decisions and repository history
to reduce developer noise, **remediation time estimation** predicts
<span acronym-label="mttr" acronym-form="singular+short">mttr</span>
from historical resolution data to inform <span acronym-label="sla"
acronym-form="singular+short">sla</span> forecasting, and **anomaly
detection** flags spikes in finding volumes or severity distribution
shifts that reveal tool misconfigurations or new weak points.

Across all four, framework commitments are narrow. Outputs land in Gold
tables under the Gold Aggregation pattern from
<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>, every
run is tracked in MLflow with the run ID recorded on output rows, and
retraining ships in the same <span acronym-label="dab"
acronym-form="singular+short">dab</span> bundle as ingestion and
transformation so deploys and rollbacks are atomic. Feature Store
supplies reusable feature tables across training and inference, and
Model Serving exposes real time inference endpoints cached in Lakebase
for latency sensitive predictions . Feature selection, splits,
algorithms, and cadence are left to
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>.

#### Serving Patterns

The serving layer delivers gold outputs to the data consumers from
<a href="#sec:component-design" data-reference-type="autoref"
data-reference="sec:component-design">[sec:component-design]</a>. Three
delivery modes address different access patterns and latency
requirements.

##### Analytical serving

Analytical serving targets dashboards, reporting tools, and ad hoc
analysis through the <span acronym-label="olap"
acronym-form="singular+short">olap</span> path. A
<span acronym-label="sql" acronym-form="singular+short">sql</span>
warehouse executes queries against gold Delta tables, providing sub five
second response times for precomputed aggregations. Materialized views
cache frequently accessed query patterns, reducing compute cost for
recurring dashboard refreshes.

Stakeholder specific views organize gold data for each audience:
executive risk overviews show application risk scores and organizational
trends, team dashboards present remediation metrics and
<span acronym-label="sla" acronym-form="singular+short">sla</span>
compliance, and security engineering views expose tool coverage gaps and
deduplication statistics. These are <span acronym-label="sql"
acronym-form="singular+short">sql</span> views on top of the gold
tables, not separate copies, ensuring consistency across consumers.

##### Operational serving

Operational serving targets low latency workloads through the
<span acronym-label="oltp" acronym-form="singular+short">oltp</span>
path. Lakebase exposes gold tables as PostgreSQL queryable relations
with sub 50 millisecond response times . Because Lakebase shares storage
with the lakehouse, gold tables are accessible without data duplication
or synchronization pipelines.

Three operational workloads use this path. Remediation state lookups
retrieve current status, severity, and ownership of individual findings
for developer workflow integration. Operational
<span acronym-label="api" acronym-form="plural+short">apis</span> expose
risk scores, coverage data, and finding details through the PostgREST
Data <span acronym-label="api" acronym-form="singular+short">api</span>,
providing <span acronym-label="http"
acronym-form="singular+short">http</span> access to any gold table
without custom <span acronym-label="api"
acronym-form="singular+short">api</span> code. <span acronym-label="ml"
acronym-form="singular+short">ml</span> inference results cached in
Lakebase serve real time risk assessments for newly ingested findings.
Lakebase scales to zero, reducing cost during off peak periods.

##### Event driven serving

Event driven serving pushes data to external systems rather than waiting
for them to query. This closes the loop between analysis and operational
action.

**Automated issue creation** triggers when new critical findings or
<span acronym-label="sla" acronym-form="singular+short">sla</span>
breaches are detected. The framework creates work items in issue
trackers (Jira, ServiceNow) through their <span acronym-label="api"
acronym-form="plural+short">apis</span>, linking back to the finding
record. Idempotency guards prevent duplicate ticket creation on reruns.

**Threshold based notifications** alert stakeholders when metrics cross
configured boundaries: a risk score exceeds a threshold, a new
<span acronym-label="kev" acronym-form="singular+short">kev</span>
listed vulnerability is detected, or <span acronym-label="sla"
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
gold tables generates a stream of change events (new critical findings,
risk score changes, coverage regressions) that
<span acronym-label="soar" acronym-form="singular+short">soar</span>
playbooks consume for automated response. Shared infrastructure with
Lakewatch (<a href="#sec:tech-stack" data-reference-type="autoref"
data-reference="sec:tech-stack">[sec:tech-stack]</a>) enables this
integration without external data movement.

**Bidirectional synchronization** keeps the view in the framework
consistent with external systems. Issue tracker status updates (e.g., a
Jira ticket moved to “Done”) flow back through scheduled polling or
webhooks, updating the lifecycle state in silver for the corresponding
finding. This ensures gold layer remediation metrics reflect actual
resolution progress.

#### Testing and Validation

Rule based analytics are validated by snapshot comparison. Each test
supplies silver fixtures with known values and asserts the gold output
matches a curated expected table exactly, using PySpark DataFrame
assertions on aggregation outputs. Fixtures cover the computation
boundaries from
<a href="#sec:analytics-patterns" data-reference-type="autoref"
data-reference="sec:analytics-patterns">[sec:analytics-patterns]</a>:
zero findings, all critical findings, missing enrichment data, period
bucketing at month boundaries, and threshold classification at each tier
cutoff. A refresh idempotency case runs the pipeline twice on the same
input to confirm no spurious gold writes.

<span acronym-label="ml" acronym-form="singular+short">ml</span> driven
analytics are validated by held out evaluation and drift monitoring.
MLflow’s <span class="mark">evaluate()</span> <span acronym-label="api"
acronym-form="singular+short">api</span> computes accuracy, precision,
recall, and F1 score on a held out dataset, and
<span class="mark">validate_evaluation_results()</span> gates promotion
against configured thresholds and the registered production baseline .
In production, prediction distribution comparisons against a rolling
baseline flag drift before model quality visibly degrades. Feature Store
staleness checks ensure inference features are no older than their
configured threshold. Serving endpoints are exercised through
<span acronym-label="http" acronym-form="singular+short">http</span>
clients to verify correctness and measure latency against the targets in
<a href="#sec:serving-patterns" data-reference-type="autoref"
data-reference="sec:serving-patterns">[sec:serving-patterns]</a>.

The required test suite covers:

- Every gold table: metric correctness, boundary conditions, and refresh
  idempotency.

- Every <span acronym-label="ml" acronym-form="singular+short">ml</span>
  model: training convergence, validation accuracy, drift monitoring,
  and promotion gating.

- Every serving endpoint: response correctness and latency verification.

New analytics or serving configurations do not merge until this suite
passes.

### A Note on Extension and AI Assistance

Every artifact this chapter prescribes is a template with named slots to
fill in, not free form code. This covers the connector files
(<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>),
the analytics jobs
(<a href="#sec:analytics-serving" data-reference-type="autoref"
data-reference="sec:analytics-serving">[sec:analytics-serving]</a>), and
the test suites
(<a href="#sec:connector-testing" data-reference-type="autoref"
data-reference="sec:connector-testing">[sec:connector-testing]</a>,
<a href="#sec:analytics-testing" data-reference-type="autoref"
data-reference="sec:analytics-testing">[sec:analytics-testing]</a>).
This was deliberate. The framework should be amenable to AI assisted
extension. The [external requirements
specification](https://vkraus.github.io/appsec-docs/) catalogs three
Claude Code skills that consume these templates and produce a reference
implementation. The catalog is organized by lifecycle role, not by
source: <span class="mark">analyze-source</span> maps a candidate source
onto the framework taxonomy,
<span class="mark">generate-connector</span> produces the eight
connector artifacts listed in
<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>,
and <span class="mark">validate-implementation</span> drives the layered
test suite from
<a href="#sec:connector-testing" data-reference-type="autoref"
data-reference="sec:connector-testing">[sec:connector-testing]</a> until
the requirement IDs from the specification are bound to passing tests.

The catalog stays at three skills rather than one skill for every
combination of role and application security category. This follows the
recommended pattern for skills that span multiple variants of the same
task . Each <span class="mark">SKILL.md</span> carries the role wide
procedure. Guidance per category lives one level deeper, in a
<span class="mark">references/\<category\>.md</span> file the agent
reads on demand. The seven application security categories the Selected
Nine exercise are <span class="mark">cmdb</span> ,
<span class="mark">scm</span> , <span class="mark">sast</span> ,
<span class="mark">sca</span> , <span class="mark">secret</span> ,
<span class="mark">dast</span> , and <span class="mark">waf</span> . The
category here is the source axis from the [per category capability
matrix](https://vkraus.github.io/appsec-docs/platform/reference/source-capability-matrix/),
not the connector category triad of
<a href="#sec:connector-abstraction" data-reference-type="autoref"
data-reference="sec:connector-abstraction">[sec:connector-abstraction]</a>.
Each reference file specializes the role procedure with the dedup tuple
from <a href="#sec:dedup" data-reference-type="autoref"
data-reference="sec:dedup">[sec:dedup]</a>, the schema discriminator
from the silver finding pattern
(<a href="#sec:entity-model" data-reference-type="autoref"
data-reference="sec:entity-model">[sec:entity-model]</a>), and the
entries per source from the capability matrix. New categories add a
reference file. The role procedure does not change.

This shape inherits two properties from the underlying skills
mechanism . The metadata cost stays at three descriptions in the agent
system prompt no matter how many categories the framework grows to
cover. The role procedure is authored once and shared across categories.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> reports on
the execution of the catalog against the nine selected sources. Hand
writing connectors is routine with modern <span acronym-label="ai"
acronym-form="singular+short">ai</span> assistance. The claim of this
thesis is different. A well specified framework plus a small skill
catalog makes the platform reproducibly buildable, with full
traceability from test to requirement in the specification itself.

## MVP Implementation

This chapter reports the reference implementation of the framework
defined in <a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>. The deliverable is a
Databricks Asset Bundle  that instantiates the three ingestion
categories against the nine sources selected in
<a href="#sec:selected-sources" data-reference-type="autoref"
data-reference="sec:selected-sources">[sec:selected-sources]</a>. It is
a minimum viable product, not a production ready integration of every
security tool an enterprise might deploy. The nine sources cover the
ingestion and integration patterns the framework must support: two
<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms, four scanners across static and dynamic testing, a
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>, a
secrets tool, and a runtime security source. Onboarding a tenth source
does not require a framework change. It repeats the procedure in
<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a> and
lands a new <span class="mark">src/connectors/\<source\>/</span> folder.

The contribution is the demonstration that the contract of three
categories holds across the nine sources and that the resulting code
fits one small, repeating module layout.
<a href="#sec:impl-project-structure" data-reference-type="autoref"
data-reference="sec:impl-project-structure">[sec:impl-project-structure]</a>
reports the realized project layout.
<a href="#sec:ingestion-category-assignment"
data-reference-type="autoref"
data-reference="sec:ingestion-category-assignment">[sec:ingestion-category-assignment]</a>
resolves each selected source to its category.
<a href="#sec:impl-representative-connectors"
data-reference-type="autoref"
data-reference="sec:impl-representative-connectors">[sec:impl-representative-connectors]</a>
shows the two ends of the category range in concrete code: ServiceNow on
Lakeflow Connect (declarative) and GitHub on PyGitHub 
(<span acronym-label="sdk" acronym-form="singular+short">sdk</span>).

### Methodology

The implementation follows the same four steps for every source in
<a href="#sec:selected-sources" data-reference-type="autoref"
data-reference="sec:selected-sources">[sec:selected-sources]</a>:

1.  **Resolve the ingestion category.** The source is matched against
    the three categories defined in
    <a href="#sec:connector-abstraction" data-reference-type="autoref"
    data-reference="sec:connector-abstraction">[sec:connector-abstraction]</a>.
    The evaluation order is fixed: Lakeflow Connect  first, then a
    maintained Python <span acronym-label="sdk"
    acronym-form="singular+short">sdk</span>, then
    <span acronym-label="dltool"
    acronym-form="singular+short">dltool</span>. Tools that only ship a
    <span acronym-label="cli" acronym-form="singular+short">cli</span>
    fall outside the axis of three categories and follow the artifact
    pattern at the <span acronym-label="cicd"
    acronym-form="singular+short">cicd</span> step described in
    <a href="#sec:ingestion-patterns" data-reference-type="autoref"
    data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>.
    <a href="#sec:ingestion-category-assignment"
    data-reference-type="autoref"
    data-reference="sec:ingestion-category-assignment">[sec:ingestion-category-assignment]</a>
    carries out this step for all nine sources.

2.  **Instantiate the module layout per connector.** Every connector
    carries the same four files under
    <span class="mark">src/connectors/\<source\>/</span> :
    <span class="mark">ingest.py</span> ,
    <span class="mark">transform.py</span> ,
    <span class="mark">mapping.yml</span> , and
    <span class="mark">config.yml</span> . For Lakeflow Connect sources,
    <span class="mark">ingest.py</span> is reduced to a module
    docstring. Ingestion is declared in the bundle fragment as a
    <span class="mark">pipelines</span> resource with an
    <span class="mark">ingestion_definition</span> .

3.  **Apply the mapping declaratively.** The
    <span class="mark">mapping.yml</span> per source encodes the column
    expressions from bronze to silver given by the [canonical mapping
    requirements](https://vkraus.github.io/appsec-docs/platform/reference/canonical-mapping/).
    Severity and status lookups live in
    <span class="mark">config/severity/\<source\>.yml</span> and
    <span class="mark">config/status/\<source\>.yml</span> .
    <span class="mark">src/common/silver.py</span> provides severity
    rank and status bucket normalization helpers and deduplication
    utilities shared across connectors. Each connector’s
    <span class="mark">transform.py</span> module builds the Silver
    DataFrame field by field, calling the shared normalization helpers.
    The <span class="mark">mapping.yml</span> file in each connector
    declares the intended field derivation per source as documentation.
    The current MVP builds the DataFrame in Python rather than applying
    the YAML declaratively, and
    <a href="#sec:future-work" data-reference-type="autoref"
    data-reference="sec:future-work">[sec:future-work]</a> carries the
    declarative applicator as a thread.

4.  **Test in the layered strategy from
    <a href="#sec:connector-testing" data-reference-type="autoref"
    data-reference="sec:connector-testing">[sec:connector-testing]</a>.**
    Tests divide along the signature of the code they exercise. Row
    level logic in pure Python (parser logic, mapping application,
    <span acronym-label="hwm" acronym-form="singular+short">hwm</span>
    state, dedup key construction) runs locally against
    <span class="mark">list\[dict\]</span> fixtures with no
    <span class="mark">SparkSession</span> . DataFrame logic
    (transformations, envelope stamping, schema enforcement) runs
    through a session scoped Databricks Connect fixture that attaches to
    a remote workspace, so the test runtime matches the production
    runtime.

Step 1 has a deterministic answer for every source in the sample.
Step 2’s layout does not vary across categories. That invariance is what
makes the framework <span acronym-label="ai"
acronym-form="singular+short">ai</span> instantiable in principle. A
generator that emits the layout with four files for a new source does
not need to branch on category beyond what
<span class="mark">ingest.py</span> contains and which bundle resource
kind the source requires.

### Project Structure

The reference implementation is distributed across three repositories
that separate the thesis document, the external requirements
specification, and the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> code.

- The thesis repository holds the LaTeX sources for this document.

- The <span class="mark">appsec-docs</span> repository
  (<https://github.com/vkraus/appsec-docs>) holds the MkDocs Material
  site published at <https://vkraus.github.io/appsec-docs/>. It is the
  authoritative requirements specification and reference per source. The
  thesis consumes it through inline hyperlinks.

- The <span class="mark">appsec-mvp</span> repository
  (<https://github.com/vkraus/appsec-mvp>) holds the reference
  implementation described in the remainder of this section.

Inside <span class="mark">appsec-mvp</span> the framework layout from
<a href="#sec:project-structure" data-reference-type="autoref"
data-reference="sec:project-structure">[sec:project-structure]</a> is
realized as the directory tree shown in
<a href="#lst:mvp-tree" data-reference-type="autoref"
data-reference="lst:mvp-tree">[lst:mvp-tree]</a>.

```
appsec-mvp/
|-- databricks.yml                       # bundle root: targets, variables
|-- pyproject.toml                       # Python package metadata
|-- src/
|   |-- common/                          # framework primitives (runtime-shared)
|   |   |-- config.py                    # config.yml / severity / status loaders
|   |   |-- hwm.py                       # high-water-mark strategies
|   |   |-- cwe.py                       # CWE extraction helpers
|   |   |-- schemas.py                   # silver-layer StructType definitions
|   |   \-- silver.py                    # severity/status normalization + dedup helpers
|   \-- connectors/
|       |-- servicenow/                  # category: Lakeflow Connect
|       |   |-- ingest.py                # docstring only; pipeline is declared
|       |   |-- transform.py             # field-by-field Silver Row builder
|       |   |-- mapping.yml
|       |   \-- config.yml
|       \-- github/                      # category: SDK (PyGitHub)
|           |-- ingest.py                # PyGitHub calls, returns iterators
|           |-- transform.py
|           |-- mapping.yml
|           \-- config.yml
|-- config/
|   |-- severity/<source>.yml            # source-to-target severity lookup
|   \-- status/<source>.yml              # source-to-target status lookup
|-- resources/
|   |-- servicenow-pipeline.yml          # pipelines resource (Lakeflow Connect)
|   |-- github-job.yml                   # jobs resource (SDK category)
|   \-- shared.yml                       # UC schema bootstrap (DAB schemas resource)
|-- sql/
|   \-- bootstrap/                       # DDL fallback (DAB-managed primary)
|-- infra/
|   \-- terraform/                       # workspace and metastore provisioning
\-- tests/
    |-- common/                          # framework-primitive unit tests
    \-- connectors/<source>/             # per-connector tests
```

Three points distinguish this layout from the framework prescription in
<a href="#sec:project-structure" data-reference-type="autoref"
data-reference="sec:project-structure">[sec:project-structure]</a>.
First, <span class="mark">src/common/</span> has a fixed, finite
membership. Every primitive in it is consumed by at least one connector
at runtime. An <span acronym-label="http"
acronym-form="singular+short">http</span> client written by hand in this
folder would be a fourth ingestion category, which the framework does
not admit.
<a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a>
reports an implementation phase iteration that removed such a module
after it had been added. Second, the bundle resources directory contains
both <span class="mark">jobs</span> fragments (for
<span acronym-label="sdk" acronym-form="singular+short">sdk</span> and
<span acronym-label="dltool" acronym-form="singular+short">dltool</span>
connectors) and <span class="mark">pipelines</span> fragments (for
Lakeflow Connect connectors). The filename suffix distinguishes them.
Third, the repository holds everything needed to stand up the target
environment from zero: Terraform under
<span class="mark">infra/terraform/</span> provisions the workspace and
Unity Catalog  metastore. Schema provisioning is
<span acronym-label="dab" acronym-form="singular+short">dab</span>
managed via <span class="mark">resources/shared.yml</span> , and
<span class="mark">sql/bootstrap/schemas.sql</span> carries an
equivalent idempotent DDL fallback for environments where bundle managed
schemas are disabled. The <span acronym-label="dab"
acronym-form="singular+short">dab</span> is the only artifact a release
promotes. The Terraform and SQL are run once per environment.

### Ingestion Category Assignment

Each source is resolved to one of the three ingestion categories defined
in <a href="#sec:connector-abstraction" data-reference-type="autoref"
data-reference="sec:connector-abstraction">[sec:connector-abstraction]</a>
before its connector module is written. The evaluation order is fixed
(Lakeflow Connect, then <span acronym-label="sdk"
acronym-form="singular+short">sdk</span>, then
<span acronym-label="dltool"
acronym-form="singular+short">dltool</span>). Each entry below restates
the functional requirements drawn from
<a href="#sec:cross-source-synthesis" data-reference-type="autoref"
data-reference="sec:cross-source-synthesis">[sec:cross-source-synthesis]</a>
and the source specific reference page, assesses the three categories
against them, and records the selected category together with the
library or mechanism that instantiates it. <span acronym-label="cli"
acronym-form="singular+short">cli</span> only tools fall outside the
axis of three categories and follow the <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> step artifact pattern
described in
<a href="#sec:ingestion-patterns" data-reference-type="autoref"
data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>.
The outcomes feed directly into
<a href="#sec:impl-results" data-reference-type="autoref"
data-reference="sec:impl-results">[sec:impl-results]</a> and determine
the bundle resource kind ( <span class="mark">jobs</span> or
<span class="mark">pipelines</span> ) used for each source.

- **ServiceNow.** Category: Lakeflow Connect. Functional requirements
  ([ServiceNow
  reference](https://vkraus.github.io/appsec-docs/connectors/cmdb/servicenow/)):
  periodic pull from the Table <span acronym-label="api"
  acronym-form="singular+short">api</span> and
  <span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
  Instance <span acronym-label="api"
  acronym-form="singular+short">api</span> with offset pagination,
  <span class="mark">sys_updated_on</span> as the high water mark,
  OAuth 2.0 or basic authentication, no webhook. ServiceNow is a source
  supported natively by Lakeflow Connect, covering authentication,
  pagination, incremental state, and schema inference through platform
  configuration. Lakeflow Connect meets every requirement. The
  <span class="mark">ingest.py</span> for the connector is left empty.
  Ingestion is declared in the bundle fragment under
  <span class="mark">resources/</span> .

- **GitHub.** Category: <span acronym-label="sdk"
  acronym-form="singular+short">sdk</span> via PyGitHub. Functional
  requirements ([GitHub
  reference](https://vkraus.github.io/appsec-docs/connectors/scm/github/)):
  <span acronym-label="rest" acronym-form="singular+short">rest</span>
  plus GraphQL access to repositories, commits, pull requests, branch
  protection, code scanning alerts, secret scanning alerts, and
  Dependabot alerts. Cursor pagination on <span acronym-label="rest"
  acronym-form="singular+short">rest</span> via
  <span class="mark">Link</span> headers and
  <span class="mark">pageInfo</span> cursors on GraphQL.
  <span acronym-label="pat" acronym-form="singular+short">pat</span> or
  GitHub App installation tokens. Primary rate limits of 5 000 requests
  per hour (<span acronym-label="pat"
  acronym-form="singular+short">pat</span>) or 15 000 for Enterprise
  GitHub Apps. Webhook preferred per
  <a href="#sec:ingestion-patterns" data-reference-type="autoref"
  data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>.
  Lakeflow Connect does not support GitHub at <span acronym-label="mvp"
  acronym-form="singular+short">mvp</span> time. PyGitHub is the widely
  adopted community Python <span acronym-label="sdk"
  acronym-form="singular+short">sdk</span>. It covers every
  <span acronym-label="rest" acronym-form="singular+short">rest</span>
  endpoint the framework needs, handles <span class="mark">Link</span>
  header pagination, and exposes rate limit status as first class
  attributes. The <span acronym-label="sdk"
  acronym-form="singular+short">sdk</span> category wins:
  <span class="mark">ingest.py</span> calls PyGitHub’s
  <span class="mark">Repository</span> ,
  <span class="mark">PullRequest</span> , and
  <span class="mark">CodeScanningAlert</span> accessors directly.

- **GitLab.** Category: <span acronym-label="sdk"
  acronym-form="singular+short">sdk</span> via python-gitlab .
  Functional requirements ([GitLab
  reference](https://vkraus.github.io/appsec-docs/connectors/scm/gitlab/)):
  <span acronym-label="rest" acronym-form="singular+short">rest</span>
  access to projects, merge requests, pipelines, and vulnerability
  findings (Ultimate tier) or pipeline artifact parsing (non-Ultimate).
  Keyset pagination on <span acronym-label="rest"
  acronym-form="singular+short">rest</span>,
  <span class="mark">pageInfo</span> on GraphQL.
  <span acronym-label="pat" acronym-form="singular+short">pat</span> or
  OAuth. Webhook coverage. No Lakeflow Connect support.
  <span class="mark">python-gitlab</span> is the project recognized
  Python client, covers the required endpoints, and handles keyset
  pagination transparently. Category selection parallels GitHub.

- **SonarQube** . Category: <span acronym-label="dltool"
  acronym-form="singular+short">dltool</span>. Functional requirements
  ([SonarQube
  reference](https://vkraus.github.io/appsec-docs/connectors/sast/sonarqube/)):
  <span acronym-label="rest" acronym-form="singular+short">rest</span>
  Web <span acronym-label="api" acronym-form="singular+short">api</span>
  ( <span class="mark">api/issues/search</span> ,
  <span class="mark">api/hotspots/search</span> ,
  <span class="mark">api/projects/search</span> ). Offset pagination via
  <span class="mark">p</span> and <span class="mark">ps</span>
  parameters. <span class="mark">updateDate</span> high water mark.
  Token based authentication via <span acronym-label="http"
  acronym-form="singular+short">http</span> Basic.
  <span acronym-label="json" acronym-form="singular+short">json</span>
  responses. No Lakeflow Connect integration. SonarSource does not
  publish and maintain an official Python <span acronym-label="sdk"
  acronym-form="singular+short">sdk</span>, and surveyed community
  clients are unmaintained at the Web <span acronym-label="api"
  acronym-form="singular+short">api</span> version the
  <span acronym-label="lts" acronym-form="singular+short">lts</span>
  server ships. <span acronym-label="dltool"
  acronym-form="singular+short">dltool</span>’s
  <span class="mark">rest_api</span> source template covers all
  requirements declaratively. <span class="mark">ingest.py</span>
  composes a <span acronym-label="dltool"
  acronym-form="singular+short">dltool</span> pipeline.

- **Semgrep (Docker).** Category: artifact path, not an
  <span acronym-label="http" acronym-form="singular+short">http</span>
  category. Functional requirements ([Semgrep
  reference](https://vkraus.github.io/appsec-docs/connectors/sast/semgrep/),
  <span acronym-label="cli" acronym-form="singular+short">cli</span>
  variant): produce a <span acronym-label="json"
  acronym-form="singular+short">json</span> report per commit from a
  <span acronym-label="cicd" acronym-form="singular+short">cicd</span>
  step. The report file is the authoritative interface. The source has
  no <span acronym-label="http"
  acronym-form="singular+short">http</span> <span acronym-label="api"
  acronym-form="singular+short">api</span> in this deployment. The
  framework handles this through the <span acronym-label="cicd"
  acronym-form="singular+short">cicd</span> step pattern
  (<a href="#sec:ingestion-patterns" data-reference-type="autoref"
  data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>):
  the <span acronym-label="cicd"
  acronym-form="singular+short">cicd</span> step runs
  <span class="mark">semgrep –json</span> and
  <span class="mark">databricks fs cp</span> to a Unity Catalog Volume.
  The <span class="mark">transform.py</span> for the connector reads the
  Volume directly. <span class="mark">ingest.py</span> is empty.

- **Semgrep (Cloud).** Category: <span acronym-label="dltool"
  acronym-form="singular+short">dltool</span>. Functional requirements
  ([Semgrep
  reference](https://vkraus.github.io/appsec-docs/connectors/sast/semgrep/),
  Cloud Platform variant): <span acronym-label="rest"
  acronym-form="singular+short">rest</span> access to findings with
  cursor pagination, <span class="mark">since_date</span> /
  <span class="mark">updated_at</span> high water mark, bearer token
  authentication. No Lakeflow Connect integration, no official Python
  <span acronym-label="sdk" acronym-form="singular+short">sdk</span>.
  <span acronym-label="dltool"
  acronym-form="singular+short">dltool</span>’s
  <span class="mark">rest_api</span> source covers the cursor pagination
  and incremental loading contract.

- **Dependency-Track** . Category: <span acronym-label="dltool"
  acronym-form="singular+short">dltool</span>. Functional requirements
  ([Dependency-Track
  reference](https://vkraus.github.io/appsec-docs/connectors/sca/dependency-track/)):
  <span acronym-label="rest" acronym-form="singular+short">rest</span>
  access to projects, components, findings, and vulnerabilities. Offset
  pagination. <span class="mark">lastOccurrence</span> high water mark.
  API key header authentication. OpenAPI specification published by the
  project. No Lakeflow Connect integration. The project does not ship a
  first party Python <span acronym-label="sdk"
  acronym-form="singular+short">sdk</span>. Community
  <span acronym-label="sdk" acronym-form="singular+short">sdk</span>
  coverage is thin and partial for the finding retrieval endpoints the
  framework requires. The OpenAPI document informs the
  <span acronym-label="dltool"
  acronym-form="singular+short">dltool</span> source configuration
  directly.

- **TruffleHog** . Category: artifact path, not an
  <span acronym-label="http" acronym-form="singular+short">http</span>
  category. Functional requirements ([TruffleHog
  reference](https://vkraus.github.io/appsec-docs/connectors/secrets/trufflehog/)):
  <span acronym-label="cli" acronym-form="singular+short">cli</span>
  tool with no server <span acronym-label="api"
  acronym-form="singular+short">api</span>. Emits line delimited
  <span acronym-label="json" acronym-form="singular+short">json</span>
  on stdout with per finding <span class="mark">Verified</span> status
  and commit <span acronym-label="sha"
  acronym-form="singular+short">sha</span>. Identical to Semgrep
  (Docker) in ingestion pattern. The <span acronym-label="cicd"
  acronym-form="singular+short">cicd</span> step redirects
  <span class="mark">trufflehog filesystem –json</span> to a file and
  uploads it to the Unity Catalog Volume. The
  <span class="mark">transform.py</span> for the connector reads and
  normalizes it.

- **OWASP ZAP.** Category: artifact path, not an
  <span acronym-label="http" acronym-form="singular+short">http</span>
  category. Functional requirements ([OWASP ZAP
  reference](https://vkraus.github.io/appsec-docs/connectors/dast/owasp-zap/)):
  orchestrate scans against target <span acronym-label="url"
  acronym-form="plural+short">urls</span> and emit a
  <span acronym-label="json" acronym-form="singular+short">json</span>
  report per scan run. In the <span acronym-label="mvp"
  acronym-form="singular+short">mvp</span>, scans are executed in a
  <span acronym-label="cicd" acronym-form="singular+short">cicd</span>
  step that runs the official ZAP image against the target environment
  and uploads the resulting report to a Unity Catalog Volume via
  <span class="mark">databricks fs cp</span> . The
  <span class="mark">transform.py</span> for the connector reads the
  Volume directly. <span class="mark">ingest.py</span> is empty.

- **AWS WAF.** Category: <span acronym-label="sdk"
  acronym-form="singular+short">sdk</span> via boto3 . Functional
  requirements ([AWS WAF
  reference](https://vkraus.github.io/appsec-docs/connectors/waf/aws-waf/)):
  <span class="mark">GetSampledRequests</span> for matched request
  samples over a time window. <span acronym-label="iam"
  acronym-form="singular+short">iam</span> signed
  <span acronym-label="api" acronym-form="singular+short">api</span>
  calls. <span acronym-label="arn"
  acronym-form="singular+short">arn</span> and tag resource
  identification. Event window high water mark. No Lakeflow Connect
  integration. <span class="mark">boto3</span> is the AWS maintained
  <span acronym-label="sdk" acronym-form="singular+short">sdk</span>
  covering every WAF <span acronym-label="api"
  acronym-form="singular+short">api</span> operation, handling
  <span acronym-label="iam" acronym-form="singular+short">iam</span>
  signature construction and pagination.
  <span class="mark">ingest.py</span> calls
  <span class="mark">boto3.client("wafv2").get_sampled_requests</span>
  directly.

<a href="#tab:ingestion-category-assignment"
data-reference-type="autoref"
data-reference="tab:ingestion-category-assignment">[tab:ingestion-category-assignment]</a>
collects the nine assignments alongside the key functional requirement
that drove each choice.

<div id="tab:ingestion-category-assignment">

| **Source**       | **Category**     | **Binding**      | **Decisive requirement**                                                                                                                                                                                                                                                                                                  |
|:-----------------|:-----------------|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ServiceNow       | Lakeflow Connect | platform managed | First party LFC supported source. Full contract met declaratively.                                                                                                                                                                                                                                                        |
| GitHub           | SDK              | PyGitHub         | Mature Python <span acronym-label="sdk" acronym-form="singular+short">sdk</span> covers <span acronym-label="rest" acronym-form="singular+short">rest</span> endpoints,                                                                                                                                                   |
| GitLab           | SDK              | python-gitlab    | Project recognized Python client covers <span acronym-label="rest" acronym-form="singular+short">rest</span> with keyset pagination.                                                                                                                                                                                      |
| SonarQube        | dltool           |                  | No maintained Python <span acronym-label="sdk" acronym-form="singular+short">sdk</span>. <span acronym-label="rest" acronym-form="singular+short">rest</span> only access with offset pagination and                                                                                                                      |
| Semgrep (Docker) | Artifact path    | CI to Volume     | <span acronym-label="cli" acronym-form="singular+short">cli</span> tool with no <span acronym-label="http" acronym-form="singular+short">http</span> <span acronym-label="api" acronym-form="singular+short">api</span>. Ingestion via <span acronym-label="cicd" acronym-form="singular+short">cicd</span> step pattern. |
| Semgrep (Cloud)  | dltool           |                  | No Python <span acronym-label="sdk" acronym-form="singular+short">sdk</span>. Cursor paginated <span acronym-label="rest" acronym-form="singular+short">rest</span> <span acronym-label="api" acronym-form="singular+short">api</span> with                                                                               |
| Dependency-Track | dltool           | OpenAPI driven   | No first party <span acronym-label="sdk" acronym-form="singular+short">sdk</span>. <span acronym-label="rest" acronym-form="singular+short">rest</span> with offset pagination and                                                                                                                                        |
| TruffleHog       | Artifact path    | CI to Volume     | <span acronym-label="cli" acronym-form="singular+short">cli</span> tool with no server <span acronym-label="api" acronym-form="singular+short">api</span>. Ingestion via <span acronym-label="cicd" acronym-form="singular+short">cicd</span> step pattern.                                                               |
| OWASP ZAP        | Artifact path    | CI to Volume     | Scan report <span acronym-label="json" acronym-form="singular+short">json</span> produced in <span acronym-label="cicd" acronym-form="singular+short">cicd</span> and uploaded to Unity Catalog Volume.                                                                                                                   |
| AWS WAF          | SDK              | boto3            | AWS maintained <span acronym-label="sdk" acronym-form="singular+short">sdk</span> covers                                                                                                                                                                                                                                  |

Ingestion category assignment across the nine selected sources, showing
the category chosen for each source and the library or mechanism that
instantiates it.

</div>

Across the nine sources, one resolves to Lakeflow Connect (ServiceNow),
three to an <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> (GitHub, GitLab, AWS WAF),
three to <span acronym-label="dltool"
acronym-form="singular+short">dltool</span> (SonarQube, Semgrep Cloud,
Dependency-Track), and three to the artifact path of
<a href="#sec:ingestion-patterns" data-reference-type="autoref"
data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>
(Semgrep Docker, TruffleHog, OWASP ZAP). Semgrep contributes two
instantiations (Docker <span acronym-label="cli"
acronym-form="singular+short">cli</span> in <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> and the Cloud
<span acronym-label="api" acronym-form="singular+short">api</span>),
which is why the nine selected sources resolve to ten ingestion category
rows.

### Representative Connectors

This section shows the realized structure of a connector at each end of
the category range. ServiceNow represents the Lakeflow Connect case, in
which <span class="mark">ingest.py</span> is empty and the bundle
fragment carries the ingestion specification. GitHub represents the
<span acronym-label="sdk" acronym-form="singular+short">sdk</span> case,
in which <span class="mark">ingest.py</span> composes client calls into
iterators over bronze records.

#### ServiceNow: Lakeflow Connect Pipeline

The ServiceNow connector has no Python ingestion code. Its
<span class="mark">ingest.py</span> carries only a pointer to the bundle
fragment, reproduced in
<a href="#lst:servicenow-ingest" data-reference-type="autoref"
data-reference="lst:servicenow-ingest">[lst:servicenow-ingest]</a>.

``` python
"""ServiceNow ingestion is declarative.

Per thesis section 2.4.1, Lakeflow Connect connectors leave
ingest.py empty. The ingestion is configured in
mvp/resources/servicenow-pipeline.yml as a Databricks Asset
Bundle pipelines resource with an ingestion_definition pointing
at two CMDB tables: cmdb_ci_business_app and cmdb_rel_ci.
"""
```

The bundle fragment in
<a href="#lst:servicenow-pipeline" data-reference-type="autoref"
data-reference="lst:servicenow-pipeline">[lst:servicenow-pipeline]</a>
declares the actual pipeline. Authentication is carried by a
preprovisioned Databricks Connection referenced by name. The
<span class="mark">objects</span> block enumerates the two
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
tables the silver layer consumes and their destination tables in bronze.
Schedule and target catalog come from bundle variables so the same
fragment can promote across dev, staging, and prod.

``` yaml
resources:
  pipelines:
    servicenow_ingest:
      name: servicenow_ingest
      catalog: ${var.catalog}
      target: bronze
      continuous: false
      schedule:
        quartz_cron_expression: "0 0 * * * ?"
        timezone_id: UTC
      ingestion_definition:
        connection_name: ${var.servicenow_connection}
        objects:
          - table:
              source_schema: default
              source_table: cmdb_ci_business_app
              destination_catalog: ${var.catalog}
              destination_schema: bronze
              destination_table: servicenow_business_apps
          - table:
              source_schema: default
              source_table: cmdb_rel_ci
              destination_catalog: ${var.catalog}
              destination_schema: bronze
              destination_table: servicenow_app_cis
```

The framework prescribed connector layout is preserved.
<span class="mark">mapping.yml</span> ,
<span class="mark">config.yml</span> , and
<span class="mark">transform.py</span> continue to govern the
transformation from bronze to silver. Only
<span class="mark">ingest.py</span> changes form, from a Python module
to a declaration embedded in the bundle. That is the exact trade the
Lakeflow Connect category offers. No pagination, authentication, or
retry code written by hand, at the cost of binding the connector to a
platform maintained capability.

#### GitHub: PyGitHub SDK Module

The GitHub connector uses PyGitHub. Its
<span class="mark">ingest.py</span> is reproduced in
<a href="#lst:github-ingest" data-reference-type="autoref"
data-reference="lst:github-ingest">[lst:github-ingest]</a>. Four
exported names make up the interface of the module: a
<span class="mark">github_client</span> factory and three iterator
functions for organization repositories, repository commits, and
repository pull requests. Every iterator yields the raw
<span acronym-label="json" acronym-form="singular+short">json</span>
body returned by the <span acronym-label="api"
acronym-form="singular+short">api</span> via PyGitHub’s
<span class="mark">raw_data</span> attribute, preserving the schema on
read contract for bronze.

``` python
from collections.abc import Iterator
from datetime import datetime

from github import Auth, Github, GithubRetry


def github_client(token: str) -> Github:
    return Github(auth=Auth.Token(token), retry=GithubRetry(total=5))


def fetch_org_repositories(gh: Github, org: str) -> Iterator[dict]:
    for repo in gh.get_organization(org).get_repos():
        yield repo.raw_data


def fetch_repo_commits(gh: Github, repo: str, since: str) -> Iterator[dict]:
    since_dt = datetime.fromisoformat(since.replace("Z", "+00:00"))
    if since_dt.tzinfo is None:
        raise ValueError(
            f"`since` must be a timezone-aware ISO-8601 timestamp: {since!r}"
        )
    for commit in gh.get_repo(repo).get_commits(since=since_dt):
        yield commit.raw_data


def fetch_repo_pulls(gh: Github, repo: str) -> Iterator[dict]:
    pulls = gh.get_repo(repo).get_pulls(
        state="all", sort="updated", direction="desc"
    )
    for pr in pulls:
        yield pr.raw_data
```

Three properties of this module are worth noting. First, authentication,
pagination, and retry are delegated to the client library.
<span class="mark">GithubRetry</span> is PyGitHub’s own
<span class="mark">urllib3.Retry</span> subclass. It recognizes GitHub’s
secondary rate limit signal, which arrives as <span acronym-label="http"
acronym-form="singular+short">http</span> 403 with a
<span class="mark">Retry-After</span> header, and which a plain
<span class="mark">Retry(status_forcelist=\[429, 5xx\])</span> does not
cover. <a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a>
documents the review iteration that established this. Second, the
boundary validation on <span class="mark">since</span> rejects timezone
naive input explicitly rather than letting PyGitHub silently interpret
the value. Third, the functions return iterators over raw dictionaries
rather than PyGitHub objects, so the bronze writer can persist the
<span acronym-label="api" acronym-form="singular+short">api</span>
response verbatim and the silver mapping can operate on stable
<span acronym-label="json" acronym-form="singular+short">json</span>
keys.

The tests in
<span class="mark">tests/connectors/github/test_ingest.py</span> fake
PyGitHub at the object graph level rather than at the
<span acronym-label="http" acronym-form="singular+short">http</span>
level. A test fixture builds <span class="mark">MagicMock</span>
instances modeled on PyGitHub’s <span class="mark">Github</span> ,
<span class="mark">Organization</span> ,
<span class="mark">Repository</span> , and
<span class="mark">PaginatedList</span> classes, each exposing the
attributes the production code calls. The <span acronym-label="http"
acronym-form="singular+short">http</span> stack below PyGitHub is not
exercised. The contract under test is the composition of
<span acronym-label="sdk" acronym-form="singular+short">sdk</span> calls
in the connector, not the <span acronym-label="http"
acronym-form="singular+short">http</span> behavior of the library.

### Aggregate Results

Of the nine sources resolved in
<a href="#sec:ingestion-category-assignment"
data-reference-type="autoref"
data-reference="sec:ingestion-category-assignment">[sec:ingestion-category-assignment]</a>,
two are built as full connectors with four files and pass their local
test suites: ServiceNow on Lakeflow Connect and GitHub on PyGitHub. They
are the representative connectors of
<a href="#sec:impl-representative-connectors"
data-reference-type="autoref"
data-reference="sec:impl-representative-connectors">[sec:impl-representative-connectors]</a>
and exercise opposite ends of the category range. Two artifact path
sources carry partial stubs under
<span class="mark">src/connectors/</span> (
<span class="mark">semgrep/</span> and
<span class="mark">owasp_zap/</span> , each with
<span class="mark">ingest.py</span> ,
<span class="mark">config.yml</span> , and
<span class="mark">mapping.yml</span> but no
<span class="mark">transform.py</span> ). The remaining five carry a
resolved category assignment and a published reference page per source,
and await the repeat of the four step procedure from
<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a>. The
framework contract and the mapping do not change from source to source.
The inputs to the procedure are the reference page per source and the
bundle variables declared in <span class="mark">databricks.yml</span> .
The outputs are the <span class="mark">src/connectors/\<source\>/</span>
folder and a bundle fragment under <span class="mark">resources/</span>
.

The test evidence distributes asymmetrically between the two built
connectors. The ServiceNow connector has no Python ingestion to
unit-test. The contract under validation is the bundle fragment parsing
and the <span class="mark">mapping.yml</span> driven transform, which
runs against bronze rows produced by Lakeflow Connect at workspace time.
The GitHub connector has the full iterator set unit-tested against fake
PyGitHub clients. This asymmetry is intrinsic to the category choice,
not a testing gap. Lakeflow Connect shifts the ingestion contract from
Python code to a platform configuration.

### Discussion

#### Contract of three categories

Every source in the sample resolved to exactly one of Lakeflow Connect,
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>, or
<span acronym-label="dltool"
acronym-form="singular+short">dltool</span>, with the two
<span acronym-label="cli" acronym-form="singular+short">cli</span> only
tools falling into the artifact path carve-out defined in
<a href="#sec:ingestion-patterns" data-reference-type="autoref"
data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>. No
source required a category the framework does not admit. The ingestion
category assignment in <a href="#sec:ingestion-category-assignment"
data-reference-type="autoref"
data-reference="sec:ingestion-category-assignment">[sec:ingestion-category-assignment]</a>
is the operational demonstration of this, and the two implemented
connectors in <a href="#sec:impl-representative-connectors"
data-reference-type="autoref"
data-reference="sec:impl-representative-connectors">[sec:impl-representative-connectors]</a>
show that the assignment is realizable in working code.

**Lakeflow Connect and <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> categories produce visibly
different connector layouts.** The ServiceNow connector has no Python
ingestion file of substance. The GitHub connector has a small, flat
<span class="mark">ingest.py</span> composed of
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>
calls. Both preserve the module layout with four files prescribed by the
framework. The difference lives in <span class="mark">ingest.py</span>
content and in which kind of <span acronym-label="dab"
acronym-form="singular+short">dab</span> resource (
<span class="mark">pipelines</span> or <span class="mark">jobs</span> )
declares the scheduling. This is the trade the framework makes explicit:
the Lakeflow Connect category absorbs ingestion into the platform at the
cost of platform lockin, and the <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> category keeps ingestion
visible in Python at the cost of maintaining client knowledge for each
source.

#### Declarative mapping

Both connectors share the severity and status normalization helpers in
<span class="mark">src/common/silver.py</span> and keep severity and
status lookup tables as YAML under
<span class="mark">config/severity/</span> and
<span class="mark">config/status/</span> , decoupled from connector
code. The transformation code per source (
<span class="mark">transform.py</span> ) builds the Silver DataFrame
field by field and calls the shared helpers. Adding or re-mapping a
field in the ServiceNow or GitHub connector is currently a Python edit
to the relevant <span class="mark">transform.py</span> . The
<span class="mark">mapping.yml</span> file documents the intended
derivation. Aligning the MVP with the declarative mapping prescription
of <a href="#sec:transformation-patterns" data-reference-type="autoref"
data-reference="sec:transformation-patterns">[sec:transformation-patterns]</a>
is a <a href="#sec:future-work" data-reference-type="autoref"
data-reference="sec:future-work">[sec:future-work]</a> thread.

#### Unsanctioned category failure mode

During an earlier phase of the implementation, a shared
<span acronym-label="http" acronym-form="singular+short">http</span>
primitive module was added under <span class="mark">src/common/</span>
to back the ServiceNow and GitHub connectors. That module was a fourth
ingestion category, which the framework explicitly does not admit, and
would have rendered the category assignment in
<a href="#sec:ingestion-category-assignment"
data-reference-type="autoref"
data-reference="sec:ingestion-category-assignment">[sec:ingestion-category-assignment]</a>
nonbinding. The implementation phase review caught the drift, and the
module was retired.
<a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a>
classifies this iteration and two smaller ones against the three way
rubric formalized in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>.

#### Iteration Summary

This subsection collects implementation phase iterations that were
caught by review rather than passing on the first attempt. Each is
classified against the three way rubric formalized in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>. **Framework gap** means
extending the framework specification would have prevented the issue and
would plausibly generalize. **Source quirk** means the correction is
source specific noise not attributable to the framework. **Environment
glue** means the issue concerns setup, authentication, or infrastructure
outside the scope of the framework.

- **Shared <span acronym-label="http"
  acronym-form="singular+short">http</span> primitive module
  retirement.** A <span class="mark">src/common/bronze.py</span> module
  had been introduced to carry an <span acronym-label="http"
  acronym-form="singular+short">http</span> client written by hand with
  offset and cursor paginators, consumed by the ServiceNow and GitHub
  connectors. Relative to
  <a href="#sec:connector-abstraction" data-reference-type="autoref"
  data-reference="sec:connector-abstraction">[sec:connector-abstraction]</a>,
  this was a fourth ingestion category. The correction had two parts:
  the ServiceNow connector was moved to a Lakeflow Connect
  <span class="mark">pipelines</span> resource
  (<a href="#sec:impl-servicenow-connector" data-reference-type="autoref"
  data-reference="sec:impl-servicenow-connector">[sec:impl-servicenow-connector]</a>),
  and the GitHub connector was rewritten on PyGitHub
  (<a href="#sec:impl-github-connector" data-reference-type="autoref"
  data-reference="sec:impl-github-connector">[sec:impl-github-connector]</a>).
  The shared module was deleted. **Framework gap.** The framework
  specification in
  <a href="#sec:connector-abstraction" data-reference-type="autoref"
  data-reference="sec:connector-abstraction">[sec:connector-abstraction]</a>
  names the three admissible categories and their evaluation order, and
  a project rule in the <span acronym-label="mvp"
  acronym-form="singular+short">mvp</span> guidance file mirrors the
  same constraint, yet an earlier implementation step still introduced
  the fourth category. The framework could hold, without adding new
  substance, a more visible guard: a single enforceable rule that no
  Python module under <span class="mark">src/</span> may write
  <span acronym-label="http" acronym-form="singular+short">http</span>
  calls by hand for ingestion, checked as part of the connector testing
  layer.

- **GitHub rate limit handling.** The initial PyGitHub rewrite
  configured the client with
  <span class="mark">urllib3.Retry(status_forcelist=\[429, 500, 502,
  503, 504\])</span> . A code review pass identified that GitHub signals
  secondary rate limits with <span acronym-label="http"
  acronym-form="singular+short">http</span> 403 and a
  <span class="mark">Retry-After</span> header, which
  <span class="mark">urllib3.Retry</span> does not recognize as
  retryable. The fix replaced the retry object with PyGitHub’s own
  <span class="mark">GithubRetry</span> subclass, which handles the 403
  response format. **Source quirk.** The deviation is specific to
  GitHub’s published response contract, not to the
  <span acronym-label="sdk" acronym-form="singular+short">sdk</span>
  category in general.

- **Boundary validation on <span class="mark">since</span> .**
  <span class="mark">fetch_repo_commits</span> accepted an ISO-8601
  timestamp string and parsed it through
  <span class="mark">datetime.fromisoformat</span> . A date only input
  such as <span class="mark">"2026-04-01"</span> parses into a timezone
  naive <span class="mark">datetime</span> , which PyGitHub would treat
  differently from the timezone aware values callers normally pass. The
  function now raises <span class="mark">ValueError</span> when the
  parsed value has no <span class="mark">tzinfo</span> . **Framework
  gap.** The connector contract in
  <a href="#sec:connector-abstraction" data-reference-type="autoref"
  data-reference="sec:connector-abstraction">[sec:connector-abstraction]</a>
  requires that ingest functions reject malformed incremental state
  inputs at the boundary rather than propagating them. A generic
  boundary validation helper in <span class="mark">src/common/</span>
  would have carried this invariant for every source.

Two of the three iterations classify as framework gaps, and both point
at the same kind of missing primitive: an enforced boundary between
<span class="mark">src/common/</span> and the connectors for each
source. One classifies as a source quirk and was caught at review cost.
None classify as environment glue. The Conclusion in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> lifts these findings to a
defended claim about where the framework holds and where it admits
further specification.

## Conclusion

### Thesis Outcomes and Contributions

This thesis delivers the three contributions announced in the abstract,
each grounded in a dedicated chapter, and evaluated against the design
science framing of and the outcome evaluation guidance of . The first
contribution is a **requirements specification** for an application
security data platform.
<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> motivates the
specification, surveys the data sources and integration patterns that
inform it, and catalogs the functional and nonfunctional requirements it
must satisfy. The specification text itself was externalized to the
product documentation site rather than carried as a thesis appendix, and
<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> links into that site at
the relevant points. The second contribution is a **reusable and
extensible framework** delivered in
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>, covering the reference
architecture, the data model, and the medallion based pipeline  that
carries source records through to the consumption layer. The third
contribution is a **reference implementation** delivered in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>, built on the
Databricks platform and instantiating the framework against two
representative sources.

The reusability and extensibility claim of the framework is defended
empirically by
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>. The
reference implementation instantiates the framework against two sources
with distinct integration patterns. ServiceNow is ingested through
Lakeflow Connect as a managed connector, and GitHub is ingested through
PyGitHub under the connector contract specified in
<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>.
The framework is **reusable** in the concrete sense that
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> introduced no
new connector level design decisions beyond the choice of which sources
to onboard. Every architectural question had already been answered by
the framework contract. The framework is **extensible** in the concrete
sense that onboarding a further source reduces to the four step
procedure described in
<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a>. That
procedure covers ingestion category resolution, module instantiation per
connector, declarative mapping, and layered testing, and it leaves no
design work at the connector level.

The decision to externalize the requirements specification to the
[product documentation site](https://vkraus.github.io/appsec-docs/) is
deliberate. It keeps the specification reviewable and updatable on its
own cadence, independently of the thesis manuscript, and it lets
downstream consumers track changes without reprinting a frozen appendix.
The thesis chapters link into the site at the points where a requirement
is first introduced, so the narrative remains self contained for a
reader who follows only the printed text, while the requirement text
remains a single source of truth for the implementation.

### Evaluation of the AI Instantiability Claim

<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> committed the artifacts
of the framework to a declarative form intended to be consumable by an
<span acronym-label="ai" acronym-form="singular+short">ai</span> coding
agent. The original Methodology target was fully autonomous generation
of the reference implementation from the [skill catalog on the
documentation
site](https://vkraus.github.io/appsec-docs/connectors/scm/skills/). The
reference implementation delivered in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> was produced
by <span acronym-label="ai" acronym-form="singular+short">ai</span>
assisted direct coding against the framework contract and the external
requirements specification. Invocations of the published skill catalog
were attempted during the build. They required iterative amendment at
every connector and did not produce the delivered artifact without
supervision. This section states what that weaker empirical path does
and does not establish.

#### Acceptance rubric

A correction counts as a **framework gap** when two conditions hold.
Extending the framework specification (schema pattern, connector
contract, or declarative artifact such as
<span class="mark">mapping.yml</span> ) would have produced the right
output on first pass, and the extension would generalize to other
sources in the same category. Corrections that trace to source specific
noise (**source quirks**) or to setup and authentication plumbing
outside scope (**environment glue**) do not count against the framework.

#### Empirical outcome

<a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a>
enumerates the iteration cases observed during the build of the
ServiceNow and GitHub connectors by direct coding. Two of the three
classify as framework gaps, and both point at the same missing
primitive. There is no enforced boundary between
<span class="mark">src/common/</span> and connectors for each source
that would prevent the reintroduction of an ingestion path written by
hand. One case classifies as a source quirk and was caught at review
cost. None classify as environment glue.

#### Claim defended

The framework is <span acronym-label="ai"
acronym-form="singular+short">ai</span> **instantiable** under skill
catalog invocation with <span acronym-label="ai"
acronym-form="singular+short">ai</span> assisted supervision. The
framework contract, the mapping, and the module layout per connector
together reduce new connector work to a four step procedure
(<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a>) that
converges with bounded supervision. The framework is not yet
<span acronym-label="ai" acronym-form="singular+short">ai</span>
**autonomous**. The empirical build required review cycles on every
connector, the framework gaps in
<a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a> have
not been closed, and the invocations of the published skill catalog
required iterative amendment at every connector rather than sustaining
themselves end to end. Closing the framework gaps and fine tuning the
skill catalog until invocations are self sustaining would measure the
distance from instantiable to autonomous. That is the subject of Future
Work.

#### Provenance

The iteration log that supports this evaluation is disclosed in
<a href="#app:genai" data-reference-type="autoref"
data-reference="app:genai">[app:genai]</a>.

### Limitations

The **scope of validation** is narrower than the scope of the framework.
Of the nine sources selected in
<a href="#sec:selected-sources" data-reference-type="autoref"
data-reference="sec:selected-sources">[sec:selected-sources]</a>, only
two were built as working connectors, namely ServiceNow and GitHub. The
remaining seven sit in the catalog of the framework as declared schema
and mapping artifacts without a live ingestion path. The reference
implementation is also **platform specific**. It runs on Databricks over
AWS object storage, and that is the only combination of runtime and
cloud that has been exercised end to end. The connector contract in
<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>
is written to be cloud agnostic and platform agnostic in principle, yet
it has not been ported to Snowflake, to Microsoft Fabric, or to an on
premises platform. The portability claim of the framework therefore
rests on the design of the contract, not on a second implementation.

The **reproducibility** of the reference implementation rests on
preconditions that are enumerated on the product documentation site
rather than in the thesis itself. An independent replication requires a
Databricks workspace with Unity Catalog enabled, an AWS account with an
S3 bucket and object storage credentials federated into the workspace, a
Lakeflow Connect entitlement on that workspace, a ServiceNow developer
instance with an API capable user, and a GitHub Personal Access Token
scoped to the organization under test. The infrastructure is
bootstrapped by a Terraform module carried in
<span class="mark">mvp/terraform/</span> and the pipeline is deployed by
a Databricks Asset Bundle. Both expect a target prefix and credentials
as input variables. A reader who retains only the submitted
<span class="mark">mvp.zip</span> and <span class="mark">docs.zip</span>
cannot reproduce the build without the workspace entitlements listed
above.

The **instrument measurement conflict** in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> is real and not mitigated
by the acceptance rubric. The framework specification, the skill
catalog, the delivered reference implementation, and the iteration log
that grades the framework’s fitness are all authored by the same
operator in the same session, so the framework was revised in response
to the iteration outcomes that the evaluation then treats as
measurements of the framework’s fitness. Under this loop, a verdict that
"framework gaps were caught" is unfalsifiable. A blind operator applying
a frozen version N of the specification to source 10 would produce a
stronger measurement. That measurement is the controlled user study
queued in <a href="#sec:future-work" data-reference-type="autoref"
data-reference="sec:future-work">[sec:future-work]</a>.

The **sampled heterogeneity** of the Selected Nine is biased toward REST
JSON APIs with token authentication. Seven of the nine sources
(ServiceNow, GitHub, GitLab, SonarQube, Dependency-Track, OWASP ZAP, AWS
WAF) fall into this category, which is also the category Lakeflow
Connect and maintained Python SDKs support. The two artifact file
sources (Semgrep CLI, TruffleHog) deliver reports via S3 rather than an
interactive API. Source categories that the framework has **not** been
demonstrated against include SOAP APIs, gRPC, syslog streams, Kafka
event streams, binary protocol telemetry, and push only webhook native
sources. The contract in
<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>
is written to accommodate these categories, but the evidence supporting
that claim is category by category absent.

The **threats to validity** of the empirical claims are correspondingly
concrete. The reference implementation has not been deployed into a
production security operation, so claims about operability rest on
design rather than on observed behavior under real load. The
<span acronym-label="ai" acronym-form="singular+short">ai</span>
instantiability evaluation in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> rests on a build of two
connectors by a single operator, which is a demonstration rather than a
controlled study across operators or sources. The iteration data
summarized in
<a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a> is
observational and does not establish a statistical bound on the rate at
which framework gaps occur. The published skill catalog on the product
documentation site was invoked during the MVP build but its invocations
required iterative amendment at every connector rather than sustaining
themselves end to end, which leaves its fitness for autonomous
instantiation unproven.

### Future Work

The most immediate thread is **closing the framework gaps** identified
in <a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a>. Both
gaps trace to the same missing primitive, an enforced boundary between
<span class="mark">src/common/</span> and connectors for each source. A
structural remedy, a connector contract that mechanically prevents the
reintroduction of ingestion paths written by hand, would remove the
class of regression that the review cycles in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> had to catch by hand.
Closing those gaps is the precondition for any stronger
<span acronym-label="ai" acronym-form="singular+short">ai</span>
autonomy claim.

A closely related thread is **completing the declarative mapping
applicator**. The transformation patterns prescription in
<a href="#sec:transformation-patterns" data-reference-type="autoref"
data-reference="sec:transformation-patterns">[sec:transformation-patterns]</a>
treats the <span class="mark">mapping.yml</span> in each connector as
the authoritative specification from bronze to silver consumed by a
generic applicator, but the MVP implements the transformation field by
field in the <span class="mark">transform.py</span> of each connector
(<a href="#sec:impl-discussion" data-reference-type="autoref"
data-reference="sec:impl-discussion">[sec:impl-discussion]</a>).
Completing the applicator so that <span class="mark">mapping.yml</span>
drives the Silver DataFrame construction would close the gap between the
framework contract and the realized code, and would make the addition
cost per source a configuration edit rather than a code edit.

The third thread is **refining the published skill catalog**. The shape
is settled. The catalog uses three role wide skills with specialization
per category in <span class="mark">references/\<category\>.md</span> ,
defended at the close of
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> against the recommended
pattern for skills that span multiple variants of the same task.
Structural redesign is no longer in scope. What remains is content
tuning. The catalog was invoked during the MVP build but every connector
required iterative amendments to the skill outputs before the delivered
artifact converged. Tightening the preconditions asserted in each
<span class="mark">SKILL.md</span> and widening the worked examples
carried in each reference file per category would reduce the amendment
cost per invocation. Running the refined catalog against the remaining
seven sources from
<a href="#sec:selected-sources" data-reference-type="autoref"
data-reference="sec:selected-sources">[sec:selected-sources]</a> would
then produce a direct measurement of the distance between
<span acronym-label="ai" acronym-form="singular+short">ai</span>
instantiable (demonstrated) and <span acronym-label="ai"
acronym-form="singular+short">ai</span> autonomous (claimed as future).

The fourth thread is **building connectors for the remaining seven
Selected Nine**. GitLab, SonarQube, Semgrep, Dependency-Track,
TruffleHog, OWASP ZAP, and AWS WAF are resolved to ingestion categories
in <a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> but sit as
declared schema and mapping without a live connector. Building them
would test whether the four step procedure from
<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a>
generalizes beyond the ticketing and code hosting categories that the
reference implementation exercised.

The fifth thread is **platform portability**. The reference
implementation runs only on Databricks over AWS. A second implementation
on Snowflake or Microsoft Fabric would validate the portability claim of
the connector contract empirically rather than on contract design alone,
and would expose any residual coupling to Databricks specific runtime
assumptions.

The sixth thread is **downstream analytics on the gold layer**. The gold
tables are positioned for consumption but no consumer has been
implemented against them. Large Language Model assisted triage and
correlation over the gold layer is a natural extension and would
exercise the data model in the direction it was designed for.

The seventh thread is a **controlled user study**. The
<span acronym-label="ai" acronym-form="singular+short">ai</span>
instantiability evaluation is a demonstration by a single operator, and
a study across multiple operators, or across sources handed to operators
blind, would produce statistical evidence rather than existence proof
evidence.

The eighth thread is **real connector state persistence**. The
<a href="#sec:connector-contract" data-reference-type="autoref"
data-reference="sec:connector-contract">[sec:connector-contract]</a>
contract wrappers accept and return
<span class="mark">ConnectorState</span> and
<span class="mark">BatchDescriptor</span> values but do not yet persist
high water marks to a Unity Catalog control table. First run semantics
are implicit. Materialising the control table and wiring high water mark
read and write into the <span acronym-label="dab"
acronym-form="singular+short">dab</span> job driver closes this gap.

# Appendices

## Generative AI Use Disclosure

This appendix expands the Declaration on the Use of Artificial
Intelligence from the front matter of this thesis. The five sections
below disclose each use in the same order. The central use is the
<span acronym-label="ai" acronym-form="singular+short">ai</span>
assisted direct coding of the reference implementation
(<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>), which is
evaluated in <a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> rather than disclosed
here as incidental assistance.

The grammar and language style assistance described in the first section
below used the Overleaf <span acronym-label="ai"
acronym-form="singular+short">ai</span> assistant on the thesis
manuscript. All other <span acronym-label="ai"
acronym-form="singular+short">ai</span> assistance reported in this
appendix used Claude models (Anthropic) accessed through the Claude Code
<span acronym-label="cli" acronym-form="singular+short">cli</span>, with
model versions spanning Claude Opus 4.5 through Claude Opus 4.7 over the
drafting period of the thesis.

### Grammar and Language Style

**Declaration item 1.** This section discloses the use described as
improvement of grammar, language style, and conciseness of the thesis.

<span acronym-label="ai" acronym-form="singular+short">ai</span>
assistance was used for grammar checking, style refinement, and copy
editing passes over prose I had already authored. I ran the assistant
over drafts to identify infelicities, tighten phrasing, and flag
inconsistencies, and I accepted, rejected, or revised the suggestions. I
reviewed and edited every paragraph in the submitted document. I did not
use the assistant as an autonomous writer.

Several review passes were run across the full manuscript to bring the
thesis to its target length. These passes rephrased longer prose into
more concise wording and relocated noncore detail into the attached
product documentation, which carries the requirements specification and
the reference material per source. The restructuring decisions were
mine. The assistant proposed candidate cuts and rephrasings that I
accepted, rejected, or revised.

The research question, chapter structure, contributions, and
argumentative framing are mine. Literature selection, claim positioning
against prior work
(<a href="#sec:related-work" data-reference-type="autoref"
data-reference="sec:related-work">[sec:related-work]</a>), and the
conceptual domain model
(<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a>) are human
authored decisions.

### Images and Other Media

**Declaration item 2.** This section discloses the use described as
generation of images and other media in the thesis.

I wrote some TikZ figures from scratch. Others the assistant drafted
from a description of the content and layout, and I revised them for
correctness and readability. A third group I wrote, then accepted
readability suggestions the assistant proposed. Per figure attribution
lives in the git history of each figure file under
<span class="mark">figures/</span> .

### Product Documentation (`docs.zip`)

**Declaration item 3.** This section discloses the use described as
generation of product documentation attached to the thesis (`docs.zip`).

The [external requirements
specification](https://vkraus.github.io/appsec-docs/), attached as
`docs.zip`, is a mix of human authored and <span acronym-label="ai"
acronym-form="singular+short">ai</span> assisted content. I authored the
per category capability matrix, canonical mapping, and reference
sections per source with targeted <span acronym-label="ai"
acronym-form="singular+short">ai</span> assistance for drafting and
consistency passes. I authored the three skill files on the [skills
page](https://vkraus.github.io/appsec-docs/connectors/scm/skills/). I
iterated each one until it produced acceptable output against
representative sources. I did not generate any of the submitted skills
with another <span acronym-label="ai"
acronym-form="singular+short">ai</span> invocation.

### Source Code (`mvp.zip`)

**Declaration item 4.** This section discloses the use described as
generation of source code attached to the thesis (`mvp.zip`).

The reference implementation in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> (submitted as
`mvp.zip`) was built by directly coding against the framework contract
(<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>) and the external
requirements specification, with <span acronym-label="ai"
acronym-form="singular+short">ai</span> assistance from Claude Code used
conversationally through a brainstorm, plan, and execute loop. Specs and
plans for the two connectors delivered (ServiceNow and GitHub) are
committed under <span class="mark">docs/superpowers/</span> in the
<span class="mark">appsec-mvp</span> repository. The iteration cases
documented in
<a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a> are
the empirical record of this use. This is my central
<span acronym-label="ai" acronym-form="singular+short">ai</span> use.
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> evaluates it. The three
skill files published on the [documentation
site](https://vkraus.github.io/appsec-docs/connectors/scm/skills/) (
<span class="mark">analyze-source</span> ,
<span class="mark">generate-connector</span> ,
<span class="mark">validate-implementation</span> ) are authored as part
of the requirements specification and are framework consumable in
principle, but they were not used to generate the delivered code.
Empirical validation of the skill catalog as a generator remains open
(<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>).

### Supporting Tooling

**Declaration item 5.** This section discloses the use described as
assistance with supporting tooling not submitted with the thesis.

I used <span acronym-label="ai" acronym-form="singular+short">ai</span>
assistance at the line level on artifacts that are not part of the
submitted `mvp.zip` or `docs.zip`: the LaTeX build scripts and
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
configuration, the sweep tooling that converted inline
<span class="mark">\texttt</span> in body text to
<span class="mark">\inlinecode</span> , and local scripts for plan
execution. This assistance is not the subject of the
<span acronym-label="ai" acronym-form="singular+short">ai</span>
instantiability claim in the thesis.
