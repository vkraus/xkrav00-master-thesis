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
- [Artifacts](#artifacts)
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
  - [Source Inventory](#source-inventory)
  - [Considered and Excluded](#considered-and-excluded)
  - [Cross Source Synthesis](#cross-source-synthesis)
- [Requirements Summary](#requirements-summary)
  - [Framework](#framework)
- [Solution Architecture](#solution-architecture)
  - [Technology Stack](#technology-stack)
  - [Component Design](#component-design)
  - [Medallion Architecture](#medallion-architecture)
        - [Bronze Layer](#bronze-layer)
        - [Silver Layer](#silver-layer)
        - [Gold Layer](#gold-layer)
- [Data Model](#data-model)
  - [Source Synthesis](#source-synthesis)
  - [Schema Patterns](#schema-patterns)
        - [Bronze envelope](#bronze-envelope)
        - [Silver entity pattern](#silver-entity-pattern)
        - [Silver finding pattern](#silver-finding-pattern)
        - [Deduplication](#deduplication)
        - [Relationship pattern](#relationship-pattern)
        - [Gold aggregation](#gold-aggregation)
  - [Entity Model](#entity-model)
        - [Entity Tables](#entity-tables)
        - [Finding Table](#finding-table)
        - [Reference and Relationship Tables](#reference-and-relationship-tables)
  - [Aggregation Model](#aggregation-model)
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
- [Extension Blueprint and AI Assistance](#extension-blueprint-and-ai-assistance)
  - [MVP Implementation](#mvp-implementation)
- [Methodology](#methodology-1)
- [Project Structure](#project-structure-1)
  - [Layering rule](#layering-rule)
  - [Component colocation](#component-colocation)
- [Ingestion Category Assignment](#ingestion-category-assignment)
- [Representative Connectors](#representative-connectors)
  - [ServiceNow: Lakeflow Connect Pipeline](#servicenow-lakeflow-connect-pipeline)
  - [GitHub: PyGitHub SDK Module](#github-pygithub-sdk-module)
- [Aggregate Results](#aggregate-results)
- [Discussion](#discussion)
  - [Contract of three categories](#contract-of-three-categories)
  - [Declarative mapping](#declarative-mapping)
  - [Iteration Summary](#iteration-summary)
  - [Conclusion](#conclusion)
- [Thesis Outcomes and Contributions](#thesis-outcomes-and-contributions)
- [Evaluation of AI Instantiability](#evaluation-of-ai-instantiability)
  - [Acceptance criterion](#acceptance-criterion)
  - [Empirical outcome](#empirical-outcome)
  - [Claim defended](#claim-defended)
- [Limitations](#limitations)
- [Future Work](#future-work)
  - [Implementation backlog](#implementation-backlog)
  - [Research extensions](#research-extensions)
- [Appendices](#appendices)
  - [Generative AI Use Disclosure](#generative-ai-use-disclosure)
- [Text Editing](#text-editing)
- [Images](#images)
- [Source Code (`appsec-mvp.zip`)](#source-code-appsec-mvpzip)
- [MVP Documentation (`appsec-mvp-docs.zip`)](#mvp-documentation-appsec-mvp-docszip)
- [Supporting Tools](#supporting-tools)

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

Prague, May 2026

</div>

### Declaration on the Use of Artificial Intelligence

I confirm that artificial intelligence tools were used in the
preparation of the submitted work. Specifically, they were used in the
following ways:

- improvement of grammar, language style, and conciseness of the thesis,
  including review cycles that shortened the text by rephrasing longer
  passages and relocating details into the MVP documentation attached to
  this thesis,

- generation of TikZ source code for figures from author sketches and
  descriptions,

- generation of source code attached to this thesis (`appsec-mvp.zip`),

- generation of MVP documentation attached to this thesis
  (`appsec-mvp-docs.zip`),

- assistance with the LaTeX build scripts.

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

To protect their business critical applications from cybersecurity
threats, enterprise security teams rely on numerous tools to detect and
resolve vulnerabilities in application source code, configuration,
dependencies, CI/CD pipelines, and runtime infrastructure. These tools
use different integration patterns, protocols, and data formats, making
it difficult to consistently parse, deduplicate, triage, and group their
findings. In large environments, additional challenges emerge when
linking all findings to the corresponding business applications. This
thesis presents a data framework to tackle those challenges, delivering
three distinct contributions: (1) a requirements specification for an
application security data platform, (2) a reusable and extensible design
covering architecture, data model, and medallion based data pipeline,
and (3) a Databricks MVP reference implementation with generated
connector modules for nine selected sources at various maturity levels.
Together, these contributions offer application security teams
a foundation for building a robust data platform independent of
individual cybersecurity vendors.

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
and tens of thousands of repositories, I have seen firsthand how
difficult such environment is to secure. Two classes of difficulty
dominate.

The first is **detection diversity**. Tools in the same category scan
differently and produce different results, so a single tool is rarely
sufficient . Running multiple tools in parallel improves coverage but
creates the opposite problem: the same vulnerability is reported several
times, and findings must be deduplicated before they can be triaged or
counted .

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
fragment data and do not scale across dozens of tools, and pull based
<span acronym-label="api" acronym-form="singular+short">api</span>
connectors, where they exist, are usually gated behind commercial
tiers .

Consolidating application security data is a data engineering problem.
Industry addresses it with commercial <span acronym-label="aspm"
acronym-form="singular+short">aspm</span> products offering dashboards
and aggregated views , but these are proprietary products with limited
customer control over internal pipelines. They can create security tool
vendor lock in and constrain security teams that need to customize
pipelines, apply their own <span acronym-label="ml"
acronym-form="singular+short">ml</span> models, or integrate with
internal systems.

The most notable open source alternative, DefectDojo, is a Django based
vulnerability management web application , not a data first platform.
Its relational backend limits scale, and ingestion relies mostly on push
based integrations or manual uploads. Pull based
<span acronym-label="api" acronym-form="singular+short">api</span>
connectors exist only in the commercial DefectDojo Pro tier.

Databricks Lakewatch, announced in March 2026 and available in Private
Preview at thesis submission, is a lakehouse native
<span acronym-label="siem" acronym-form="singular+short">siem</span> .
It runs on the same lakehouse platform this thesis adopts but addresses
a different domain: runtime threat detection, alert triage, and log
analytics, not application security posture. The author did not have
access to the Private Preview during thesis preparation, so Lakewatch is
treated as related product context rather than implementation evidence.
The distinction is discussed
in <a href="#sec:lakewatch" data-reference-type="autoref"
data-reference="sec:lakewatch">[sec:lakewatch]</a>.

Enterprise security teams need a governed data platform that keeps
findings, ownership, business criticality, and remediation state
together. This thesis proposes such a framework for application security
data. It is independent of individual security tool vendors and their
proprietary risk models, but the submitted <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> is Databricks based.
Portability to another platform is a design claim bounded in the
Limitations section.

The intended reduction is practical: onboarding a new source should
follow the five step connector procedure in
<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a>, not
require a pipeline redesign. The <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> does not yet complete every
part of that reduction. In particular, step three of the procedure still
applies Silver mappings through Python and Spark code rather than
through the planned generic mapping applicator. Future Work records that
applicator as the consolidation that closes this gap.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> and
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> evaluate how far the
reduction holds in the evidence gathered for this thesis.

The central research question is: **how can diverse enterprise
application security findings be consolidated into a unified, security
tool vendor agnostic data model and integration framework that serves
the analytical and operational needs of security teams?**

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
    gap, select source systems to carry forward, and summarize the
    derived requirements. The <span acronym-label="api"
    acronym-form="singular+short">api</span> analysis per source
    grounding these findings is collected on the external [documentation
    site](https://vkraus.github.io/appsec-mvp/).

2.  **Framework** (<a href="#ch:framework" data-reference-type="autoref"
    data-reference="ch:framework">[ch:framework]</a>): Use the
    requirements summary to propose a reusable blueprint covering
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
    a Databricks reference implementation for the nine selected sources.
    Each source has the generated connector artifact set: configuration,
    ingest and transform modules, mappings, bundle resources, source
    runtime where applicable, and requirement bound tests. The source
    evidence is mixed. Live exercise and Spark wrapper completeness
    differ by source and are stated in
    <a href="#sec:impl-results" data-reference-type="autoref"
    data-reference="sec:impl-results">[sec:impl-results]</a> and in the
    Limitations section. The implementation also includes the platform
    app to repository linker and analytics and serving artifacts. The
    [traceability
    matrix](https://vkraus.github.io/appsec-mvp/platform/reference/catalog/)
    records PASS or N/A for every (requirement $\times$ source) cell.
    The deliverable is a minimum viable product on a sample chosen to
    cover the ingestion and integration patterns, not an exhaustive
    integration of every security tool.

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
testing. **Runtime security** covers observational telemetry from
production systems. One representative source (AWS WAF sampled
requests ) is included so the model covers runtime findings linked to
applications through deployment metadata, although live WAF tenant
exercise remains outside the submitted evidence. Broader runtime
operations (threat detection, incident response, log analytics) are out
of scope.

<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> and
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> are framed against the
full <span acronym-label="aspm"
acronym-form="singular+short">aspm</span> scope.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> applies the
framework to the nine sources selected in
<a href="#sec:selected-sources" data-reference-type="autoref"
data-reference="sec:selected-sources">[sec:selected-sources]</a> at the
<span acronym-label="mvp" acronym-form="singular+short">mvp</span>
evidence levels reported in
<a href="#sec:impl-results" data-reference-type="autoref"
data-reference="sec:impl-results">[sec:impl-results]</a>. Onboarding a
tenth source repeats the procedure described in
<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a> without
changes to the framework.

The intended audience is application security architects and data
platform engineers who need to consolidate security findings at scale
without lockin to one application security tool vendor.

### Methodology

This thesis follows the design science research methodology of  in three
phases aligned with the main chapters. The **analysis** phase combines a
literature review with a systematic study of source systems, identifies
the research gap, and summarizes the derived requirements. The
**framework** phase designs the architecture, data model, connector
contract, and analytics patterns. The **implementation** phase evaluates
supervised <span acronym-label="ai"
acronym-form="singular+short">ai</span> assisted connector artifact
generation for the integration layer of the reference implementation. In
this thesis, <span acronym-label="ai"
acronym-form="singular+short">ai</span> instantiable means that a human
supervised coding agent can generate connector artifacts from the
framework templates and pass the specified review and test cycle. A
prompt based chain of four skills (analyze-source, provision-source,
generate-connector, validate-implementation) was authored from the
connector contract and run across all nine source specifications under
reviewer subagent supervision.

The thesis delivers three contributions: (1) a **requirements
specification**, (2) a **reusable framework** covering architecture,
data model, connector contract, and analytics and serving patterns, and
(3) a **Databricks MVP reference implementation** with generated
connector modules for nine selected sources.
<a href="#sec:impl-results" data-reference-type="autoref"
data-reference="sec:impl-results">[sec:impl-results]</a> reports the
evidence level for each source, and
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> evaluates the
<span acronym-label="ai" acronym-form="singular+short">ai</span>
instantiability claim.

### Structure

<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> surveys the problem
domain and closes with related work, gap analysis, source selection, and
the requirements summary.
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> gives the architecture,
data model, connector framework, and analytics and serving framework.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> reports the
<span acronym-label="mvp" acronym-form="singular+short">mvp</span>
reference implementation against the nine selected sources. The
Conclusion evaluates the objectives, defends the
<span acronym-label="ai" acronym-form="singular+short">ai</span>
instantiability claim in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>, and records limitations
and future work. <a href="#app:genai" data-reference-type="autoref"
data-reference="app:genai">[app:genai]</a> discloses the use of
generative <span acronym-label="ai"
acronym-form="singular+short">ai</span> tooling.
<a href="#fig:contribution-flow" data-reference-type="autoref"
data-reference="fig:contribution-flow">[fig:contribution-flow]</a>
summarizes the contribution flow.

<div class="center">

\[Thesis contribution flow\]Thesis contribution flow.
<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> and
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> contribute to the
Requirements Specification published on the documentation site.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> consumes the
specification, with reviewer subagent cycles catching defect classes
evaluated in <a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>. Implementation results
populate the Implementation reports for each source on the site (dashed
return arrow). <span id="fig:contribution-flow"
label="fig:contribution-flow"></span>

</div>

### Artifacts

Throughout the thesis, **<span acronym-label="mvp"
acronym-form="singular+short">mvp</span> implementation** refers to the
public [ <span class="mark">appsec-mvp</span>
repository](https://github.com/vkraus/appsec-mvp) and its source
archive, `appsec-mvp.zip`. **<span acronym-label="mvp"
acronym-form="singular+short">mvp</span> documentation** or
**documentation site** refers to the published site at
<https://vkraus.github.io/appsec-mvp/> and its static archive,
`appsec-mvp-docs.zip`, which includes a prerendered site under
`docs/site/index.html`. Both archive files are attached during
submission in the Integrated Study Information System and are snapshots
at the commit from which this <span acronym-label="pdf"
acronym-form="singular+short">pdf</span> was built.

The full requirements specification is published in the
<span acronym-label="mvp" acronym-form="singular+short">mvp</span>
documentation. It is structured into four sections (Requirements,
Functional Specification, Design, Tests), generated with MkDocs Material
from <span class="mark">mkdocs/docs/</span> in the
<span acronym-label="mvp" acronym-form="singular+short">mvp</span>
implementation repository, and deployed via GitHub Pages. The same
documentation snapshot is attached to this thesis as
`appsec-mvp-docs.zip`.
<a href="#sec:req-summary" data-reference-type="autoref"
data-reference="sec:req-summary">[sec:req-summary]</a> gives the compact
in thesis summary needed to evaluate the requirements specification
contribution without browsing the site. Where the main chapters name a
page, they link to it directly. The relevant top level sections are the
[capability
matrix](https://vkraus.github.io/appsec-mvp/platform/reference/source-capability-matrix/),
[mapping
requirements](https://vkraus.github.io/appsec-mvp/platform/reference/canonical-mapping/),
[connector hub](https://vkraus.github.io/appsec-mvp/connectors/), and
[catalog](https://vkraus.github.io/appsec-mvp/platform/reference/catalog/).

## Analysis

The analysis starts from the data that an application security platform
has to integrate: inventories, development systems, security tools,
vulnerability intelligence, and runtime telemetry. For each area, the
chapter identifies the relevant interfaces, data models, and integration
patterns. Technology choices are made later in
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> and
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>.

### Asset Discovery and Inventory

Asset discovery and inventory provide the first required context for an
application security data platform. Organizations maintain application
inventories in a <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> or custom catalog, while cloud
providers and container orchestrators expose asset inventories through
<span acronym-label="api" acronym-form="plural+short">apis</span>.
Without this context, a vulnerability cannot be attributed to an owner,
scored for business impact, or prioritized.

#### Application Portfolio Management

Enterprise organizations maintain catalogs of business applications with
metadata such as name, description, ownership, lifecycle status, and
relationships to other assets . These registries also carry criticality
tiers (Tier 1 mission critical, Tier 2 important, Tier 3 noncritical)
derived from business impact assessments along the
<span acronym-label="cia" acronym-form="singular+short">cia</span>
triad  and regulatory scope flags.

The attribute that matters most for data integration is the mapping from
business applications to their technical assets: a single application
may span repositories, microservices, infrastructure, and deployment
environments. When the framework ingests a vulnerability from a
<span acronym-label="sast" acronym-form="singular+short">sast</span>
scanner linked to a repository, this mapping determines which
application is affected, who owns it, and how critical it is.

#### Configuration Management Databases

ServiceNow is widely deployed as a <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> platform in enterprise
environments and leads the global <span acronym-label="itsm"
acronym-form="singular+short">itsm</span> market with over 44% share ,
the closest available proxy for <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> adoption. It serves as the
reference platform for this thesis. A <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> organizes all managed assets
as <span acronym-label="ci" acronym-form="plural+short">cis</span>, each
with attributes describing its type, status, and ownership .

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

ServiceNow exposes two <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> for <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> extraction. The Table
<span acronym-label="api" acronym-form="singular+short">api</span> (
<span class="mark">/api/now/table/{tableName}</span> ) provides generic
queries against any table with server side filtering, field selection,
and pagination . The <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> Instance
<span acronym-label="api" acronym-form="singular+short">api</span> (
<span class="mark">/now/cmdb/instance/{className}</span> ) understands
the <span acronym-label="ci" acronym-form="singular+short">ci</span>
class hierarchy and retrieves a <span acronym-label="ci"
acronym-form="singular+short">ci</span> with its relationships in a
single call . Authentication is Basic auth with a service account or
OAuth 2.0 , and the <span class="mark">sys_updated_on</span> timestamp
serves as a reliable high water mark for incremental extraction.

##### ServiceNow Application

An alternative is to push from the source. A scoped ServiceNow
application can use Outbound REST Messages on a schedule, or expose a
Scripted <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span>  that prejoins application
records with relationships in one response. The advantage is full access
to ServiceNow scripting and relationship traversal. The disadvantage is
that development and maintenance live inside ServiceNow, with schema
changes coordinated across two platforms. This approach suits
organizations with mature ServiceNow development teams.

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

Repositories, build pipelines, and issue trackers form the second major
data source category . These platforms share a common integration
pattern: <span acronym-label="rest"
acronym-form="singular+short">rest</span> over
<span acronym-label="json" acronym-form="singular+short">json</span>,
authentication via OAuth tokens, <span acronym-label="pat"
acronym-form="plural+short">pats</span>, or service accounts, page or
cursor pagination, and rate limits that require backoff. This
consistency enables shared connector logic.

#### Source Code Management

For this thesis, the repository is the primary entity around which
findings are grouped .

Development teams host Git repositories on cloud
<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms. GitHub is dominant (81% adoption for code collaboration),
followed by GitLab (36%), Bitbucket, and Azure DevOps . Most large
organizations run several platforms, so multi platform ingestion is a
practical requirement.

Beyond source code, <span acronym-label="scm"
acronym-form="singular+short">scm</span> platforms expose security
relevant metadata: primary language, last activity, visibility, archive
status. Branch protection rules indicate development process maturity.
Team and contributor assignments establish ownership feeding into the
mapping from application to team in
<a href="#sec:app-inventory" data-reference-type="autoref"
data-reference="sec:app-inventory">[sec:app-inventory]</a>.

These platforms share three API patterns: token based authentication
(OAuth or <span acronym-label="pat"
acronym-form="plural+short">pats</span>), page or cursor pagination, and
rate limits that require backoff. GitHub also exposes a GraphQL endpoint
alongside its <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> (v3), with a 5 000 requests per
hour limit . GitLab, Bitbucket, and Azure DevOps Repos provide
comparable interfaces.

#### Continuous Integration and Delivery

Application security is fundamentally about securing the
<span acronym-label="sdlc" acronym-form="singular+short">sdlc</span>:
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
pipelines are the spine of the modern <span acronym-label="sdlc"
acronym-form="singular+short">sdlc</span> and each stage can integrate
security tools . The dominant platforms are GitHub Actions, Jenkins,
GitLab CI, and Azure Pipelines . Many organizations run more than one,
so the multi platform pattern from <span acronym-label="scm"
acronym-form="singular+short">scm</span> repeats here.

<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
platforms provide contextual data about security scans. Pipeline
definitions reveal which tools run. Build results show whether gates
passed. Execution metadata records commit, timing, and duration. A
repository whose last scan ran three months ago, or whose scans
consistently fail, signals coverage gaps and tool health. This is
operational context rather than a primary finding source.

Integration patterns vary across <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> platforms more than across
<span acronym-label="scm" acronym-form="singular+short">scm</span>:
GitHub Actions and Azure Pipelines expose <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span>, Jenkins uses an
<span acronym-label="xml" acronym-form="singular+short">xml</span> based
<span acronym-label="api" acronym-form="singular+short">api</span>, and
GitLab CI piggybacks on the GitLab <span acronym-label="api"
acronym-form="singular+short">api</span>. Retrieved data is structurally
similar across them: pipeline identifiers, run statuses, timestamps, and
commit references. None of these is built as a connector in the
reference implementation.

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
implementation.

Integration is bidirectional: the framework reads remediation status and
may create new issues when findings require attention. This raises
idempotency concerns (avoiding duplicate issue creation) and state
synchronization (keeping the view of the framework consistent with the
tracker).

### Static Application Security

Application security covers practices and tools for identifying
vulnerabilities throughout the software lifecycle . advocated for
security touchpoints spanning development. The DevSecOps approach 
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
matching for injection flaws, buffer overflows, and insecure data
handling. Broader rule sets catch more issues and generate more noise.
That is the central <span acronym-label="sast"
acronym-form="singular+short">sast</span> tradeoff.

Server tools (SonarQube, Checkmarx, Fortify) expose a
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="api" acronym-form="singular+short">api</span>.
<span acronym-label="cli" acronym-form="singular+short">cli</span> tools
(Semgrep) produce <span acronym-label="json"
acronym-form="singular+short">json</span> or <span acronym-label="sarif"
acronym-form="singular+short">sarif</span> files. Platform integrated
scanners (GitHub Code Scanning, GitLab <span acronym-label="sast"
acronym-form="singular+short">sast</span>) report through the host
<span acronym-label="scm" acronym-form="singular+short">scm</span>
<span acronym-label="api" acronym-form="singular+short">api</span>. When
a platform scanner and a standalone tool both scan a repository, the
overlap requires deduplication.

Findings include a rule identifier, file path and line number, severity,
code snippet, and remediation guidance. Severity models differ:
SonarQube uses five levels (blocker, critical, major, minor, info),
Semgrep and Checkmarx use three (high, medium, low). Severity
normalization is therefore a core transformation.

#### Software Composition Analysis

<span acronym-label="sca" acronym-form="singular+short">sca</span>
identifies known vulnerabilities in third party dependencies. Modern
applications pull in hundreds of transitive dependencies , any of which
can introduce a vulnerability. cover supply chain attacks including
typosquatting, dependency confusion, and malicious package injection.
<span acronym-label="sca" acronym-form="singular+short">sca</span> tools
analyze dependency manifests, resolve the full tree, and cross reference
versions against vulnerability databases such as the
<span acronym-label="nvd" acronym-form="singular+short">nvd</span>.

Tools fall into three groups by integration: server platforms
(<span acronym-label="owasp" acronym-form="singular+short">owasp</span>
Dependency-Track, Snyk) with a <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span>, platform integrated scanners
(Dependabot through GitHub GraphQL, GitLab dependency scanning) reached
through the host <span acronym-label="api"
acronym-form="singular+short">api</span>, and <span acronym-label="cli"
acronym-form="singular+short">cli</span> alternatives such as
<span acronym-label="owasp" acronym-form="singular+short">owasp</span>
Dependency-Check that write <span acronym-label="json"
acronym-form="singular+short">json</span> or <span acronym-label="xml"
acronym-form="singular+short">xml</span> reports from
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
runs. Many tools also generate <span acronym-label="sbom"
acronym-form="plural+short">sboms</span> in CycloneDX or
<span acronym-label="spdx" acronym-form="singular+short">spdx</span>
format , increasingly required by regulators .

<span acronym-label="sca" acronym-form="singular+short">sca</span>
output is more standardized than other categories because the underlying
data comes from shared public databases (<span acronym-label="cve"
acronym-form="singular+short">cve</span>, <span acronym-label="nvd"
acronym-form="singular+short">nvd</span>). Findings include the
vulnerable dependency name and version, a <span acronym-label="cve"
acronym-form="singular+short">cve</span> identifier, a
<span acronym-label="cvss" acronym-form="singular+short">cvss</span>
score, the fixed version when available, and exploitability metadata.
Tools may resolve the same dependency tree differently, so two scanners
flag inconsistent <span acronym-label="cve"
acronym-form="plural+short">cves</span>. The framework handles this
during deduplication: the same <span acronym-label="cve"
acronym-form="singular+short">cve</span> reported by multiple tools
against the same repository likely represents a single issue. The
<span acronym-label="slsa" acronym-form="singular+short">slsa</span>
framework  complements <span acronym-label="sca"
acronym-form="singular+short">sca</span> by verifying the integrity and
provenance of build artifacts.

#### Secret Detection

Secret detection tools scan version control history for credentials,
<span acronym-label="api" acronym-form="singular+short">api</span> keys,
tokens, and other sensitive material. Once committed, a secret persists
in Git history even after deletion from the working tree. Two techniques
apply: regex patterns against known credential formats, and entropy
scoring against unusually random strings. The entropy approach catches
novel formats at higher false positive rates.

<span acronym-label="cli" acronym-form="singular+short">cli</span> tools
(TruffleHog, GitLeaks, detect-secrets) write <span acronym-label="json"
acronym-form="singular+short">json</span> reports parsed as artifacts.
Commercial servers (GitGuardian) expose a <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span>. Platform integrated scanners
(GitHub Secret Scanning, GitLab Secret Detection) report through the
host <span acronym-label="api" acronym-form="singular+short">api</span> 
but only cover repositories on their own platform. There is no standard
output format. Each tool defines its own <span acronym-label="json"
acronym-form="singular+short">json</span> schema, none supports
<span acronym-label="sarif" acronym-form="singular+short">sarif</span>.
Findings include secret type, file path, commit reference, and sometimes
validity status, but field names and structures vary.

### Dynamic Application Security Testing

<span acronym-label="dast" acronym-form="singular+short">dast</span>
tests running applications by sending crafted <span acronym-label="http"
acronym-form="singular+short">http</span> requests and analyzing
responses for vulnerability indicators . It requires a deployed
application and detects vulnerabilities that appear only at runtime,
such as authentication bypass, server misconfiguration, and injection
flaws. This section covers active scanning.
<a href="#sec:runtime-security" data-reference-type="autoref"
data-reference="sec:runtime-security">[sec:runtime-security]</a> covers
passive telemetry.

The representative tools are <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> <span acronym-label="zap"
acronym-form="singular+short">zap</span> (open source) and Burp Suite
Enterprise, both exposing a <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> for scan management and alert
retrieval. Findings include the target <span acronym-label="url"
acronym-form="singular+short">url</span>, affected
<span acronym-label="http" acronym-form="singular+short">http</span>
parameter, vulnerability type mapped to <span acronym-label="cwe"
acronym-form="singular+short">cwe</span> , exploitation evidence, and
confidence rating. The core integration challenge is that
<span acronym-label="dast" acronym-form="singular+short">dast</span>
findings are <span acronym-label="url"
acronym-form="singular+short">url</span> based, not code based. Mapping
them to source repositories requires deployment metadata or inventory
data from <a href="#sec:app-inventory" data-reference-type="autoref"
data-reference="sec:app-inventory">[sec:app-inventory]</a>. Without that
link, <span acronym-label="dast"
acronym-form="singular+short">dast</span> findings can be attributed to
applications but not to teams or code locations.

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
and linking to applications through deployment metadata instead of
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
acronym-form="singular+short">aws</span> <span acronym-label="waf"
acronym-form="singular+short">waf</span> delivers full request logs to
Amazon S3 through Kinesis Data Firehose, which the framework consumes as
the primary path. The <span class="mark">GetSampledRequests</span>
<span acronym-label="api" acronym-form="singular+short">api</span>
returns only a sampled subset and serves as a fallback ([source
reference](https://vkraus.github.io/appsec-mvp/connectors/waf/aws-waf/)).
Cloudflare and Akamai expose comparable <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> for log retrieval and
configuration.

These platforms bundle <span acronym-label="ddos"
acronym-form="singular+short">ddos</span> protection alongside
<span acronym-label="waf" acronym-form="singular+short">waf</span>
capabilities. <span acronym-label="ddos"
acronym-form="singular+short">ddos</span> mitigation logs traffic
patterns, attack signatures, and mitigation actions, providing
availability impact data that complements vulnerability findings.

<span acronym-label="waf" acronym-form="plural+short">wafs</span> emit
append only event streams. The framework projects each event as one
finding row on <span class="mark">silver.findings</span> , with severity
derived from the <span acronym-label="waf"
acronym-form="singular+short">waf</span> action and status fixed to
<span class="mark">open</span> .

### Source Integration Summary

The [source
characteristics](https://vkraus.github.io/appsec-mvp/platform/reference/source-characteristics/)
page tabulates integration characteristics across the AppSec sources
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

Consolidating the sources above into one analytical platform is a data
integration problem. The relevant engineering patterns are lakehouse
storage, layered transformation, incremental ingestion, and dual
analytical and operational serving.

#### Data Platform Architecture

Data warehouses  assume structured, stable sources, and security tool
output is neither. Data lakes  accept any format through schema on read
but risk “data swamps” without governance . The lakehouse  combines lake
flexibility with warehouse governance through open table formats that
add <span acronym-label="acid" acronym-form="singular+short">acid</span>
transactions, schema enforcement, and time travel on top of lake
storage . It accepts semi structured tool output and gives the
governance and fast queries needed for dashboards and operational
lookups.

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

Managed ingestion connectors complement manually coded integration.
Databricks documents Lakeflow Connect as a managed ingestion service for
SaaS applications and databases, governed by Unity Catalog and powered
by serverless compute and Lakeflow Spark Declarative Pipelines . Managed
connectors are in different release states, so the framework uses them
where a supported connector meets the connector contract. The Databricks
Labs project Lakeflow Community Connectors  extends Lakeflow Connect
with community maintained connectors built on the Spark Python Data
Source <span acronym-label="api"
acronym-form="singular+short">api</span>. Community connectors were in
Beta at thesis submission, are not maintained by Databricks, and do not
guarantee forward compatibility . Otherwise the framework falls back to
a maintained Python <span acronym-label="sdk"
acronym-form="singular+short">sdk</span>, then to
<span acronym-label="dltool"
acronym-form="singular+short">dltool</span>, then to artifact path
consumption.

#### Domain Data Model

The security domains analyzed above produce data about a common set of
entities. A vendor agnostic conceptual model precedes physical schemas.
<a href="#tab:domain-entities" data-reference-type="autoref"
data-reference="tab:domain-entities">[tab:domain-entities]</a>
summarizes the entities and their role in the model.

<div class="center">

<span id="tab:domain-entities" label="tab:domain-entities"></span>

| **Entity**      | **Role in the model**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Applications    | Business unit from asset inventories (<a href="#sec:app-inventory" data-reference-type="autoref"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               
                   data-reference="sec:app-inventory">[sec:app-inventory]</a>): name, owning team, criticality tier, lifecycle status, compliance scope. Spans repositories and deployment environments.                                                                                                                                                                                                                                                                                                                                                                                                           |
| Repositories    | Technical asset from <span acronym-label="scm" acronym-form="singular+short">scm</span> (<a href="#sec:sw-dev-analysis" data-reference-type="autoref"                                                                                                                                                                                                                                                                                                                                                                                                                                          
                   data-reference="sec:sw-dev-analysis">[sec:sw-dev-analysis]</a>): primary unit around which findings are grouped.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Findings        | Security issue from any tool category: severity, status, source tool, code location, rule identifier. Each traces to a specific scan.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Vulnerabilities | <span acronym-label="cve" acronym-form="singular+short">cve</span> identified issue enriched with three signals: <span acronym-label="cvss" acronym-form="singular+short">cvss</span> from <span acronym-label="nvd" acronym-form="singular+short">nvd</span>, exploitation probability from <span acronym-label="epss" acronym-form="singular+short">epss</span>, and <span acronym-label="cisa" acronym-form="singular+short">cisa</span> <span acronym-label="kev" acronym-form="singular+short">kev</span> confirmed exploitation. Multiple findings may reference the same vulnerability. |
| Teams           | Organizational ownership linking personnel to applications and remediation responsibility.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Commits         | Individual code changes with author, timestamp, files. Link findings to a code version.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Pull requests   | Code change proposals where scans typically execute. Natural grouping unit for new findings.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Pipeline runs   | <span acronym-label="cicd" acronym-form="singular+short">cicd</span> execution records: which tools ran, when, against which commit, gate outcomes.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Issues          | Remediation work items in trackers such as Jira. Enable <span acronym-label="mttr" acronym-form="singular+short">mttr</span> and <span acronym-label="sla" acronym-form="singular+short">sla</span> monitoring.                                                                                                                                                                                                                                                                                                                                                                                |
| Dependencies    | Third party libraries from <span acronym-label="sca" acronym-form="singular+short">sca</span>: package, version, license, <span acronym-label="cve" acronym-form="plural+short">cves</span>.                                                                                                                                                                                                                                                                                                                                                                                                   |
| Branch policies | <span acronym-label="scm" acronym-form="singular+short">scm</span> governance: required reviewers, status checks, merge restrictions. Indicate process maturity.                                                                                                                                                                                                                                                                                                                                                                                                                               |

</div>

The first five rows are primary entities. The rest add development and
supply chain context.
<a href="#fig:domain-model" data-reference-type="autoref"
data-reference="fig:domain-model">[fig:domain-model]</a> illustrates the
relationships, with primary entities shown in bold.

<div class="center">

<span id="fig:domain-model" label="fig:domain-model"></span>

</div>

The mapping from app to repo is the key relationship. It links findings
to business context and is many to many: shared libraries serve multiple
applications, and microservice applications span multiple repositories.
Teams own applications, applications connect to repositories many to
many, and findings are produced from pipeline runs against those
repositories. Dependencies attach to repositories and reach
vulnerabilities through <span acronym-label="sca"
acronym-form="singular+short">sca</span> findings: a finding cites a
specific library version and references a known
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

No single surveyed approach consolidates application security tool
output into the data platform model required here. Organizations face a
fragmented set of partial solutions.

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
designed as a vulnerability management interface, not a data platform.
Its PostgreSQL backend limits enterprise scale analytics, and advanced
<span acronym-label="api" acronym-form="singular+short">api</span>
connectors are commercial only. <span acronym-label="ocsf"
acronym-form="singular+short">ocsf</span>  standardizes security event
schemas for <span acronym-label="siem"
acronym-form="singular+short">siem</span> and <span acronym-label="soar"
acronym-form="singular+short">soar</span> but does not model application
level entities such as repositories, applications, or teams.

The direct alternatives therefore leave different gaps relative to the
framework of this thesis. Commercial <span acronym-label="aspm"
acronym-form="singular+short">aspm</span> platforms address application
risk aggregation but keep the data model, connector behavior, and
analytics pipeline inside a vendor product . Platform native features
provide strong findings inside one <span acronym-label="scm"
acronym-form="singular+short">scm</span> or DevSecOps ecosystem but do
not consolidate mixed toolchains . DefectDojo provides broad parser
coverage and vulnerability management workflows, but not a governed
lakehouse pipeline from raw source records to analytical and serving
tables . <span acronym-label="sarif"
acronym-form="singular+short">sarif</span>, CycloneDX,
<span acronym-label="spdx" acronym-form="singular+short">spdx</span>,
and <span acronym-label="ocsf" acronym-form="singular+short">ocsf</span>
are valuable interchange standards, but each covers only part of the
model needed here: static analysis results, software bills of materials,
package metadata, or security events . Lakewatch is closest at the data
platform level, but its domain is runtime security operations rather
than application security posture .

Many enterprises build ad hoc integrations: custom scripts,
<span acronym-label="etl" acronym-form="singular+short">etl</span>
pipelines, and dashboards from manual exports. These lack schema
governance, break on <span acronym-label="api"
acronym-form="singular+short">api</span> changes, and persist as
institutional knowledge in unmaintained scripts.

#### Databricks Lakewatch

Databricks announced Lakewatch in March 2026 as an open, agentic
<span acronym-label="siem" acronym-form="singular+short">siem</span>
built on the Databricks lakehouse and made it available in Private
Preview . It unifies security, <span acronym-label="it"
acronym-form="singular+short">it</span>, and business data in a single
governed environment powered by Delta Lake and Unity Catalog, with
agentic triage, Detection as Code, and a partner ecosystem including
Wiz, Palo Alto Networks, Okta, and Zscaler.

Lakewatch focuses on runtime security operations: threat detection,
incident response, alert triage, and log analytics. This framework
focuses on application security posture: findings from
<span acronym-label="sast" acronym-form="singular+short">sast</span>,
<span acronym-label="sca" acronym-form="singular+short">sca</span>,
<span acronym-label="dast" acronym-form="singular+short">dast</span>,
secret scanning, and <span acronym-label="waf"
acronym-form="singular+short">waf</span> runtime telemetry, joined to
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span> and
<span acronym-label="scm" acronym-form="singular+short">scm</span>
context for remediation tracking and risk aggregation. The author did
not have access to the Private Preview during thesis preparation, so
this comparison is based on Databricks public material rather than hands
on evaluation. The two are complementary. Shared lakehouse
infrastructure could enable data exchange: Lakewatch could consume
application risk scores for incident triage, and the framework could
ingest Lakewatch runtime detections as a finding source.

#### Comparative Analysis and Research Gap

<a href="#tab:related-work-comparison" data-reference-type="autoref"
data-reference="tab:related-work-comparison">[tab:related-work-comparison]</a>
compares the surveyed approaches against criteria from the preceding
analysis.

<div class="center">

<span id="tab:related-work-comparison"
label="tab:related-work-comparison"></span>

|                          |                |               |         |         |         |         |
|:-------------------------|:--------------:|:-------------:|:-------:|:-------:|:-------:|:-------:|
| **Criterion**            |    **ASPM**    |               |         |         |         |         |
| **native**               | **DefectDojo** | **Lakewatch** |         |         |         |         |
| **framework**            |                |               |         |         |         |         |
| **MVP**                  |                |               |         |         |         |         |
| Open source              |       –        |       –       |   Yes   |    –    |   Yes   |   Yes   |
| Vendor agnostic model    |       –        |       –       | Partial |    –    |   Yes   | Partial |
| Extensible connectors    |       –        |       –       |   Yes   | Partial |   Yes   |   Yes   |
| Lakehouse architecture   |       –        |       –       |    –    |   Yes   |   Yes   |   Yes   |
| OLAP + OLTP serving      |       –        |       –       |    –    |    –    |   Yes   | Partial |
| Data quality enforcement |       –        |       –       |    –    |    –    |   Yes   | Partial |
| AppSec specific model    |      Yes       |    Partial    |   Yes   |    –    |   Yes   | Partial |
| Enterprise scalability   |      Yes       |    Partial    |    –    |   Yes   | Partial |    –    |

*Note.* Thesis framework means design specification. Thesis MVP means
Databricks reference implementation evidence. Partial indicates bounded
or acknowledged support. – indicates out of scope or not addressed.
Source: cited product documentation and author synthesis (accessed
2026-03/04).

</div>

The surveyed approaches do not jointly satisfy the criteria in the form
required by this thesis. The contribution is the combination of an
application security domain model, a medallion pipeline, a connector
contract, requirement traceability, and a Databricks reference
implementation. The present work is itself partial on two criteria: the
vendor agnostic claim holds at framework level but the reference
implementation runs on Databricks alone, and lakehouse based enterprise
scalability is supported by design but not empirically validated here
(both noted in the Limitations section of the Conclusion). The academic
sources reviewed in this chapter mainly support the detection and data
engineering parts of the problem rather than a complete cross tool
integration architecture .

### Selected Sources

The reference implementation in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> instantiates
the framework against nine source systems chosen to cover the ingestion
and integration patterns that the framework must support, while keeping
the sample small enough to manage. The selection spans all three
detection tiers: static testing, dynamic testing, and runtime security.

#### Selection Criteria

The nine sources are selected based on five criteria:

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

4.  **Limit heterogeneity to nine to maintain scope control.** The nine
    sources are selected as a design sample. They cover the ingestion
    and integration patterns needed to exercise the framework while
    keeping implementation effort manageable. This improves pattern
    coverage but does not make the sample statistically representative
    of all enterprise application security sources.

5.  **Industry adoption.** Each tool is in widespread enterprise use.

The selection therefore supports analytical generalization from observed
integration patterns, not statistical generalization from a population
of tools. The main bias is toward sources with accessible
<span acronym-label="api" acronym-form="plural+short">apis</span>, free
tiers, and formats that can be exercised in a thesis setting. The
Limitations section of the Conclusion names source categories not
demonstrated, including SOAP, gRPC, syslog, Kafka event streams, binary
telemetry, and push only webhook native sources.

A summary of the variation in incremental strategies among the selected
sources is presented in
<a href="#tab:incremental-strategies" data-reference-type="autoref"
data-reference="tab:incremental-strategies">[tab:incremental-strategies]</a>.

<div class="center">

<span id="tab:incremental-strategies"
label="tab:incremental-strategies"></span>

| **Source**                  | **Incremental strategy**                                                        |
|:----------------------------|:--------------------------------------------------------------------------------|
| ServiceNow                  | Native                                                                          |
| SonarQube, Dependency-Track | Native high water mark column (SonarQube                                        |
| GitHub, GitLab              | Webhook                                                                         |
| Semgrep, TruffleHog         | Commit <span acronym-label="sha" acronym-form="singular+short">sha</span>       |
| OWASP ZAP                   | Scan lifecycle retrieval                                                        |
| AWS WAF                     | Firehose to S3 log stream (preferred), time window sampled retrieval (fallback) |

*Note.* Classification synthesized from the medallion pattern treatment
in and the Lakeflow Declarative Pipelines operations guidance in .
Pairings of source and strategy are author attributions based on the API
capability matrix per source.

</div>

#### Source Inventory

The selection resolves to nine sources spanning the three detection
tiers, plus a <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> for inventory and an
<span acronym-label="scm" acronym-form="singular+short">scm</span> pair
for the framework first dependency.

- **ServiceNow** (<span acronym-label="cmdb"
  acronym-form="singular+short">cmdb</span>). Dominant enterprise
  <span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
  with <span acronym-label="rest"
  acronym-form="singular+short">rest</span> Table and CMDB Instance
  <span acronym-label="api" acronym-form="plural+short">apis</span> and
  a native <span class="mark">sys_updated_on</span> high water mark.

- **GitHub** (<span acronym-label="scm"
  acronym-form="singular+short">scm</span> plus integrated
  <span acronym-label="sast" acronym-form="singular+short">sast</span>,
  <span acronym-label="sca" acronym-form="singular+short">sca</span>,
  secrets). <span acronym-label="rest"
  acronym-form="singular+short">rest</span> and GraphQL
  <span acronym-label="api" acronym-form="plural+short">apis</span> with
  cursor pagination and rich webhooks.

- **GitLab** (<span acronym-label="scm"
  acronym-form="singular+short">scm</span> plus integrated security).
  <span acronym-label="rest" acronym-form="singular+short">rest</span>
  and GraphQL with keyset and offset pagination. Security findings
  require Ultimate tier or pipeline artifacts.

- **SonarQube** (<span acronym-label="sast"
  acronym-form="singular+short">sast</span>). Mature server product with
  a <span acronym-label="rest" acronym-form="singular+short">rest</span>
  Web <span acronym-label="api"
  acronym-form="singular+short">api</span>,
  <span class="mark">updateDate</span> high water mark, and a scan
  completion webhook.

- **Semgrep** (<span acronym-label="sast"
  acronym-form="singular+short">sast</span>). Free
  <span acronym-label="cli" acronym-form="singular+short">cli</span>
  engine deployed in a <span acronym-label="cicd"
  acronym-form="singular+short">cicd</span> step. Exercises the artifact
  ingestion pattern.

- **Dependency-Track** (<span acronym-label="sca"
  acronym-form="singular+short">sca</span>). <span acronym-label="owasp"
  acronym-form="singular+short">owasp</span> project with a
  <span acronym-label="rest" acronym-form="singular+short">rest</span>
  <span acronym-label="api" acronym-form="singular+short">api</span> and
  <span acronym-label="sbom" acronym-form="singular+short">sbom</span>
  centric vulnerability correlation across multiple advisory sources.

- **TruffleHog** (secrets). <span acronym-label="cli"
  acronym-form="singular+short">cli</span> tool with live credential
  verification that populates the
  <span class="mark">validity_status</span> field.

- **OWASP ZAP** (<span acronym-label="dast"
  acronym-form="singular+short">dast</span>). Open source dynamic
  scanner operated as a daemon with a <span acronym-label="rest"
  acronym-form="singular+short">rest</span> <span acronym-label="api"
  acronym-form="singular+short">api</span> , exercising the on demand
  scan lifecycle pattern.

- **AWS WAF** (<span acronym-label="waf"
  acronym-form="singular+short">waf</span>, runtime). Kinesis Data
  Firehose to S3 log stream as the primary path , with the
  <span class="mark">GetSampledRequests</span> <span acronym-label="api"
  acronym-form="singular+short">api</span> as the time window sampled
  fallback.

Details for each source are on the [connector
hub](https://vkraus.github.io/appsec-mvp/connectors/).

#### Considered and Excluded

<a href="#tab:considered-excluded" data-reference-type="autoref"
data-reference="tab:considered-excluded">[tab:considered-excluded]</a>
enumerates the key tools that were considered and the criterion that
excluded each. Tools marked **within scope, deferred** satisfy all
criteria but are excluded based on the cap in Criterion 4. Onboarding
them would simply be a repeat of the procedure per source in
<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a>.

<div class="center">

\[Considered and excluded sources\]Considered and excluded sources. Each
row names the tool, the category it would have populated, and the
criterion that excluded it (C1 open source or free tier, C2 full domain
coverage, C3 <span acronym-label="api"
acronym-form="singular+short">api</span> heterogeneity, C4 heterogeneity
cap, C5 industry adoption). <span id="tab:considered-excluded"
label="tab:considered-excluded"></span>

| **Tool**        | **Category**                                                                                                                              | **Excl. by** | **Note**                                                                                                                    |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------|:-------------|:----------------------------------------------------------------------------------------------------------------------------|
| Checkmarx       | <span acronym-label="sast" acronym-form="singular+short">sast</span>                                                                      | C1           | commercial only, no permissive tier                                                                                         |
| Fortify         | <span acronym-label="sast" acronym-form="singular+short">sast</span>                                                                      | C1           | commercial, OpenText                                                                                                        |
| Burp Enterprise | <span acronym-label="dast" acronym-form="singular+short">dast</span>                                                                      | C1           | commercial. Community edition is manual only                                                                                |
| Snyk            | <span acronym-label="sca" acronym-form="singular+short">sca</span> / <span acronym-label="sast" acronym-form="singular+short">sast</span> | C4           | **within scope, deferred** (overlap with Dependency-Track and Semgrep)                                                      |
| GitGuardian     | secrets                                                                                                                                   | C4           | **within scope, deferred** (overlap with TruffleHog)                                                                        |
| GitLeaks        | secrets                                                                                                                                   | C4           | **within scope, deferred** (overlap with TruffleHog)                                                                        |
| Dependabot      | <span acronym-label="sca" acronym-form="singular+short">sca</span>                                                                        | C4           | **within scope, deferred**. GitHub native, overlap with Dependency-Track                                                    |
| Jira            | issue tracker                                                                                                                             | C4           | **within scope, deferred**. Issue tracking is in the data model (<a href="#sec:data-entities" data-reference-type="autoref" 
                                                                                                                                                                              data-reference="sec:data-entities">[sec:data-entities]</a>), MVP defers connector to keep the count at nine                  |
| Azure DevOps    | <span acronym-label="scm" acronym-form="singular+short">scm</span> / <span acronym-label="cicd" acronym-form="singular+short">cicd</span> | C4           | **within scope, deferred** (overlap with GitHub and GitLab)                                                                 |
| Bitbucket Cloud | <span acronym-label="scm" acronym-form="singular+short">scm</span>                                                                        | C4           | **within scope, deferred**                                                                                                  |
| Jenkins         | <span acronym-label="cicd" acronym-form="singular+short">cicd</span>                                                                      | C2           | CI orchestrator, does not produce <span acronym-label="aspm" acronym-form="singular+short">aspm</span> findings on its own  |
| GitHub Actions  | <span acronym-label="cicd" acronym-form="singular+short">cicd</span>                                                                      | C4           | **within scope, deferred**                                                                                                  |
| Cloudflare WAF  | <span acronym-label="waf" acronym-form="singular+short">waf</span>                                                                        | C4           | **within scope, deferred** (overlap with AWS WAF)                                                                           |
| Akamai WAF      | <span acronym-label="waf" acronym-form="singular+short">waf</span>                                                                        | C1           | commercial, no free tier                                                                                                    |

</div>

#### Cross Source Synthesis

Across the nine sources, four record forms recur (ticket like, resource
like, finding like, event like), severity scales span three to six
levels, and status vocabularies diverge more sharply with tool specific
states that rarely map one to one. Five pagination strategies appear:
offset (ServiceNow, SonarQube, Dependency-Track), cursor (GitHub
<span acronym-label="rest" acronym-form="singular+short">rest</span>),
GraphQL cursor (GitHub and GitLab GraphQL), keyset (GitLab
<span acronym-label="rest" acronym-form="singular+short">rest</span>),
and none (<span acronym-label="cli"
acronym-form="singular+short">cli</span> sources, AWS WAF). The sources
also split on an operational pattern axis: periodic global scanners
polled via <span class="mark">updated_at</span> (SonarQube,
Dependency-Track), <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> step scanners indexed by
commit <span acronym-label="sha"
acronym-form="singular+short">sha</span> (Semgrep, TruffleHog), on
demand dynamic scanners read via scan lifecycle
<span acronym-label="api" acronym-form="singular+short">api</span>
(OWASP ZAP), and runtime telemetry sampled over time windows (AWS WAF).
Together they exercise all five ingestion strategies the framework
prescribes. The [capability
matrix](https://vkraus.github.io/appsec-mvp/platform/reference/source-capability-matrix/)
tabulates them against the capabilities that matter for connector
design.

### Requirements Summary

The analysis above produces the core requirements used by
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>. The complete
requirements specification is published in the
[<span acronym-label="mvp" acronym-form="singular+short">mvp</span>
documentation](https://vkraus.github.io/appsec-mvp/) and attached to
this thesis as `appsec-mvp-docs.zip`. It contains the source
<span acronym-label="api" acronym-form="singular+short">api</span>
analysis, mapping derivations, runbooks, validation logs, and the full
traceability matrix. The summary below gives the parts needed to
evaluate the requirements contribution without reading the external
specification. <a href="#tab:req-summary" data-reference-type="autoref"
data-reference="tab:req-summary">[tab:req-summary]</a> names the
requirement families, the evidence in the thesis, and the implementation
trace used to evaluate each family.
<a href="#tab:connector-req-snapshot" data-reference-type="autoref"
data-reference="tab:connector-req-snapshot">[tab:connector-req-snapshot]</a>
lists the stable connector requirement identifiers used by tests and by
the published traceability matrix.

The requirement identifiers are intentionally stable across sources. A
source can mark a requirement as not applicable (for example, tools that
only emit artifacts have no <span acronym-label="api"
acronym-form="singular+short">api</span> pagination or rate limit
handling), but applicable requirements must be bound to tests. This is
the bridge between the requirements specification contribution and the
implementation evidence: the framework defines the identifiers and
expected behavior, while
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> reports how
the <span acronym-label="mvp" acronym-form="singular+short">mvp</span>
satisfies or bounds them for each selected source.

The gap identified above is addressed by a vendor agnostic framework. It
applies lakehouse architecture and the medallion pattern to ingest tool
output, normalize it into a domain model, and serve it through
<span acronym-label="olap" acronym-form="singular+short">olap</span> and
<span acronym-label="oltp" acronym-form="singular+short">oltp</span>
interfaces. <a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> gives the design, and
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> reports the
<span acronym-label="mvp" acronym-form="singular+short">mvp</span>.

<div class="center">

\[Requirements summary\]Requirements summary for the application
security data integration framework. <span id="tab:req-summary"
label="tab:req-summary"></span>

| **Requirement family**      | **Requirement summary**                                                                                                                                                                                                                                                                                                                             | **Thesis evidence**                                                                                                                                                               |
|:----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Source coverage             | Cover business application inventory, source repositories, static testing, software composition analysis, secrets, dynamic testing, and one runtime security source.                                                                                                                                                                                | Source selection criteria and inventory in <a href="#sec:selected-sources" data-reference-type="autoref"                                                                          
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:selected-sources">[sec:selected-sources]</a>. Ingestion assignment in <a href="#sec:ingestion-category-assignment"                                             
                                                                                                                                                                                                                                                                                                                                                                                     data-reference-type="autoref"                                                                                                                                                      
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:ingestion-category-assignment">[sec:ingestion-category-assignment]</a>.                                                                                        |
| Source heterogeneity        | Exercise <span acronym-label="rest" acronym-form="singular+short">rest</span>, GraphQL, managed connector, <span acronym-label="sdk" acronym-form="singular+short">sdk</span>, <span acronym-label="dltool" acronym-form="singular+short">dltool</span>, and artifact ingestion patterns, including multiple pagination and high water mark styles. | Cross source synthesis in <a href="#sec:cross-source-synthesis" data-reference-type="autoref"                                                                                     
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:cross-source-synthesis">[sec:cross-source-synthesis]</a>. Connector categories in <a href="#sec:connector-abstraction" data-reference-type="autoref"           
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:connector-abstraction">[sec:connector-abstraction]</a>.                                                                                                        |
| Standard data model         | Normalize heterogeneous records into bronze, silver, and gold layers, with a single findings fact table and relationship tables for application context and deduplication.                                                                                                                                                                          | Medallion and schema patterns in <a href="#sec:medallion-arch" data-reference-type="autoref"                                                                                      
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:medallion-arch">[sec:medallion-arch]</a> and <a href="#sec:schema-patterns" data-reference-type="autoref"                                                      
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:schema-patterns">[sec:schema-patterns]</a>. Entity model in <a href="#sec:entity-model" data-reference-type="autoref"                                          
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:entity-model">[sec:entity-model]</a>.                                                                                                                          |
| Connector contract          | Standardize authentication, pagination, rate limits, high water marks, schema mapping, severity/status normalization, timestamp normalization, data quality, and deduplication.                                                                                                                                                                     | Connector contract and testing requirements in <a href="#sec:connector-framework" data-reference-type="autoref"                                                                   
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:connector-framework">[sec:connector-framework]</a> and <a href="#sec:connector-testing" data-reference-type="autoref"                                          
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:connector-testing">[sec:connector-testing]</a>. REQ ID summary in <a href="#tab:connector-req-snapshot" data-reference-type="autoref"                          
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="tab:connector-req-snapshot">[tab:connector-req-snapshot]</a>.                                                                                                      |
| Serving and analytics       | Provide Gold datasets ready for consumption and both analytical and operational serving paths.                                                                                                                                                                                                                                                      | Analytics and serving framework in <a href="#sec:analytics-serving" data-reference-type="autoref"                                                                                 
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:analytics-serving">[sec:analytics-serving]</a>. MVP analytics evidence in <a href="#sec:impl-results" data-reference-type="autoref"                            
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:impl-results">[sec:impl-results]</a>.                                                                                                                          |
| Extensibility               | Onboard a new source by resolving category, instantiating the module layout, encoding the mapping, testing, and running the skill chain with review.                                                                                                                                                                                                | Implementation methodology in <a href="#sec:impl-methodology" data-reference-type="autoref"                                                                                       
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:impl-methodology">[sec:impl-methodology]</a>. AI instantiability evaluation in <a href="#sec:ai-eval" data-reference-type="autoref"                            
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="sec:ai-eval">[sec:ai-eval]</a>.                                                                                                                                    |
| Validation and traceability | Bind implementation tests to stable requirement identifiers and publish PASS/N/A evidence per source.                                                                                                                                                                                                                                               | Connector REQ IDs in <a href="#tab:connector-req-snapshot" data-reference-type="autoref"                                                                                          
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="tab:connector-req-snapshot">[tab:connector-req-snapshot]</a>. Implementation evidence matrix in <a href="#tab:impl-evidence-levels" data-reference-type="autoref"  
                                                                                                                                                                                                                                                                                                                                                                                     data-reference="tab:impl-evidence-levels">[tab:impl-evidence-levels]</a>.                                                                                                          |

</div>

<div class="center">

\[Connector requirement identifiers\]Connector requirement identifiers
used for traceability. The full matrix for each source is published in
the <span acronym-label="mvp" acronym-form="singular+short">mvp</span>
documentation. <a href="#sec:impl-results" data-reference-type="autoref"
data-reference="sec:impl-results">[sec:impl-results]</a> reports the
evidence boundary in this thesis. <span id="tab:connector-req-snapshot"
label="tab:connector-req-snapshot"></span>

| **ID** | **Area**  | **Requirement**                                                                               |
|:-------|:----------|:----------------------------------------------------------------------------------------------|
|        | Ingestion | Credentials resolve from the platform secret scope. Invalid credentials fail clearly.         |
|        | Ingestion | Pagination completes without data loss or duplication across at least two pages.              |
|        | Ingestion | Rate limit handling follows the configured retry and backoff policy.                          |
|        | Ingestion | High water mark resume fetches only new or changed records on the next run.                   |
|        | Transform | Source records map to the target Silver schema with correct types, values, and null handling. |
|        | Transform | Native severity values normalize to the standard severity model, including edge cases.        |
|        | Transform | Native lifecycle states normalize to the standard status model.                               |
|        | Transform | Source timestamps normalize to UTC datetimes.                                                 |
|        | Quality   | Silver validation expectations distinguish valid records from quarantine candidates.          |
|        | Quality   | Applicable finding categories produce deterministic deduplication keys and overlap links.     |

</div>

## Framework

<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> produced the source
patterns and requirements. The framework turns them into three design
parts: deployment architecture, medallion data model, and connector and
analytics contracts. The design targets the Databricks Lakehouse while
separating general patterns from platform specific choices.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> then
instantiates it.

### Solution Architecture

The architecture is described through three views: the Databricks stack,
the runtime components, and the bronze, silver, and gold data layers.
These views cover the requirements from domain analysis: heterogeneous
source ingestion, vendor agnostic normalization, dual
<span acronym-label="olap"
acronym-form="singular+short">olap</span>/<span acronym-label="oltp"
acronym-form="singular+short">oltp</span> serving, and extension to new
data sources and analytics.

A further design principle applies to the framework artifacts: every
template defined in this chapter (schema patterns, mappings, connector
contract) is declarative, not procedural, so that an
<span acronym-label="ai" acronym-form="singular+short">ai</span> coding
agent reading the specification has enough material to produce a
candidate connector implementation. The published skill catalog, which
sits in the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> documentation and wraps these
templates into executable prompts, is evaluated separately in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>.

#### Technology Stack

The framework targets the Databricks platform on
<span acronym-label="aws" acronym-form="singular+short">aws</span>.
Databricks separates storage from compute: data resides in object
storage and compute scales independently. This reduces costs for uneven
workloads typical for security data integration .

The four platform components are Delta Lake, Unity Catalog, Lakeflow
Declarative Pipelines, and Lakebase. **Delta Lake**  is the open table
format providing the storage layer for all three medallion tiers, with
<span acronym-label="acid" acronym-form="singular+short">acid</span>
transactions, schema enforcement, schema evolution, and time travel.
**Unity Catalog**  manages a three level namespace (
<span class="mark">catalog.schema.table</span> ) mapped to the medallion
layout (one catalog per environment, schemas per source for bronze, per
domain for silver and gold), with fine grained access control and
automated lineage. **<span acronym-label="ldp"
acronym-form="singular+short">ldp</span>**  declares pipelines as Python
or <span acronym-label="sql" acronym-form="singular+short">sql</span>
functions, embeds data quality expectations as declarative constraints
with quarantine on violation, and processes incrementally through change
data feed. **Lakebase**  is a serverless Postgres operational database
integrated with the Databricks platform and provides the
<span acronym-label="oltp" acronym-form="singular+short">oltp</span>
serving layer required by
<a href="#sec:data-architecture" data-reference-type="autoref"
data-reference="sec:data-architecture">[sec:data-architecture]</a>.

Running all four on one platform yields governance, lineage, and compute
benefits that would require significant integration across separate
tools. The platform also lines up with Lakewatch, the Databricks
<span acronym-label="siem" acronym-form="singular+short">siem</span>
analyzed in <a href="#sec:lakewatch" data-reference-type="autoref"
data-reference="sec:lakewatch">[sec:lakewatch]</a>: both use the
lakehouse and Unity Catalog governance, opening a possible path for the
framework gold outputs (risk scores, remediation status) to enrich
Lakewatch threat detection and for Lakewatch runtime events to feed back
as a finding source.

#### Component Design

Five tiers organize the framework, illustrated in
<a href="#fig:component-design" data-reference-type="autoref"
data-reference="fig:component-design">[fig:component-design]</a>. Data
flows from top to bottom, from sources through the platform to
consumers.

<div class="center">

<span id="fig:component-design" label="fig:component-design"></span>

</div>

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
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>. A
separate artifact ingestion pattern applies to <span acronym-label="cli"
acronym-form="singular+short">cli</span> only tools that emit a report
file during a continuous integration step and is documented in
<a href="#sec:ingestion-patterns" data-reference-type="autoref"
data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>.
All connectors share common concerns: authentication, pagination, rate
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

<div class="center">

<span id="fig:medallion-design" label="fig:medallion-design"></span>

</div>

##### Bronze Layer

Bronze stores raw data from each source with no business logic, in a per
source schema ( <span class="mark">bronze\_\<source\></span> ). Records
are appended with the bronze envelope columns. Schema on read accepts
new source fields without pipeline changes. Tables are partitioned by
ingestion date. Structural validation failures at ingestion go to per
source quarantine tables.

##### Silver Layer

Silver is the system of record. Transformations normalize source data
into the vendor agnostic domain model from
<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a>, applying
severity harmonization, entity normalization, timestamp standardization,
and deduplication. The layer holds entity tables (dimensions), the
single <span class="mark">silver.findings</span> fact table
(<a href="#sec:silver-findings-design" data-reference-type="autoref"
data-reference="sec:silver-findings-design">[sec:silver-findings-design]</a>),
and relationship tables for many to many links.
<span acronym-label="ldp" acronym-form="singular+short">ldp</span>
expectations enforce constraints declaratively, and violators go to
quarantine.

##### Gold Layer

Gold computes consumption ready datasets from silver. Aggregation tables
compute metrics (risk scores, team remediation rates,
<span acronym-label="mttr" acronym-form="singular+short">mttr</span>,
<span acronym-label="sla" acronym-form="singular+short">sla</span>
compliance, time series). <span acronym-label="ml"
acronym-form="singular+short">ml</span> enriched tables store model
outputs (composite risk scores, false positive predictions, remediation
time estimates) per the patterns in
<a href="#sec:analytics-patterns" data-reference-type="autoref"
data-reference="sec:analytics-patterns">[sec:analytics-patterns]</a>.
Gold uses incremental refresh where possible, and full refresh applies
for metrics needing global recomputation.

### Data Model

The conceptual domain model from
<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a> is mapped to
physical tables across the three medallion layers. The schema patterns
produce the entity, finding, relationship, reference, and aggregation
tables used by the framework.

#### Source Synthesis

The schema patterns are derived from the <span acronym-label="api"
acronym-form="plural+short">apis</span> of the nine sources introduced
in <a href="#sec:selected-sources" data-reference-type="autoref"
data-reference="sec:selected-sources">[sec:selected-sources]</a>, not
chosen in advance. The [capability
matrix](https://vkraus.github.io/appsec-mvp/platform/reference/source-capability-matrix/)
and [connector hub](https://vkraus.github.io/appsec-mvp/connectors/)
provide the source facts this section maps onto concrete Entity,
Finding, and Relationship schemas.

#### Schema Patterns

Schema patterns standardize how tables are created at each medallion
layer. <a href="#fig:record-lifecycle" data-reference-type="autoref"
data-reference="fig:record-lifecycle">[fig:record-lifecycle]</a> walks a
single SonarQube <span acronym-label="sast"
acronym-form="singular+short">sast</span> finding through the layers and
shows the metadata envelope from
<a href="#sec:bronze-pattern" data-reference-type="autoref"
data-reference="sec:bronze-pattern">[sec:bronze-pattern]</a>.

<div class="center">

\[Record lifecycle through the medallion layers\]Lifecycle of a single
SonarQube <span acronym-label="sast"
acronym-form="singular+short">sast</span> finding from
<span acronym-label="api" acronym-form="singular+short">api</span>
response through Bronze ingestion with the metadata envelope with five
columns, Silver normalization into
<span class="mark">silver.findings</span> with category discriminator,
and Gold aggregation into <span class="mark">app_risk_scores</span> .
<span id="fig:record-lifecycle" label="fig:record-lifecycle"></span>

</div>

##### Bronze envelope

Every bronze table carries a uniform metadata envelope: four columns
shared across connectors (
<span class="mark">\_ingestion_timestamp</span> ,
<span class="mark">\_source_system</span> ,
<span class="mark">\_batch_id</span> ,
<span class="mark">\_raw_payload</span> ) and a fifth (
<span class="mark">\_hwm_value</span> ) on incremental only tables
(<a href="#sec:ingestion-patterns" data-reference-type="autoref"
data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>).
When the framework owns the bronze schema (artifact sources such as
<span acronym-label="owasp" acronym-form="singular+short">owasp</span>
<span acronym-label="zap" acronym-form="singular+short">zap</span> and
Semgrep), a helper stamps the envelope before the write. When an
ingestion managed service owns the table (Lakeflow Connect, as in
ServiceNow), a downstream <span acronym-label="sql"
acronym-form="singular+short">sql</span> view projects the same five
columns on top of the managed table using the service run identifier and
timestamp. Downstream readers see the same envelope regardless of
ingestion path.

Additional source native columns sit alongside the raw payload via
schema on read. New fields are accepted through additive evolution.
Tables are partitioned by ingestion date.

##### Silver entity pattern

Entity tables store normalized dimension data. The natural key plus
source system identifies a record origin, and the surrogate key provides
a stable foreign key target even when source identifiers change . The
framework specifies the <span acronym-label="scd"
acronym-form="singular+short">scd</span>-2 pattern (
<span class="mark">valid_from</span> ,
<span class="mark">valid_to</span> ) for tracking entity history . The
reference implementation in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> simplifies to
<span acronym-label="scd" acronym-form="singular+short">scd</span>-1
(overwrite on update) since the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> scenarios do not exercise point
in time queries. The [mapping
table](https://vkraus.github.io/appsec-mvp/platform/reference/canonical-mapping/#silver-entity-mapping-requirements)
is published in the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> documentation.

The Bronze to Silver step quarantines a record when (1) the Bronze
record failed <span acronym-label="json"
acronym-form="singular+short">json</span> parse at landing, (2) a
required field is null ( <span class="mark">natural_key</span> ,
<span class="mark">source_system</span> ,
<span class="mark">valid_from</span> ), or (3) a mandatory lookup yields
no match. Optional field nulls and safe casts are accepted with a data
quality warning. The same rule applies to finding tables.

For <span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
entities, related tables ( <span class="mark">cmdb_rel_ci</span> , group
and user references) are ingested as separate Bronze tables and joined
in Silver rather than resolved through relationship
<span acronym-label="api" acronym-form="plural+short">apis</span>. This
keeps <span class="mark">ingest.py</span> stateless and localizes schema
change handling to the transformation layer.

##### Silver finding pattern

The single Silver Finding table
<span class="mark">silver.findings</span> (rationale in
<a href="#sec:silver-findings-design" data-reference-type="autoref"
data-reference="sec:silver-findings-design">[sec:silver-findings-design]</a>)
stores normalized fact data for every category. Each target field unions
over the native fields of the finding emitting sources, with
inapplicable fields stored as <span class="mark">NULL</span> . The
<span class="mark">mapping.yml</span> for each source
(<a href="#sec:transformation-patterns" data-reference-type="autoref"
data-reference="sec:transformation-patterns">[sec:transformation-patterns]</a>)
makes each mapping explicit, including the
<span class="mark">category</span> discriminator. The [mapping
tables](https://vkraus.github.io/appsec-mvp/platform/reference/canonical-mapping/#silver-finding-mapping-requirements)
are published in the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> documentation.

##### Deduplication

When several tools scan the same artifact, overlapping findings are
linked rather than collapsed . Deduplication is applied within
<span class="mark">silver.findings</span> using a category conditional
exact match tuple:

- <span acronym-label="sast" acronym-form="singular+short">sast</span> (
  <span class="mark">category = ’sast’</span> ):
  <span class="mark">(repository_id, file_path, rule_id,
  line_number)</span> .

- <span acronym-label="sca" acronym-form="singular+short">sca</span> (
  <span class="mark">category = ’sca’</span> ):
  <span class="mark">(repository_id, package_name, cve_id)</span> .

- Secret ( <span class="mark">category = ’secret’</span> ):
  <span class="mark">(repository_id, commit_sha, secret_type,
  file_path)</span> . Secrets are retained per commit, not collapsed by
  value.

A match across two tools links the records via a
<span class="mark">dedup_links</span> record. No fuzzy matching is
performed. When tools diverge on line numbers, both findings are
retained and grouped at Gold via a
<span class="mark">finding_group_id</span> on
<span class="mark">(repository_id, file_path, rule_id)</span>
independent of line number.

##### Relationship pattern

Relationship tables hold many to many mappings between entities: foreign
keys to both sides, a source system indicator, relationship state fields
such as <span class="mark">link_source</span> or
<span class="mark">attribution_state</span> , and
<span class="mark">valid_from</span> /
<span class="mark">valid_to</span> . They carry relationship metadata
rather than entity payload columns. Examples are application to
repository, finding to <span acronym-label="cve"
acronym-form="singular+short">cve</span>, and cross tool deduplication
links.

##### Gold aggregation

Aggregation tables follow a grain, metric, period structure : grain
columns define detail level (entity key plus time period), metric
columns store computed values (finding counts,
<span acronym-label="mttr" acronym-form="singular+short">mttr</span>,
<span acronym-label="sla" acronym-form="singular+short">sla</span>
compliance, risk score), period columns store the window (
<span class="mark">period_start</span> ,
<span class="mark">period_end</span> ), and refresh metadata records the
<span class="mark">computed_at</span> timestamp and strategy.

#### Entity Model

The silver layer instantiates the schema patterns as concrete tables in
four groups: entities (dimensions), findings (facts), reference data,
and relationships.
<a href="#fig:silver-erd" data-reference-type="autoref"
data-reference="fig:silver-erd">[fig:silver-erd]</a> shows a
representative subset that exercises every relationship type. The
prescription totals 15 domain tables across the four groups. The
<span acronym-label="mvp" acronym-form="singular+short">mvp</span> in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> realizes four
of those prescribed domain tables (
<span class="mark">applications</span> ,
<span class="mark">repositories</span> ,
<span class="mark">findings</span> , and
<span class="mark">app_repo_mapping</span> ) plus three supporting
Silver tables ( <span class="mark">finding_location</span> ,
<span class="mark">hwm</span> , and
<span class="mark">suppression_rules</span> ). Together they form the
current core Silver subset sufficient to demonstrate the medallion
contract. Population of the remaining prescribed domain tables is
recorded as Future Work in
<a href="#sec:future-work" data-reference-type="autoref"
data-reference="sec:future-work">[sec:future-work]</a>.

<div class="center">

\[Silver layer entity relationship diagram\]Silver layer entity
relationship diagram for the prescribed framework. Representative
subset: **8** of the **15** prescribed domain silver tables grouped by
type (entities, findings, reference, relationships). Highlighted nodes
are the prescribed domain tables included in the
<span acronym-label="mvp" acronym-form="singular+short">mvp</span> core
subset. The <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> also includes supporting Silver
tables not shown in this compact relationship diagram:
<span class="mark">finding_location</span> ,
<span class="mark">hwm</span> , and
<span class="mark">suppression_rules</span> . The remaining prescribed
domain tables follow the same schema patterns and are listed in
<a href="#sec:future-work" data-reference-type="autoref"
data-reference="sec:future-work">[sec:future-work]</a>.
<span id="fig:silver-erd" label="fig:silver-erd"></span>

</div>

##### Entity Tables

Eight entity tables hold the stable business objects:
<span class="mark">applications</span> and
<span class="mark">repositories</span> as the two primary tables, plus
<span class="mark">teams</span> , <span class="mark">commits</span> ,
<span class="mark">pull_requests</span> ,
<span class="mark">pipeline_runs</span> ,
<span class="mark">dependencies</span> , and
<span class="mark">branch_policies</span> . All tables share the silver
entity pattern columns ( <span class="mark">id</span> ,
<span class="mark">natural_key</span> ,
<span class="mark">source_system</span> ,
<span class="mark">valid_from</span> ,
<span class="mark">valid_to</span> ). Domain specific columns and source
mappings are listed on the [ownership
page](https://vkraus.github.io/appsec-mvp/platform/reference/silver-table-ownership/).

##### Finding Table

All security findings land in a single Silver table,
<span class="mark">silver.findings</span> . A
<span class="mark">category</span> column discriminates records as
<span class="mark">sast</span> , <span class="mark">sca</span> ,
<span class="mark">secret</span> , <span class="mark">dast</span> ,
<span class="mark">waf</span> , <span class="mark">container</span> , or
<span class="mark">iac</span> . Category specific attributes (such as
<span class="mark">file_path</span> and <span class="mark">cwe_id</span>
for <span acronym-label="sast"
acronym-form="singular+short">sast</span>, or
<span class="mark">cve_id</span> and
<span class="mark">installed_version</span> for
<span acronym-label="sca" acronym-form="singular+short">sca</span>) are
carried as nullable columns and populated only where the category
defines them. Code located findings reference their repository through
<span class="mark">repository_id</span> . Runtime perimeter findings
(<span acronym-label="waf" acronym-form="singular+short">waf</span>)
leave <span class="mark">repository_id</span> null and use
<span class="mark">url</span> as the closest location coordinate.
Business application context is derived through the
<span class="mark">app_repo_mapping</span> relationship table instead of
being stored on the finding itself.

A single table is preferred over per category tables because the silver
mapping is already a union over sources . Splitting it would force
<span class="mark">UNION ALL</span> for cross category analytics and
fragment the per category dedup routing. At the target scale, Delta Lake
columnar compression makes the sparse NULLs cheap. Full column listing
and rationale are on the [rationale
page](https://vkraus.github.io/appsec-mvp/platform/reference/single-silver-findings-rationale/).

##### Reference and Relationship Tables

Three reference tables hold external intelligence:
<span class="mark">vulnerabilities</span> (<span acronym-label="cve"
acronym-form="singular+short">cve</span> records with
<span acronym-label="cvss" acronym-form="singular+short">cvss</span>
from the <span acronym-label="nvd"
acronym-form="singular+short">nvd</span>),
<span class="mark">epss_scores</span> (daily <span acronym-label="epss"
acronym-form="singular+short">epss</span> probabilities per
<span acronym-label="cve" acronym-form="singular+short">cve</span>), and
<span class="mark">kev_entries</span> (<span acronym-label="cisa"
acronym-form="singular+short">cisa</span> <span acronym-label="kev"
acronym-form="singular+short">kev</span> catalog). They are refreshed on
schedule and linked to findings through <span acronym-label="cve"
acronym-form="singular+short">cve</span> identifiers, supporting the
three signal enrichment described in
<a href="#sec:static-appsec" data-reference-type="autoref"
data-reference="sec:static-appsec">[sec:static-appsec]</a>.

Three relationship tables implement the cross object mappings:
<span class="mark">app_repo_mapping</span> (applications to
repositories, many to many),
<span class="mark">finding_cve_mapping</span> (findings to
<span acronym-label="cve" acronym-form="singular+short">cve</span>
records), and <span class="mark">dedup_links</span> (duplicate findings
across tools, with one reference record). Silver tables and connectors
do not line up one to one. Each table can be fed by multiple connectors
and each connector feeds multiple tables.

#### Aggregation Model

Four gold tables target the stakeholder needs identified in
<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a>, each
following the gold aggregation pattern from
<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>.

- ** <span class="mark">app_risk_scores</span> ** : composite risk per
  application per period. Open finding counts by severity, a weighted
  risk score combining severity, <span acronym-label="epss"
  acronym-form="singular+short">epss</span> probability and application
  criticality tier, <span acronym-label="sla"
  acronym-form="singular+short">sla</span> compliance, and a trend
  indicator. Serves application owners.

- ** <span class="mark">team_metrics</span> ** : remediation performance
  per team per period. <span acronym-label="mttr"
  acronym-form="singular+short">mttr</span> by severity, closure rate,
  new versus resolved ratio, <span acronym-label="sla"
  acronym-form="singular+short">sla</span> breach count. Used by
  leadership for cross team comparisons.

- ** <span class="mark">vulnerability_trends</span> ** : time series at
  configurable intervals (daily, weekly, monthly). New findings,
  resolved findings, net open count, severity distribution shifts, mean
  age of open findings. Powers longitudinal dashboards.

- ** <span class="mark">coverage_analysis</span> ** : gaps in tool
  coverage per repository. A repository with no
  <span acronym-label="sast" acronym-form="singular+short">sast</span>
  findings and no <span acronym-label="sast"
  acronym-form="singular+short">sast</span> pipeline runs likely lacks
  static analysis integration. Helps prioritize tooling rollout.

Adding a new gold table follows the same procedure: define the
granularity, specify the metrics, write the <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> transformation, configure the
refresh strategy. The shared aggregation pattern lets dashboards consume
new tables without structural changes.

### Environment and Deployment

Deployment assumes a working Databricks environment. Account onboarding,
workspace creation, networking, and <span acronym-label="iam"
acronym-form="singular+short">iam</span> federation are outside scope.
Deployment splits into two tiers along resource ownership: every
Databricks object that the bundle format has a native type for is
declared in a Declarative Automation Bundle, formerly Databricks Asset
Bundle , and source side cloud infrastructure for each connector is
declared in Terraform under the connector folder. The deployment model
follows the declarative infrastructure as code patterns established in
the DevOps literature .

#### Deployment Strategy

The **Databricks tier** owns every workspace resource the bundle format
covers natively: catalogs, schemas, volumes, jobs,
<span acronym-label="ldp" acronym-form="singular+short">ldp</span>
pipelines, notebooks, permissions, cluster attachments, and the Lakeflow
Connect connection objects. Declarative Automation Bundles, formerly
Databricks Asset Bundles, declare these alongside the source code, so
one <span class="mark">databricks bundle deploy</span> recreates the
workspace state for a new environment . The handful of Databricks
objects the bundle format does not yet have a native type for (the
secret scope container, Unity Catalog storage credential, and Unity
Catalog external location) are created by a small post deploy shell
script colocated with the platform layer at
<span class="mark">src/platform/scripts/bootstrap.sh</span> . The
framework deliberately keeps a single state owner per resource. Mixing
the bundle with the Databricks Terraform provider would split state
ownership for the same Databricks objects across two state stores and
create promotion drift.

The **source side tier** owns cloud infrastructure for each connector
that needs to bring up its source system or supporting cloud resources
(S3 buckets, <span acronym-label="iam"
acronym-form="singular+short">iam</span> roles, OIDC trust policies,
source side VMs). Each connector ships a Terraform runtime under
<span class="mark">src/connectors/\<source\>/</span>
<span class="mark">runtime/</span> , scoped to that connector and never
referencing Databricks resources. This keeps the layering rule of
<a href="#sec:impl-layering-rule" data-reference-type="autoref"
data-reference="sec:impl-layering-rule">[sec:impl-layering-rule]</a>
clean: per connector setup code has no upward or sideways dependencies.
Organizations preferring Pulumi or OpenTofu can substitute those at this
tier without touching the Databricks tier.

One bundle exists per target, with three targets structuring the
promotion path (development, staging, production). Each target overrides
the catalog name, secret scope, and compute target. Both tiers are
declarative, so the same flow moves a change through the three
environments without hand editing.

#### Project Structure

The project is a monorepo: <span class="mark">src/</span> for pipeline
source code, <span class="mark">tests/</span> for the test suite,
<span class="mark">config/</span> for lookup tables, and bundle files at
the root. The Unity Catalog layout mirrors the medallion layers
(<a href="#sec:medallion-arch" data-reference-type="autoref"
data-reference="sec:medallion-arch">[sec:medallion-arch]</a>) with one
catalog per environment ( <span class="mark">appsec_dev</span> ,
<span class="mark">appsec_staging</span> ,
<span class="mark">appsec_prod</span> ). Source specific bronze and
silver tables live in <span class="mark">bronze\_\<source\></span> and
<span class="mark">silver\_\<source\></span> schemas. Cross source
silver and gold tables live in unqualified
<span class="mark">silver</span> and <span class="mark">gold</span>
schemas whose names encode the analytic, not the source. Pipeline names
mirror their source module (
<span class="mark">ingest\_\<source\></span> ,
<span class="mark">transform\_\<source\>\_silver</span> ). Column names
use <span class="mark">snake_case</span> throughout. These conventions
let governance rules target tables and pipelines by name pattern.

Each connector module under
<span class="mark">src/connectors/{source}/</span> carries the same
artifacts
(<a href="#sec:connector-abstraction" data-reference-type="autoref"
data-reference="sec:connector-abstraction">[sec:connector-abstraction]</a>):
<span class="mark">ingest.py</span> ,
<span class="mark">transform.py</span> ,
<span class="mark">mapping.yml</span> ,
<span class="mark">config.yml</span> , and a colocated
<span class="mark">tests/</span> folder. Silver to gold transformations
group by analytic rather than by source because a single gold table can
consume data from multiple connectors.

Secrets sit in the platform secret scope and are referenced by name.
Nonsensitive settings (severity, status lookups) sit colocated with the
connector code as YAML. Tuning these values is a configuration change,
not a code change. Full layout with a worked example is on the [layout
page](https://vkraus.github.io/appsec-mvp/platform/reference/project-layout/).

#### Pipeline Orchestration

Lakeflow Jobs schedules pipeline execution . A job groups tasks into a
<span acronym-label="dag" acronym-form="singular+short">dag</span> with
explicit dependencies. Jobs are defined in the bundle alongside the
resources they operate on, so scheduling promotes through the deployment
path of <a href="#sec:deployment-strategy" data-reference-type="autoref"
data-reference="sec:deployment-strategy">[sec:deployment-strategy]</a>.

One job per connector handles two sequential tasks: ingest into bronze,
then transform to silver. This gives each connector an independent
failure domain. Gold layer analytics run as separate jobs that list
their upstream connector jobs as dependencies, so a gold job starts only
after the required silver data is fresh.

Source characteristics drive frequency: high change sources
(<span acronym-label="scm" acronym-form="singular+short">scm</span>,
scanners) run hourly, stable sources (<span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span>) run daily, enrichment sources
(<span acronym-label="nvd" acronym-form="singular+short">nvd</span>,
<span acronym-label="epss" acronym-form="singular+short">epss</span>,
<span acronym-label="cisa" acronym-form="singular+short">cisa</span>
<span acronym-label="kev" acronym-form="singular+short">kev</span>)
follow their own cadences. Each task has retry count and backoff
interval. On retry exhaustion the task fails and downstream tasks do not
execute. Jobs run in parallel on ephemeral clusters.

#### Monitoring and Observability

Monitoring handles whether pipelines are working over time. The platform
provides system tables for job execution history, pipeline events, and
compute utilization . The framework tracks three dimensions: **data
freshness** (last successful ingestion timestamp against thresholds from
the scheduling frequency in
<a href="#sec:orchestration" data-reference-type="autoref"
data-reference="sec:orchestration">[sec:orchestration]</a>), **pipeline
health** (success rate, mean run duration, retry frequency, quarantine
volume, with a rising quarantine rate preceding data quality issues),
and **data quality trends** (violations of <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> expectations over time). Alerts
fire at job level (individual failures) and system level (aggregate
degradation such as multiple connectors stale simultaneously).
Thresholds and delivery channels are configuration, so framework users
tune sensitivity without redeploying pipelines.

#### Testing and Validation

Deployment level verification covers the environment and codebase.
Component level patterns live in
<a href="#sec:connector-testing" data-reference-type="autoref"
data-reference="sec:connector-testing">[sec:connector-testing]</a> and
<a href="#sec:analytics-testing" data-reference-type="autoref"
data-reference="sec:analytics-testing">[sec:analytics-testing]</a>. The
<span acronym-label="cicd" acronym-form="singular+short">cicd</span>
pipeline enforces linting, formatting, and unit tests over isolated
helpers (severity lookups, timestamp parsers, schema mapping). After
deployment, smoke tests confirm Unity Catalog objects, compute
resources, secret scopes, and <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> pipelines exist with the
expected configuration.

Tests are linked to requirement identifiers via pytest markers (
<span class="mark">@pytest.mark.requirement("REQ-TRF-SEV")</span> )
drawn from the [requirement
catalog](https://vkraus.github.io/appsec-mvp/platform/reference/catalog/).
The [source traceability
matrix](https://vkraus.github.io/appsec-mvp/platform/reference/catalog/#per-source-traceability-matrix)
applies uniformly across environment, connector, and analytics testing.

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
end to end view refined by the subsections below: ingest, transform, and
aggregate tasks along the spine, quarantine branches where validation
can fail, and the state and dedup annotations that the framework commits
to.

<div class="center">

\[Data plane flow\]Data plane flow within the framework: ingestion with
auditable high water mark state in `silver.hwm` (right), quarantine on
the Bronze side and on the Silver side for records that fail structural
or required field validation (left), SCD-2 tracking on entity tables via
`valid_from`/`valid_to`, a post mapping dedup pass that writes
`silver.dedup_links` during the transform task, and gold
`finding_group_id` clustering at the aggregate task.
<span id="fig:data-plane-flow" label="fig:data-plane-flow"></span>

</div>

#### Connector Abstraction

Every connector handles the same cross cutting concerns, but the three
categories from
<a href="#sec:component-design" data-reference-type="autoref"
data-reference="sec:component-design">[sec:component-design]</a> differ
in how much work the developer performs versus the platform or library.

##### Connector Categories

The three categories rank in a preference order set by how many of the
five cross cutting concerns (auth, pagination, rate limit, incremental
state, schema mapping) the developer must write versus delegate.

1.  **Lakeflow Connect.** Declarative, configured through the bundle,
    not coded. Authentication, pagination, rate limiting, incremental
    state, and schema inference are platform handled. Suits sources with
    a supported Lakeflow Connect integration where full table ingestion
    meets requirements. The connector becomes a declaration that cannot
    drift from the framework contract.

2.  **<span acronym-label="sdk" acronym-form="singular+short">sdk</span>
    connectors.** Use a source provided client library
    (<span acronym-label="aws" acronym-form="singular+short">aws</span>
    <span acronym-label="sdk" acronym-form="singular+short">sdk</span>
    for Python, PyGitHub, python-gitlab) that encapsulates transport,
    pagination, and rate limiting. The developer controls extraction
    logic. The library is typed against the source object model, so
    upstream <span acronym-label="api"
    acronym-form="singular+short">api</span> changes appear as library
    upgrades, not silent breakage in hand written code.

3.  **<span acronym-label="rest"
    acronym-form="singular+short">rest</span> <span acronym-label="api"
    acronym-form="singular+short">api</span> with
    <span acronym-label="dltool"
    acronym-form="singular+short">dltool</span>.** The open source
    <span acronym-label="dltool"
    acronym-form="singular+short">dltool</span> library provides
    prebuilt authentication, pagination, and incremental loading
    components composed declaratively. The developer specifies
    endpoints, schema mapping, and extraction parameters. More connector
    code than the prior two categories, but mechanical concerns still
    sit in tested library components rather than hand written
    <span acronym-label="http"
    acronym-form="singular+short">http</span>.

Each step shifts more concerns from platform custody into connector
code. Hand written <span acronym-label="http"
acronym-form="singular+short">http</span> clients sit outside the order
entirely and are not sanctioned: they reintroduce every concern the
three categories above delegate.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> demonstrates
all three categories.
<a href="#fig:connector-decision" data-reference-type="autoref"
data-reference="fig:connector-decision">[fig:connector-decision]</a>
summarizes the selection.

<div class="center">

\[Connector category selection\]Connector category selection. Terminal
panels show how the five cross cutting concerns are handled:
**platform** (managed), **library** (SDK or dlt), or **developer** (code
per connector). <span id="fig:connector-decision"
label="fig:connector-decision"></span>

</div>

##### Cross cutting concerns

2.25ex 1ex .2ex 1ex .2ex Authentication Source <span acronym-label="api"
acronym-form="plural+short">apis</span> use <span acronym-label="pat"
acronym-form="plural+short">pats</span>, OAuth 2.0 client credentials,
or service account keys. Credentials live in the platform secret scope.
Each connector declares which type it requires and the framework
resolves it at runtime. This keeps secrets out of code and enables
credential rotation without redeploying.

2.25ex 1ex .2ex 1ex .2ex Pagination <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="plural+short">apis</span> return results in pages. Two
strategies cover most sources: offset based (page number and size) and
cursor based (opaque token). The connector abstraction hides pagination
so downstream code sees a stream of records. GraphQL sources (GitHub
<span acronym-label="api" acronym-form="singular+short">api</span>) use
cursor based pagination exclusively.

2.25ex 1ex .2ex 1ex .2ex Rate limiting On <span acronym-label="http"
acronym-form="singular+short">http</span> 429 the connector pauses for
the duration in the response headers before retrying. For sources
without rate limit headers, a configurable per source rate limit
prevents exceeding undocumented thresholds. Transient errors
(<span acronym-label="http" acronym-form="singular+short">http</span>
5xx) trigger exponential backoff with a configurable retry cap.

2.25ex 1ex .2ex 1ex .2ex Incremental state Full re-ingestion does not
scale at enterprise volumes. Each connector maintains a high water mark
(timestamp or cursor) persisted in a state table within the bronze
schema. For sources supporting <span acronym-label="cdc"
acronym-form="singular+short">cdc</span>, the connector consumes change
events directly. Two patterns drive the choice. **Periodic global**
sources (server scanners, <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span>, <span acronym-label="scm"
acronym-form="singular+short">scm</span> polling
<span class="mark">updated_at</span> ) use a timestamp high water mark.
**CI/CD step** sources (per commit <span acronym-label="cli"
acronym-form="singular+short">cli</span> tools) use a per repository
commit <span acronym-label="sha"
acronym-form="singular+short">sha</span> or run identifier. Both
patterns share the same state table schema.

##### Connector Contract

Every connector module exposes two entry points.
<span class="mark">ingest</span> accepts a run identifier and state
object, pulls new records, and returns a batch descriptor with the rows
landed and the advanced high water mark.
<span class="mark">transform</span> accepts a bronze dataframe and
returns a silver dataframe conforming to the entity or finding pattern
(<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>). Neither
writes to silver itself. The pipeline runner persists the returned
dataframe, so both entry points are testable with in memory fixtures.
For artifact path connectors whose source specific ingestion primitive
already uses the <span class="mark">ingest</span> symbol, the contract
wrapper is exposed as <span class="mark">ingest_contract</span> .

The state object has a fixed structure across categories: high water
mark value, source system identifier, and optional backfill parameters.
The runner loads state before <span class="mark">ingest</span> and
persists it after a successful write, giving consistent resume semantics
regardless of category. Lakeflow Connect connectors satisfy the contract
through platform configuration. <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> and <span acronym-label="rest"
acronym-form="singular+short">rest</span> <span acronym-label="api"
acronym-form="singular+short">api</span> connectors implement the two
operations directly.

##### Connector Artifacts

Adding a connector populates the module template from
<a href="#sec:project-structure" data-reference-type="autoref"
data-reference="sec:project-structure">[sec:project-structure]</a> with
the same set of artifacts across all three categories:

1.   <span class="mark">config.yml</span> : source parameters (base
    <span acronym-label="url" acronym-form="singular+short">url</span>,
    endpoints, pagination strategy, rate limit, high water mark column,
    target bronze table).

2.  A secret scope entry registering the connector credential,
    referenced from <span class="mark">config.yml</span> .

3.   <span class="mark">ingest.py</span> : implements
    <span class="mark">ingest(run_id, state) -\> batch</span> . Lakeflow
    Connect connectors leave this empty and declare the resource in the
    bundle fragment. <span acronym-label="sdk"
    acronym-form="singular+short">sdk</span> connectors delegate to the
    client library, and <span acronym-label="dltool"
    acronym-form="singular+short">dltool</span> connectors compose
    prebuilt components.

4.   <span class="mark">transform.py</span> : implements
    <span class="mark">transform(bronze_df) -\> silver_df</span>
    targeting the silver table for the category
    (<a href="#sec:entity-model" data-reference-type="autoref"
    data-reference="sec:entity-model">[sec:entity-model]</a>).

5.   <span class="mark">mapping.yml</span> ,
    <span class="mark">severity.yml</span> ,
    <span class="mark">status.yml</span> : declarative column
    expressions and lookups, maintained as configuration so vocabulary
    updates do not require a pipeline redeploy.

6.  A bundle fragment under <span class="mark">resources/</span>
    declaring the two task connector job
    (<a href="#sec:ingestion-patterns" data-reference-type="autoref"
    data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>).

7.   <span class="mark">tests/</span> : ingestion and transformation
    tests per
    <a href="#sec:connector-testing" data-reference-type="autoref"
    data-reference="sec:connector-testing">[sec:connector-testing]</a>.

Silver and gold do not change: the silver tables from
<a href="#sec:entity-model" data-reference-type="autoref"
data-reference="sec:entity-model">[sec:entity-model]</a> take the new
source through the schema mapping and gold analytics keep working.

#### Ingestion Patterns

Ingestion moves data from source <span acronym-label="api"
acronym-form="plural+short">apis</span> into bronze. All connectors
follow the same landing pattern, with source type specific variations
below.

##### Common landing pattern

Every ingestion run produces append only writes to the target bronze
table. The full <span acronym-label="api"
acronym-form="singular+short">api</span> response is preserved in
<span class="mark">\_raw_payload</span> alongside the bronze envelope
columns (<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>). No
field filtering or transformation occurs. Bronze is an exact copy. The
batch identifier enables idempotent replays: a failed run reexecutes the
same batch and overwrites only those records. For sources where merge
semantics are appropriate (e.g., <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> entity snapshots), the
connector upserts on the natural identifier. Records failing structural
validation at landing (malformed <span acronym-label="json"
acronym-form="singular+short">json</span>, unexpected schema changes)
are routed to quarantine tables per source with raw payload, error, and
batch identifier. No record is silently dropped .

##### Bronze table template

Every bronze table follows the same structure extending the schema
pattern from
<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>. The
<span class="mark">\_hwm_value</span> column carries the high water mark
per record, making the resume position auditable and supporting targeted
rebuilds. Tables are partitioned by ingestion date. The naming
convention is
<span class="mark">appsec\_\<env\>.bronze\_\<source\>.\<entity\></span>
(for example,
<span class="mark">appsec_prod.bronze_github.code_scanning_alerts</span>
). A connector author fills in three blanks per entity: source name,
entity name, and high water mark source field.

##### Connector job template

Every connector instantiates the same Lakeflow Job layout
(<a href="#sec:orchestration" data-reference-type="autoref"
data-reference="sec:orchestration">[sec:orchestration]</a>): a two task
<span acronym-label="dag" acronym-form="singular+short">dag</span> where
ingest produces bronze and transform consumes it to produce silver, with
the transform task declaring a hard dependency on the ingest task. Retry
configuration is identical across connectors (three attempts, capped
exponential backoff). The bundle fragment exposes a fixed set of
parameters (source name, target catalog, high water mark reset flag,
cron expression). The full fragment is on the [job
template](https://vkraus.github.io/appsec-mvp/platform/reference/connector-job-template/).

The common landing pattern and bronze table template apply uniformly
across categories. Parameters for each source live in
<span class="mark">src/connectors/{source}/config.yml</span> . Category
specific notes (incremental strategy preference for
<span acronym-label="scm" acronym-form="singular+short">scm</span>,
scanner deployment styles, <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> relationship traversal) are on
the [capability
matrix](https://vkraus.github.io/appsec-mvp/platform/reference/source-capability-matrix/).

#### Transformation Patterns

Transformations move data from bronze to the silver entity and finding
tables from <a href="#sec:entity-model" data-reference-type="autoref"
data-reference="sec:entity-model">[sec:entity-model]</a>. Each
transformation is a <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> pipeline reading from one or
more bronze tables and writing to a silver table. Five patterns compose
the path from bronze to silver.

##### Schema mapping

Each connector has a schema mapping that extracts typed columns from the
bronze raw payload, applies type casts, and assigns the surrogate key.
Mappings are declared as column expressions in the
<span acronym-label="ldp" acronym-form="singular+short">ldp</span>
pipeline. The <span class="mark">mapping.yml</span> for every connector
has the same structure: a target table declaration and column blocks
naming the target column, the <span acronym-label="json"
acronym-form="singular+short">json</span> path into
<span class="mark">\_raw_payload</span> , and the cast. Severity and
status lookups live separately as key value maps. The [SonarQube mapping
example](https://vkraus.github.io/appsec-mvp/connectors/sast/sonarqube/#mapping-example)
shows a worked instance.

##### Normalization

Three rules bring source data to a common form:

- **Severity harmonization.** Tools use different scales (catalogued in
  <a href="#sec:selected-sources" data-reference-type="autoref"
  data-reference="sec:selected-sources">[sec:selected-sources]</a>). The
  framework maps each native scale to a four level model (critical,
  high, medium, low) through per tool lookup tables. Undocumented or
  missing values fall through to a configurable default (
  <span class="mark">medium</span> ) and trigger a data quality warning.

- **Status normalization.** Lifecycle states vary across tools. A per
  tool status mapping translates them to a five state model (open,
  confirmed, resolved, false_positive, wontfix).

- **Timestamp standardization.** All timestamps are parsed during schema
  mapping and stored as <span acronym-label="utc"
  acronym-form="singular+short">utc</span> datetime columns.

##### Data quality validation

<span acronym-label="ldp" acronym-form="singular+short">ldp</span>
expectations enforce constraints on every record entering silver.
Expectations are declared alongside the transformation and checked at
runtime. Examples: severity must be one of four standard values, status
must be one of five standard states, repository foreign keys must
reference an existing silver entity, and timestamps must fall within a
plausible range. Violating records are quarantined, not propagated,
consistent with the quarantine pattern at ingestion.

##### Deduplication application

Deduplication keys are defined in the Silver Finding pattern
(<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a>). The
transformation runs a post mapping dedup pass that writes
<span class="mark">dedup_links</span> records for every overlapping pair
sharing a <span class="mark">repository_id</span> . Deduplicated
findings are not deleted. The link preserves traceability while
establishing the reference finding. No fuzzy matching is performed, and
line number divergence is handled at Gold via
<span class="mark">finding_group_id</span> .

##### Business context attribution

Findings are linked to business applications through the
<span class="mark">app_repo_mapping</span> relationship table. Because
the mapping is many to many, findings inherit application context
through a join instead of a direct foreign key, which enables the per
application aggregations in
<a href="#sec:aggregation-model" data-reference-type="autoref"
data-reference="sec:aggregation-model">[sec:aggregation-model]</a>. The
primary authoritative mapping is expected from the
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>
connector when the inventory carries repository relationships. The
relationship table can also be populated by deterministic supplemental
linkers (for example application code matching in repository names, used
by the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span>) or by automated inference in
the <span acronym-label="ml" acronym-form="singular+short">ml</span>
workflows from
<a href="#sec:analytics-patterns" data-reference-type="autoref"
data-reference="sec:analytics-patterns">[sec:analytics-patterns]</a>.

The framework treats attribution as a data quality outcome rather than a
binary join. Relationship records preserve the link source and an
attribution state so downstream consumers can distinguish authoritative,
supplemental, inferred, and failed matches.
<a href="#tab:attribution-state-model" data-reference-type="autoref"
data-reference="tab:attribution-state-model">[tab:attribution-state-model]</a>
defines the states and required downstream behavior.

<div class="center">

\[Application attribution state model\]Application attribution state
model for <span class="mark">app_repo_mapping</span> .
<span id="tab:attribution-state-model"
label="tab:attribution-state-model"></span>

| **State** | **Meaning**                                                                                                                                                                                                                                                                                        | **Gold and ticketing behavior**                                                                                                                                                                                        |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           | No application relationship exists for the repository, <span acronym-label="url" acronym-form="singular+short">url</span>, or deployment coordinate.                                                                                                                                               | Gold keeps the finding in unattributed counts. Automated ticketing routes to security triage or data quality review rather than to an application owner.                                                               |
|           | A deterministic linker finds exactly one application code in a repository name or other governed naming field.                                                                                                                                                                                     | Gold includes the finding in the application risk score with supplemental attribution. Ticketing may proceed if the organization accepts the naming convention as a routing rule.                                      |
|           | A <span acronym-label="cmdb" acronym-form="singular+short">cmdb</span> relationship links the application and repository or deployment asset.                                                                                                                                                      | Gold treats the relationship as authoritative. Ticketing routes to the application owner from the inventory.                                                                                                           |
|           | A <span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>, <span acronym-label="scm" acronym-form="singular+short">scm</span>, or registry field carries an explicit repository <span acronym-label="url" acronym-form="singular+short">url</span> or identifier for the application. | Gold treats the relationship as authoritative. Ticketing routes to the mapped application owner.                                                                                                                       |
|           | A rule based or <span acronym-label="ml" acronym-form="singular+short">ml</span> workflow proposes an application with a confidence score but without an authoritative source.                                                                                                                     | Gold separates inferred context from authoritative context. Ticketing requires review or uses a lower automation level.                                                                                                |
|           | More than one application matches the same repository, <span acronym-label="url" acronym-form="singular+short">url</span>, or deployment coordinate with no clear winner.                                                                                                                          | Gold counts the finding in an ambiguity bucket and excludes it from owner level <span acronym-label="sla" acronym-form="singular+short">sla</span> metrics. Automated owner ticketing is suppressed or sent to triage. |
|           | The matched application or repository is inactive, expired, ownerless, or outside the valid time window.                                                                                                                                                                                           | Gold flags stale context and keeps the finding visible. Ticketing routes to inventory correction before remediation ownership is assigned.                                                                             |

</div>

#### Testing and Validation

Connector tests live beside the connector at
<span class="mark">src/connectors/{source}/tests/</span> , not in a
central suite. <span class="mark">test_ingest.py</span> covers the
ingestion contract, <span class="mark">test_transform.py</span> covers
the transformation, and <span class="mark">fixtures/</span> holds
<span acronym-label="json" acronym-form="singular+short">json</span>
inputs named <span class="mark">{endpoint}\_{scenario}.json</span> .
Fixtures are recorded once from a representative source instance and
frozen, so the suite runs in <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> without network access. The
stack adds three libraries on top of pytest: an
<span acronym-label="http" acronym-form="singular+short">http</span>
mocking library, a PySpark DataFrame assertion library (
<span class="mark">chispa</span> ), and <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> expectations for runtime
checks. Each test carries a
<span class="mark">@pytest.mark.requirement(...)</span> marker so the
traceability matrix links results to the identifiers in
<a href="#tab:connector-req-snapshot" data-reference-type="autoref"
data-reference="tab:connector-req-snapshot">[tab:connector-req-snapshot]</a>.

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

The framework target is that new connectors do not merge until every
applicable marker above passes in <span acronym-label="cicd"
acronym-form="singular+short">cicd</span>.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> reports the
evidence level reached by the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> connectors and names the paths
that require live systems or remain deferred.

### Analytics and Serving Framework

The final stage turns Silver data into Gold outputs for stakeholders.
<a href="#sec:aggregation-model" data-reference-type="autoref"
data-reference="sec:aggregation-model">[sec:aggregation-model]</a>
defined **which** Gold tables exist. The sections below define **how**
those tables are computed and how results reach analytical, operational,
and event driven consumers.

#### Analytics Patterns

Gold layer computations fall into two categories: rule based analytics
applying deterministic formulas to silver data, and
<span acronym-label="ml" acronym-form="singular+short">ml</span> driven
analytics learning patterns from historical data. Both produce outputs
following the gold aggregation pattern from
<a href="#sec:schema-patterns" data-reference-type="autoref"
data-reference="sec:schema-patterns">[sec:schema-patterns]</a> and run
under the *aggregate task* of the data plane
(<a href="#fig:data-plane-flow" data-reference-type="autoref"
data-reference="fig:data-plane-flow">[fig:data-plane-flow]</a>).

##### Extension blueprint

Adding an analytics workflow follows the same procedure as a connector:
define the business question and stakeholder, choose rule based or
<span acronym-label="ml" acronym-form="singular+short">ml</span>,
implement as a <span acronym-label="ldp"
acronym-form="singular+short">ldp</span> pipeline, notebook job, or
MLflow experiment, then wire the output to a gold table with the
configured refresh strategy. The framework-level artifacts are the
executable workflow, its DDL or table/view declaration, configuration, a
bundle fragment under <span class="mark">resources/</span> , and tests.
The <span acronym-label="mvp" acronym-form="singular+short">mvp</span>
realizes this under
<span class="mark">src/analytics/notebooks/gold/</span> ,
<span class="mark">src/analytics/resources/</span> , and
<span class="mark">src/analytics/tests/</span> . Silver is the stable
boundary: authoring a new analytic never requires connector edits, and
adding a connector never requires analytics edits.

##### Rule Based Analytics

Three patterns cover the rule based work. **Composite scoring** combines
signals into a single metric (the application risk score weights open
findings by severity, multiplies by <span acronym-label="epss"
acronym-form="singular+short">epss</span>, and factors in criticality
tier, with configurable weights). **Time series aggregation** rolls up
findings at daily, weekly, and monthly intervals with period metrics and
derived indicators (period over period change, moving averages).
**Threshold classification** assigns categorical labels (risk tiers,
coverage gaps, <span acronym-label="sla"
acronym-form="singular+short">sla</span> breaches) downstream consumers
can filter and alert on. Refresh is incremental where each record maps
to a single grain partition. Full refresh applies for metrics needing
global state (cross application percentiles, organization wide
distributions).

##### ML Driven Analytics

<span acronym-label="ml" acronym-form="singular+short">ml</span>
analytics learn from historical silver and gold data. The framework
supports four use cases: **composite risk scoring** learns which signal
combinations preceded security incidents, **false positive prediction**
estimates probability from historical triage decisions, **remediation
time estimation** predicts <span acronym-label="mttr"
acronym-form="singular+short">mttr</span> for <span acronym-label="sla"
acronym-form="singular+short">sla</span> forecasting, and **anomaly
detection** flags spikes in finding volume or severity shifts. The
exploit prediction direction draws on the published
<span acronym-label="epss" acronym-form="singular+short">epss</span>
methodology .

Framework commitments across the four are narrow. Outputs land in Gold
tables under the aggregation pattern, every run is tracked in MLflow
with the run ID recorded on output rows, and retraining ships in the
same <span acronym-label="dab" acronym-form="singular+short">dab</span>
bundle as ingestion so deploys and rollbacks are atomic. Feature Store
supplies reusable feature tables, and Model Serving caches real time
inference results in Lakebase . Feature selection, splits, algorithms,
and cadence are left to
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>.

#### Serving Patterns

The serving layer delivers gold outputs to the data consumers from
<a href="#sec:component-design" data-reference-type="autoref"
data-reference="sec:component-design">[sec:component-design]</a>. Three
delivery modes address different access patterns and latency
requirements.

##### Analytical serving

Analytical serving targets dashboards and ad hoc analysis through the
<span acronym-label="olap" acronym-form="singular+short">olap</span>
path. A <span acronym-label="sql"
acronym-form="singular+short">sql</span> warehouse queries gold Delta
tables, and materialized views cache recurring query patterns.
Stakeholder specific <span acronym-label="sql"
acronym-form="singular+short">sql</span> views (executive overviews,
team dashboards, security engineering views) sit on top of the gold
tables rather than as separate copies, keeping consumers consistent.

##### Operational serving

Operational serving targets low latency workloads through the
<span acronym-label="oltp" acronym-form="singular+short">oltp</span>
path. Lakebase serves Unity Catalog data through synced tables: Unity
Catalog tables are copied into Lakebase Postgres and kept current by
managed Lakeflow pipelines, so applications can query the data through
standard Postgres interfaces . Three workloads use this path:
remediation state lookups for developer workflow integration,
operational <span acronym-label="api"
acronym-form="plural+short">apis</span> exposed through PostgREST
without custom <span acronym-label="api"
acronym-form="singular+short">api</span> code, and cached
<span acronym-label="ml" acronym-form="singular+short">ml</span>
inference results for real time risk assessment.

##### Event driven serving

Event driven serving pushes data to external systems instead of waiting
for queries.

**Automated issue creation** triggers on new critical findings or
<span acronym-label="sla" acronym-form="singular+short">sla</span>
breaches, creating tickets in issue trackers (Jira, ServiceNow) with
idempotency guards against reruns.

**Threshold based notifications** alert stakeholders when metrics cross
configured boundaries (risk score, new <span acronym-label="kev"
acronym-form="singular+short">kev</span> listing,
<span acronym-label="sla" acronym-form="singular+short">sla</span> drop)
through configured channels.

**<span acronym-label="siem" acronym-form="singular+short">siem</span>
and <span acronym-label="soar" acronym-form="singular+short">soar</span>
feeds** push events to platforms such as Lakewatch
(<a href="#sec:lakewatch" data-reference-type="autoref"
data-reference="sec:lakewatch">[sec:lakewatch]</a>) via
<span acronym-label="cdc" acronym-form="singular+short">cdc</span> on
gold tables. The Lakewatch path is a compatibility direction, not
implementation evidence, because the author did not have access to the
Lakewatch Private Preview.

**Bidirectional synchronization** flows external status updates back to
silver via scheduled polling or webhooks, so gold remediation metrics
reflect actual resolution progress.

#### Testing and Validation

Rule based analytics are validated by snapshot comparison. Each test
supplies silver inputs with known values and confirms the gold output
matches expected exactly via PySpark DataFrame assertions. Test cases
cover computation boundaries (zero findings, all critical, missing
enrichment, period bucketing at month boundaries, threshold tier
cutoffs) plus a refresh idempotency case that runs the pipeline twice on
the same input.

<span acronym-label="ml" acronym-form="singular+short">ml</span>
analytics are validated by held out evaluation and drift monitoring.
MLflow’s <span class="mark">evaluate()</span> computes accuracy,
precision, recall, and F1, and
<span class="mark">validate_evaluation_results()</span> gates promotion
against configured thresholds and the registered baseline . In
production, prediction distribution comparisons flag drift before model
quality degrades. Serving endpoints are exercised through
<span acronym-label="http" acronym-form="singular+short">http</span>
clients to verify correctness and latency against the targets in
<a href="#sec:serving-patterns" data-reference-type="autoref"
data-reference="sec:serving-patterns">[sec:serving-patterns]</a>.

The complete framework suite covers every gold table (metric
correctness, boundaries, idempotency), every <span acronym-label="ml"
acronym-form="singular+short">ml</span> model (convergence, accuracy,
drift, promotion gating), and every serving endpoint (correctness and
latency). The <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> instantiates the rule based
part of this target and reports its concrete analytics evidence in
<a href="#sec:impl-results" data-reference-type="autoref"
data-reference="sec:impl-results">[sec:impl-results]</a>.
<span acronym-label="ml" acronym-form="singular+short">ml</span> model
training and production serving latency evidence remain outside the
submitted implementation.

### Extension Blueprint and AI Assistance

AI assisted extension is built into the artifact design. Connector
files, analytics jobs, and tests are templates with fixed inputs and
expected outputs. The [<span acronym-label="mvp"
acronym-form="singular+short">mvp</span>
documentation](https://vkraus.github.io/appsec-mvp/) packages the
procedure as four Claude Code skills:
<span class="mark">analyze-source</span> ,
<span class="mark">provision-source</span> ,
<span class="mark">generate-connector</span> , and
<span class="mark">validate-implementation</span> . The first skill
writes the source reference sections from official
<span acronym-label="api" acronym-form="singular+short">api</span>
documentation. The second emits source runtime infrastructure. The third
produces the connector artifacts and Databricks runtime layout. The
fourth runs the test suite until requirements from the specification are
mapped to passing tests. A data file for each source at
<span class="mark">src/connectors/\<source\>/operational.yml</span>
records deployment values such as cloud account, secret scope name, and
target bronze table. Missing fields are gathered during a skill run, so
the framework user does not have to know the schema upfront.

It was a conscious design decision that the set consists of four skills
rather than a dedicated skill for every combination of role and
application security category. This follows the recommended pattern for
skills that span multiple variants of the same task . Each
<span class="mark">SKILL.md</span> carries the role wide procedure.
Guidance per category lives one level deeper, in a
<span class="mark">references/\<category\>.md</span> file that the agent
reads on demand. The seven application security categories are
<span class="mark">cmdb</span> , <span class="mark">scm</span> ,
<span class="mark">sast</span> , <span class="mark">sca</span> ,
<span class="mark">secret</span> , <span class="mark">dast</span> , and
<span class="mark">waf</span> .

This structure inherits two properties from the underlying skills
mechanism . The metadata overhead in the agent system prompt remains
fixed at four descriptions, regardless of how many categories are
eventually added to the framework. The procedure is authored once and
shared across categories.
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> reports on
the execution of the catalog against the selected sources. The approach
of this thesis relies on modern <span acronym-label="ai"
acronym-form="singular+short">ai</span> assistance for connector
construction. A well specified framework plus a compact skill set makes
the integration layer reproducibly constructible, with full traceability
from test to requirement directly in the specification.

## MVP Implementation

The reference implementation instantiates the framework from
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> as a Declarative
Automation Bundle, formerly Databricks Asset Bundle . It covers the
three connector categories plus the artifact ingestion pattern across
the nine sources selected in
<a href="#sec:selected-sources" data-reference-type="autoref"
data-reference="sec:selected-sources">[sec:selected-sources]</a>: two
<span acronym-label="scm" acronym-form="singular+short">scm</span>
platforms, four scanners across static and dynamic testing, a
<span acronym-label="cmdb" acronym-form="singular+short">cmdb</span>, a
secrets tool, and a runtime security source. It is a minimum viable
product. Open items are listed in
<a href="#sec:impl-results" data-reference-type="autoref"
data-reference="sec:impl-results">[sec:impl-results]</a>.

The contribution is twofold. The contract of three categories holds
across all nine sources, and the resulting code fits one small repeating
module layout. The chain of four skills was run across the nine source
specifications and produced the connector modules, runtime artifacts,
bundle fragments, tests, and documentation evidence, with reviewer
subagent cycles catching named defect classes
(<a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a>,
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>). The implementation
evidence is not identical for every source: some sources were exercised
against live systems, some are backed only by fixtures, some Spark
wrappers write Silver frames with rows, and some contract wrappers still
return empty Silver frames while mapping helpers at row level are
tested. <a href="#sec:impl-results" data-reference-type="autoref"
data-reference="sec:impl-results">[sec:impl-results]</a> states those
boundaries. <a href="#sec:impl-representative-connectors"
data-reference-type="autoref"
data-reference="sec:impl-representative-connectors">[sec:impl-representative-connectors]</a>
shows two ends of the category range in concrete code: ServiceNow on
Lakeflow Connect and GitHub on PyGitHub .

### Methodology

The implementation follows the procedure below for every source in
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

2.  **Instantiate the module layout for the connector.** Every connector
    carries the same files under
    <span class="mark">src/connectors/\<source\>/</span> :
    <span class="mark">ingest.py</span> ,
    <span class="mark">transform.py</span> ,
    <span class="mark">mapping.yml</span> ,
    <span class="mark">config.yml</span> ,
    <span class="mark">severity.yml</span> , and
    <span class="mark">status.yml</span> . Bundle resources, tests, and
    the secret loading script are colocated with the connector code. For
    Lakeflow Connect sources, <span class="mark">ingest.py</span> is
    reduced to a module docstring and ingestion is declared in the
    bundle fragment as a <span class="mark">pipelines</span> resource
    with an <span class="mark">ingestion_definition</span> .

3.  **Use the mapping artifact as the transformation specification.**
    The <span class="mark">mapping.yml</span> file for the connector
    records the intended column derivation from bronze to silver given
    by the [published mapping
    requirements](https://vkraus.github.io/appsec-mvp/platform/reference/canonical-mapping/).
    Severity and status lookups live in the connector folder as
    <span class="mark">severity.yml</span> and
    <span class="mark">status.yml</span> .
    <span class="mark">src/platform/silver.py</span> provides severity
    rank and status bucket normalization helpers and deduplication
    utilities shared across connectors. The current
    <span acronym-label="mvp" acronym-form="singular+short">mvp</span>
    keeps the mapping as the authoritative artifact but applies it
    through Python helpers and Spark code for each source rather than
    through a generic YAML applicator. Several connectors have tested
    helpers at row level while their Spark contract wrapper still
    returns an empty frame with the target schema.
    <a href="#sec:future-work" data-reference-type="autoref"
    data-reference="sec:future-work">[sec:future-work]</a> carries the
    declarative applicator and wrapper completion as a thread.

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
    runtime. Tests live under
    <span class="mark">src/connectors/\<source\>/tests/</span> and are
    linked to requirement IDs through
    <span class="mark">@pytest.mark.requirement</span> markers.

5.  **Run the skill chain pass for the source.** The Claude Code skill
    chain (analyze-source, provision-source, generate-connector,
    validate-implementation) executes against the source and writes
    evidence rows to the documentation site: an Implementation log entry
    per pass and a Validation table keyed by requirement IDs. Each skill
    pass is then reviewed by a separate subagent (one for spec
    compliance, one for code quality), whose findings are folded back as
    follow up commits before the next source moves forward.
    <a href="#sec:iteration-summary" data-reference-type="autoref"
    data-reference="sec:iteration-summary">[sec:iteration-summary]</a>
    records the defect classes the reviewer cycle caught.

The procedure is repeatable because the source category is resolved
before generation and the connector folder layout stays fixed across
categories. A generator that emits the layout for a new source only
needs to vary <span class="mark">ingest.py</span> and the bundle
resource kind. The [documentation
site](https://vkraus.github.io/appsec-mvp/) makes the run auditable by
recording the Implementation log and Validation table for each source.

In this thesis, <span acronym-label="ai"
acronym-form="singular+short">ai</span> instantiable means prompt based
generation through tailored agent skills created for the framework. The
skills encode the connector procedure, required artifacts, and
validation steps. The framework user supplies missing environment facts,
reviews generated changes, and reruns the skill chain until requirement
linked tests and reviewer checks pass.

### Project Structure

The reference implementation is distributed across two repositories that
separate the thesis document from the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> code.

- The thesis repository holds the LaTeX sources for this document.

- The <span acronym-label="mvp" acronym-form="singular+short">mvp</span>
  implementation repository holds the reference implementation described
  in the remainder of this section. The source for the documentation
  site lives inside the same repository under
  <span class="mark">mkdocs/</span> . The [published
  site](https://vkraus.github.io/appsec-mvp/) is the framework user
  reference and the trail of evidence for each connector.

#### Layering rule

The repository is organized into three install layers with no upward or
sideways dependencies in setup code: platform, then connectors, then
analytics. The platform layer must not pre-declare resources for any
specific connector. No source schemas, volumes, connections, or secrets
live in <span class="mark">src/platform/resources/</span> . Each
connector owns its own bronze and silver schemas, secret loading script,
and bundle resources. The analytics layer reads only the connector
agnostic silver tables ( <span class="mark">silver.findings</span> ,
<span class="mark">silver.repositories</span> ,
<span class="mark">silver.applications</span> ,
<span class="mark">silver.app_repo_mapping</span> ,
<span class="mark">silver.hwm</span> , and
<span class="mark">silver.suppression_rules</span> ). The one ordering
constraint is data level, not setup code level. An
<span acronym-label="scm" acronym-form="singular+short">scm</span>
connector (GitHub or GitLab) must run first at job time because non
<span acronym-label="scm" acronym-form="singular+short">scm</span>
connectors map findings onto repository entities populated by
<span acronym-label="scm" acronym-form="singular+short">scm</span>. The
bundle deploys all declared resources regardless of install order.

#### Component colocation

Inside the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> implementation repository,
every component (the platform, each connector, the analytics layer) owns
its code, its tests, its bundle resources, its scripts, and (for
connectors that bring up source systems) an optional Terraform runtime.
Adding a new source is one new folder under
<span class="mark">src/connectors/</span> . There are no top level
<span class="mark">tests/</span> , <span class="mark">config/</span> ,
<span class="mark">resources/</span> , <span class="mark">sql/</span> ,
or <span class="mark">infra/terraform/</span> directories.
<a href="#lst:mvp-tree" data-reference-type="autoref"
data-reference="lst:mvp-tree">[lst:mvp-tree]</a> shows the realized
layout with one connector of each category expanded.

```
appsec-mvp/
|-- databricks.yml                       # bundle root
|-- pyproject.toml                       # package metadata
|-- mkdocs/                              # docs site
|-- examples/end-to-end-demo/            # demo across scanners
|-- src/
|   |-- platform/                        # shared primitives
|   |   |-- silver.py                    # severity, status, dedup
|   |   |-- hwm.py, schemas.py, ...      # HWM and schemas
|   |   |-- resources/{platform,bootstrap-job}.yml
|   |   |-- scripts/bootstrap.sh         # bootstrap after deploy
|   |   |-- sql/silver_tables.sql        # silver DDL
|   |   \-- tests/                       # primitive tests
|   |-- connectors/
|   |   |-- servicenow/                  # Lakeflow Connect
|   |   |   |-- ingest.py                # contract wrapper
|   |   |   |-- transform.py
|   |   |   |-- mapping.yml, config.yml
|   |   |   |-- severity.yml, status.yml
|   |   |   |-- resources/{schemas,connection,pipeline,job}.yml
|   |   |   |-- scripts/load-secrets.sh
|   |   |   |-- runtime/                 # source Terraform
|   |   |   \-- tests/
|   |   |-- github/                      # SDK connector
|   |   |   |-- ingest.py, transform.py
|   |   |   |-- mapping.yml, config.yml
|   |   |   |-- severity.yml, status.yml
|   |   |   |-- resources/{schemas,job}.yml
|   |   |   |-- scripts/load-secrets.sh
|   |   |   |-- runtime/
|   |   |   \-- tests/
|   |   \-- (gitlab, sonarqube, semgrep, owasp_zap, dependency_track,
|   |       trufflehog, aws_waf): same layout
|   \-- analytics/                       # Gold and app assets
|       |-- notebooks/gold/              # Gold datasets and view
|       |-- lib/                         # shared helpers
|       |-- app/                         # app API endpoints
|       |-- resources/{schemas,job,online_tables,app}.yml
|       \-- tests/                       # analytics tests
```

The bundle resources for each source are colocated:
<span class="mark">src/connectors/\<source\>/</span>
<span class="mark">resources/</span> contains
<span class="mark">schemas.yml</span> and either
<span class="mark">job.yml</span> (for <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> and
<span acronym-label="dltool" acronym-form="singular+short">dltool</span>
connectors) or <span class="mark">pipeline.yml</span> plus
<span class="mark">connection.yml</span> for Lakeflow Connect
connectors, with <span class="mark">job.yml</span> alongside for the
downstream transform task. The bundle root includes everything via the
glob <span class="mark">src/{platform,</span>
<span class="mark">connectors/\*,</span>
<span class="mark">analytics}/</span>
<span class="mark">resources/\*.yml</span> . Schemas, volumes, and
secret loading scripts move with the connector folder, so installing or
removing a connector does not touch shared files.

### Ingestion Category Assignment

Each source is resolved to one of the three ingestion categories defined
in <a href="#sec:connector-abstraction" data-reference-type="autoref"
data-reference="sec:connector-abstraction">[sec:connector-abstraction]</a>
before its connector module is written. The evaluation order is Lakeflow
Connect, then <span acronym-label="sdk"
acronym-form="singular+short">sdk</span>, then
<span acronym-label="dltool"
acronym-form="singular+short">dltool</span>. <span acronym-label="cli"
acronym-form="singular+short">cli</span> only tools fall outside the
three categories and follow the <span acronym-label="cicd"
acronym-form="singular+short">cicd</span> step artifact pattern
(<a href="#sec:ingestion-patterns" data-reference-type="autoref"
data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>).
The full per source functional requirements live on the documentation
site. The reference links below cite the deciding factor only.

- **ServiceNow**: Lakeflow Connect. Supported natively by the
  platform [(source
  reference)](https://vkraus.github.io/appsec-mvp/connectors/cmdb/servicenow/),
  so <span class="mark">ingest.py</span> carries only the contract
  wrapper and the bundle fragment declares the pipeline.

- **GitHub**: <span acronym-label="sdk"
  acronym-form="singular+short">sdk</span> via PyGitHub. Lakeflow
  Connect does not support it at <span acronym-label="mvp"
  acronym-form="singular+short">mvp</span> time, and PyGitHub covers the
  required endpoints, handles <span class="mark">Link</span> header
  pagination, and exposes rate limit status [(source
  reference)](https://vkraus.github.io/appsec-mvp/connectors/scm/github/).

- **GitLab**: <span acronym-label="sdk"
  acronym-form="singular+short">sdk</span> via python-gitlab . No
  Lakeflow Connect support, and the official client handles keyset
  pagination transparently [(source
  reference)](https://vkraus.github.io/appsec-mvp/connectors/scm/gitlab/).

- **SonarQube** : <span acronym-label="dltool"
  acronym-form="singular+short">dltool</span>. No first party Python
  <span acronym-label="sdk" acronym-form="singular+short">sdk</span>,
  and the <span class="mark">rest_api</span> source template that ships
  with <span acronym-label="dltool"
  acronym-form="singular+short">dltool</span> covers all requirements
  declaratively against the Web <span acronym-label="api"
  acronym-form="singular+short">api</span> [(source
  reference)](https://vkraus.github.io/appsec-mvp/connectors/sast/sonarqube/).

- **Semgrep**: artifact path. The free <span acronym-label="cli"
  acronym-form="singular+short">cli</span> writes a
  <span acronym-label="json" acronym-form="singular+short">json</span>
  report per commit from a <span acronym-label="cicd"
  acronym-form="singular+short">cicd</span> step, and
  <span class="mark">ingest.py</span> reads from
  <span class="mark">periodic/semgrep/</span> and
  <span class="mark">cicd/semgrep/</span> prefixes [(source
  reference)](https://vkraus.github.io/appsec-mvp/connectors/sast/semgrep/).

- **Dependency-Track** : <span acronym-label="dltool"
  acronym-form="singular+short">dltool</span>. No first party Python
  <span acronym-label="sdk" acronym-form="singular+short">sdk</span>,
  and the published OpenAPI document configures
  <span acronym-label="dltool"
  acronym-form="singular+short">dltool</span> directly [(source
  reference)](https://vkraus.github.io/appsec-mvp/connectors/sca/dependency-track/).

- **TruffleHog** : artifact path. <span acronym-label="cli"
  acronym-form="singular+short">cli</span> tool with no server
  <span acronym-label="api" acronym-form="singular+short">api</span>,
  same pattern as Semgrep [(source
  reference)](https://vkraus.github.io/appsec-mvp/connectors/secrets/trufflehog/).

- **<span acronym-label="owasp"
  acronym-form="singular+short">owasp</span> <span acronym-label="zap"
  acronym-form="singular+short">zap</span>**: artifact path.
  <span class="mark">ingest.py</span> supports two trigger contexts (on
  demand against the daemon, and reads of <span acronym-label="cicd"
  acronym-form="singular+short">cicd</span> step artifacts) and
  dispatches both into the same bronze table [(source
  reference)](https://vkraus.github.io/appsec-mvp/connectors/dast/owasp-zap/).

- **<span acronym-label="aws" acronym-form="singular+short">aws</span>
  <span acronym-label="waf" acronym-form="singular+short">waf</span>**:
  <span acronym-label="sdk" acronym-form="singular+short">sdk</span> via
  boto3 . The connector ships two ingestion modes selected by
  <span class="mark">config.yml::ingestion_mode</span> . The preferred
  mode reads full request logs delivered by Kinesis Data Firehose to an
  S3 prefix through an autoloader read. The fallback mode calls
  <span class="mark">boto3.client("wafv2").get_sampled_requests</span>
  with <span acronym-label="iam"
  acronym-form="singular+short">iam</span> signed credentials and
  preserves the per record <span class="mark">Weight</span>
  field [(source
  reference)](https://vkraus.github.io/appsec-mvp/connectors/waf/aws-waf/).

<a href="#tab:ingestion-category-assignment"
data-reference-type="autoref"
data-reference="tab:ingestion-category-assignment">[tab:ingestion-category-assignment]</a>
collects the nine assignments alongside the key functional requirement
that drove each choice.

<div class="center">

\[Ingestion category assignment across selected sources\]Ingestion
category assignment across the nine selected sources, showing the
category chosen for each source and the library or mechanism that
instantiates it. <span id="tab:ingestion-category-assignment"
label="tab:ingestion-category-assignment"></span>

| **Source**                                                                                                                                | **Category**                                                       | **Binding**                                                                    | **Decisive requirement**                                                                                                                                                                                                                                                                                                  |
|:------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------|:-------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ServiceNow                                                                                                                                | Lakeflow Connect                                                   | platform managed                                                               | First party LFC supported source. Full contract met declaratively.                                                                                                                                                                                                                                                        |
| GitHub                                                                                                                                    | <span acronym-label="sdk" acronym-form="singular+short">sdk</span> | PyGitHub                                                                       | Mature Python <span acronym-label="sdk" acronym-form="singular+short">sdk</span> covers <span acronym-label="rest" acronym-form="singular+short">rest</span> endpoints,                                                                                                                                                   |
| GitLab                                                                                                                                    | <span acronym-label="sdk" acronym-form="singular+short">sdk</span> | python-gitlab                                                                  | Project recognized Python client covers <span acronym-label="rest" acronym-form="singular+short">rest</span> with keyset pagination.                                                                                                                                                                                      |
| SonarQube                                                                                                                                 | dltool                                                             |                                                                                | No maintained Python <span acronym-label="sdk" acronym-form="singular+short">sdk</span>. <span acronym-label="rest" acronym-form="singular+short">rest</span> only access with offset pagination and                                                                                                                      |
| Semgrep                                                                                                                                   | Artifact path                                                      | <span acronym-label="cicd" acronym-form="singular+short">cicd</span> to Volume | <span acronym-label="cli" acronym-form="singular+short">cli</span> tool with no <span acronym-label="http" acronym-form="singular+short">http</span> <span acronym-label="api" acronym-form="singular+short">api</span>. Ingestion via <span acronym-label="cicd" acronym-form="singular+short">cicd</span> step pattern. |
| Dependency-Track                                                                                                                          | dltool                                                             | OpenAPI driven                                                                 | No first party <span acronym-label="sdk" acronym-form="singular+short">sdk</span>. <span acronym-label="rest" acronym-form="singular+short">rest</span> with offset pagination and                                                                                                                                        |
| TruffleHog                                                                                                                                | Artifact path                                                      | <span acronym-label="cicd" acronym-form="singular+short">cicd</span> to Volume | <span acronym-label="cli" acronym-form="singular+short">cli</span> tool with no server <span acronym-label="api" acronym-form="singular+short">api</span>. Ingestion via <span acronym-label="cicd" acronym-form="singular+short">cicd</span> step pattern.                                                               |
| <span acronym-label="owasp" acronym-form="singular+short">owasp</span> <span acronym-label="zap" acronym-form="singular+short">zap</span> | Artifact path                                                      | <span acronym-label="cicd" acronym-form="singular+short">cicd</span> to Volume | Scan report <span acronym-label="json" acronym-form="singular+short">json</span> produced in <span acronym-label="cicd" acronym-form="singular+short">cicd</span> and uploaded to Unity Catalog Volume.                                                                                                                   |
| <span acronym-label="aws" acronym-form="singular+short">aws</span> <span acronym-label="waf" acronym-form="singular+short">waf</span>     | <span acronym-label="sdk" acronym-form="singular+short">sdk</span> | boto3                                                                          | Two modes: log stream from Kinesis Data Firehose to S3 (preferred), boto3                                                                                                                                                                                                                                                 |

</div>

Across the nine sources, one resolves to Lakeflow Connect (ServiceNow),
three to an <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> (GitHub, GitLab,
<span acronym-label="aws" acronym-form="singular+short">aws</span>
<span acronym-label="waf" acronym-form="singular+short">waf</span>), two
to <span acronym-label="dltool"
acronym-form="singular+short">dltool</span> (SonarQube,
Dependency-Track), and three to the artifact path of
<a href="#sec:ingestion-patterns" data-reference-type="autoref"
data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>
(Semgrep, TruffleHog, <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> <span acronym-label="zap"
acronym-form="singular+short">zap</span>).

### Representative Connectors

Two connectors show the category range. ServiceNow represents the
Lakeflow Connect case, where <span class="mark">ingest.py</span> reduces
to a thin contract wrapper and the bundle fragment carries the ingestion
specification. GitHub represents the <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> case, where
<span class="mark">ingest.py</span> composes client calls into iterators
over bronze records.

#### ServiceNow: Lakeflow Connect Pipeline

The ServiceNow connector performs no live Python ingestion. The
<span class="mark">ingest.py</span> module carries a module docstring
pointing at the bundle fragment under
<span class="mark">src/connectors/servicenow/</span>
<span class="mark">resources/pipeline.yml</span> (reproduced in
<a href="#lst:servicenow-pipeline" data-reference-type="autoref"
data-reference="lst:servicenow-pipeline">[lst:servicenow-pipeline]</a>)
and a thin framework contract wrapper (
<span class="mark">ingest_contract</span> ) that validates the
credential set so a misconfigured bundle job fails fast. Lakeflow
Connect performs the actual <span acronym-label="http"
acronym-form="singular+short">http</span> ingestion against ServiceNow.
Authentication is carried by a Databricks Connection declared in the
same folder under <span class="mark">resources/connection.yml</span> and
referenced by name. The <span class="mark">objects</span> block
enumerates the two <span acronym-label="cmdb"
acronym-form="singular+short">cmdb</span> tables the silver layer
consumes and their destination tables in bronze. The
<span class="mark">cmdb_ci_business_app</span> table supplies
application records, and <span class="mark">cmdb_rel_ci</span> supplies
the relationship edges used by the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> app repository mapping path.
Fuller production inventories would add explicit repository link fields
or additional relationship classes. Schedule and target catalog come
from bundle variables so the same fragment can promote across dev,
staging, and prod.

``` yaml
resources:
  pipelines:
    servicenow_ingest:
      name: servicenow_ingest
      catalog: ${var.catalog}
      target: bronze_servicenow
      continuous: false
      schedule:
        quartz_cron_expression: "0 0 * * * ?"
        timezone_id: UTC
      ingestion_definition:
        connection_name: servicenow
        objects:
          - table:
              source_schema: default
              source_table: cmdb_ci_business_app
              destination_catalog: ${var.catalog}
              destination_schema: bronze_servicenow
              destination_table: business_applications
          - table:
              source_schema: default
              source_table: cmdb_rel_ci
              destination_catalog: ${var.catalog}
              destination_schema: bronze_servicenow
              destination_table: app_cis
```

The framework prescribed connector layout is preserved.
<span class="mark">mapping.yml</span> ,
<span class="mark">config.yml</span> ,
<span class="mark">severity.yml</span> ,
<span class="mark">status.yml</span> , and
<span class="mark">transform.py</span> continue to govern the
transformation from bronze to silver. Only
<span class="mark">ingest.py</span> changes form, from a Python module
to a declaration embedded in the bundle. That is the trade the Lakeflow
Connect category offers: no pagination, authentication, or retry code
written by hand, in exchange for binding the connector to a platform
maintained capability.

#### GitHub: PyGitHub SDK Module

The GitHub connector uses PyGitHub. The
<span class="mark">ingest.py</span> module exposes three names: a
<span class="mark">build_github_client</span> factory, an
<span class="mark">ingest_contract</span> framework wrapper that
demonstrates the documented traversal, and a
<span class="mark">verify_webhook_signature</span> HMAC helper that
handles webhook receipt outside SDK territory. The traversal calls
<span class="mark">client.get_organization(org).get_repos()</span> and
receives a <span class="mark">PaginatedList</span> of
<span class="mark">Repository</span> instances. Each repository then
exposes <span class="mark">repo.get_pulls(state, since=hwm_value)</span>
and <span class="mark">repo.get_codescan_alerts()</span> for walking the
finding streams.
<a href="#lst:github-ingest" data-reference-type="autoref"
data-reference="lst:github-ingest">[lst:github-ingest]</a> reproduces
the client factory as the representative fragment.

``` python
from github import Auth, Github, GithubRetry


def build_github_client(token: str) -> Github:
    """Authenticated Github client with retry tuned for
    secondary rate limits."""
    auth = Auth.Token(token)
    retry = GithubRetry(
        total=10, backoff_factor=2.0, secondary_rate_wait=60
    )
    return Github(auth=auth, retry=retry, per_page=100)
```

PyGitHub absorbs the cross cutting concerns of authentication,
pagination, and retry. <span class="mark">GithubRetry</span> , a
<span class="mark">urllib3.Retry</span> subclass shipped with the
library, recognizes GitHub’s secondary rate limit signal that arrives as
<span acronym-label="http" acronym-form="singular+short">http</span> 403
with a <span class="mark">Retry-After</span> header. A plain
<span class="mark">Retry(status_forcelist=\[429, 5xx\])</span> does not
cover that path. The incremental state contract from the framework
(REQ-ING-HWM) maps onto a built in PyGitHub mechanism: resource
accessors such as
<span class="mark">Repository.get_pulls(state="closed",
since=hwm_value)</span> accept a <span class="mark">since</span>
parameter, so high water mark filtering pushes down to the
<span acronym-label="api" acronym-form="singular+short">api</span> call
instead of running client side. The page size is set to PyGitHub’s
documented maximum of 100 to minimize round trips.

The tests under <span class="mark">src/connectors/github/tests/</span>
fake PyGitHub at the object graph level rather than at the
<span acronym-label="http" acronym-form="singular+short">http</span>
level. A test fixture builds <span class="mark">MagicMock</span>
instances modeled on PyGitHub’s <span class="mark">Github</span> ,
<span class="mark">Organization</span> ,
<span class="mark">Repository</span> , and
<span class="mark">PaginatedList</span> classes, each exposing the
attributes the production code calls. The contract under test is the
composition of <span acronym-label="sdk"
acronym-form="singular+short">sdk</span> calls in the connector, not the
<span acronym-label="http" acronym-form="singular+short">http</span>
behavior of the library.

### Aggregate Results

All nine sources have a connector folder under
<span class="mark">src/connectors/\<source\>/</span> . Each folder
contains configuration, ingest and transform modules, mappings, severity
and status lookups, bundle resources, secret loading scripts, source
runtime where applicable, and colocated tests.

Evidence is recorded at two levels. Each source page on the
documentation site contains an Implementation log and a Validation table
keyed by requirement IDs that map to
<span class="mark">@pytest.mark.requirement</span> markers. The
[catalog](https://vkraus.github.io/appsec-mvp/platform/reference/catalog/)
combines those rows into one requirement by source view with PASS or N/A
cells. The ten requirement identifiers (
<span class="mark">REQ-ING-AUTH</span> ,
<span class="mark">REQ-ING-PAG</span> ,
<span class="mark">REQ-ING-RL</span> ,
<span class="mark">REQ-ING-HWM</span> ,
<span class="mark">REQ-TRF-MAP</span> ,
<span class="mark">REQ-TRF-SEV</span> ,
<span class="mark">REQ-TRF-STS</span> ,
<span class="mark">REQ-TRF-TS</span> , <span class="mark">REQ-DQ</span>
, <span class="mark">REQ-DEDUP</span> ) structure the matrix and form
the evidence trail behind the <span acronym-label="ai"
acronym-form="singular+short">ai</span> claim defended in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>.

<a href="#tab:impl-evidence-levels" data-reference-type="autoref"
data-reference="tab:impl-evidence-levels">[tab:impl-evidence-levels]</a>
separates the artifact claim from runtime evidence. A "working
connector" has several levels in the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span>: generated module present,
requirement bound tests present, live source exercised, and Spark
transform wired to write Silver rows.

<div class="center">

\[Implementation evidence levels by source\]Implementation evidence
levels by source. All rows include the generated connector folder,
mapping/configuration artifacts, bundle resources, source runtime where
applicable, and requirement bound tests.
<span id="tab:impl-evidence-levels"
label="tab:impl-evidence-levels"></span>

| **Source**                                                                                                                                | **Delivered evidence**                                                                                                                                | **Boundary to keep explicit**                                                                                                         |
|:------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| ServiceNow                                                                                                                                | Lakeflow Connect bundle pipeline, contract wrapper, CMDB row helpers, application and app repository mapping tests, live developer instance exercise. | Spark wrapper for the full Silver application frame still returns an empty frame with the target schema while row helpers are tested. |
| GitHub                                                                                                                                    | PyGitHub ingest contract, repository and alert row helpers, severity/status/dedup tests, live GitHub exercise.                                        | Repository population is partial, and the finding Spark wrapper still needs full wiring.                                              |
| GitLab                                                                                                                                    | python-gitlab module layout, mapping files, bundle resources, tests at row level.                                                                     | Evidence is backed only by fixtures. Live tenant exercise and wrapper completion remain future work.                                  |
| SonarQube                                                                                                                                 | REST/dltool category artifacts, ingestion tests, Spark transform that writes rows to                                                                  | Live deployment evidence is specific to this source, not evidence for every dltool source.                                            |
| Semgrep                                                                                                                                   | Artifact ingestion path, mapping and transform tests at row level, CI artifact exercise.                                                              | Spark wrapper completion remains future work.                                                                                         |
| Dependency-Track                                                                                                                          | OpenAPI/dltool artifacts, pagination and mapping tests, source runtime.                                                                               | The live dltool primitive is deferred. Evidence is backed by fixtures.                                                                |
| TruffleHog                                                                                                                                | Artifact ingestion path, mapping helpers, severity/status tests, source runtime.                                                                      | Evidence is backed only by fixtures. Spark wrapper completion remains future work.                                                    |
| <span acronym-label="owasp" acronym-form="singular+short">owasp</span> <span acronym-label="zap" acronym-form="singular+short">zap</span> | Artifact and daemon ingestion paths, Spark transform that writes rows to                                                                              | Application attribution still depends on repository/deployment mapping being populated.                                               |
| <span acronym-label="aws" acronym-form="singular+short">aws</span> <span acronym-label="waf" acronym-form="singular+short">waf</span>     | Preferred log stream path, boto3 fallback contract, event normalization helpers, source runtime.                                                      | Live tenant exercise and the boto3 sampled request fallback remain deferred. Spark wrapper completion remains future work.            |

</div>

<a href="#tab:connector-evidence-matrix" data-reference-type="autoref"
data-reference="tab:connector-evidence-matrix">[tab:connector-evidence-matrix]</a>
gives the same evidence as a scan matrix. It separates test type, live
source exercise, bundle resources, row level mapping evidence, and Spark
wrapper completion.

<div class="center">

\[Connector evidence matrix\]Connector evidence matrix. Every row has a
requirement matrix on the documentation site with PASS or N/A cells.
“Rows” means the Spark wrapper emits non empty Silver rows. “Schema”
means it returns the target schema while row helpers are tested.
<span id="tab:connector-evidence-matrix"
label="tab:connector-evidence-matrix"></span>

| **Source**                                                                                                                                | **Tests** | **Live** | **Bundle** | **Rows** | **Spark** | **Boundary**                                          |
|:------------------------------------------------------------------------------------------------------------------------------------------|:---------:|:--------:|:----------:|:--------:|:---------:|:------------------------------------------------------|
| ServiceNow                                                                                                                                |    Yes    |   Yes    |    Yes     |   Yes    |  Schema   | Full Silver application frame pending.                |
| GitHub                                                                                                                                    |    Yes    |   Yes    |    Yes     |   Yes    |  Partial  | Repository rows are partial. Finding wrapper pending. |
| GitLab                                                                                                                                    |    Yes    |    No    |    Yes     |   Yes    |  Schema   | Fixture backed only.                                  |
| SonarQube                                                                                                                                 |    Yes    |   Yes    |    Yes     |   Yes    |   Rows    | Live evidence is source specific.                     |
| Semgrep                                                                                                                                   |    Yes    |   Yes    |    Yes     |   Yes    |  Schema   | Artifact path exercised. Wrapper pending.             |
| Dependency-Track                                                                                                                          |    Yes    |    No    |    Yes     |   Yes    |  Schema   | Live dltool primitive deferred.                       |
| TruffleHog                                                                                                                                |    Yes    |    No    |    Yes     |   Yes    |  Schema   | Fixture backed only.                                  |
| <span acronym-label="owasp" acronym-form="singular+short">owasp</span> <span acronym-label="zap" acronym-form="singular+short">zap</span> |    Yes    |   Yes    |    Yes     |   Yes    |   Rows    | Attribution depends on deployment mapping.            |
| <span acronym-label="aws" acronym-form="singular+short">aws</span> <span acronym-label="waf" acronym-form="singular+short">waf</span>     |    Yes    |    No    |    Yes     |   Yes    |  Schema   | Live tenant and sampled fallback deferred.            |

</div>

<a href="#tab:platform-analytics-evidence-matrix"
data-reference-type="autoref"
data-reference="tab:platform-analytics-evidence-matrix">[tab:platform-analytics-evidence-matrix]</a>
separates platform and analytics evidence from connector evidence. These
artifacts support the thesis demonstration but are not claimed as a
production deployment.

<div class="center">

\[Platform and analytics evidence matrix\]Platform and analytics
evidence matrix. <span id="tab:platform-analytics-evidence-matrix"
label="tab:platform-analytics-evidence-matrix"></span>

| **Artifact**        | **Test evidence**                                                   | **Live/deployed** | **Boundary**                                              |
|:--------------------|:--------------------------------------------------------------------|:-----------------:|:----------------------------------------------------------|
| Silver DDL contract | Schema and DDL contract tests for the realized Silver subset.       |        No         | Single source of truth remains future work.               |
|                     | Platform linker tests over application code matching.               |        No         | CMDB relationship and explicit link column paths pending. |
| Gold datasets       | Tests cover pure Python helpers and Spark write paths where marked. |        No         | Fixture backed thesis evidence.                           |
| Gold view           | View declaration and mocked application query tests.                |        No         | Production query workload not measured.                   |
| Online Tables       | Bundle resources for two serving tables.                            |        No         | No production serving latency claim.                      |
| Databricks App      | App resource and mocked lookup/policy checks.                       |        No         | Demonstrates interface pattern, not production service.   |
| Suppression rules   | Suppression logic tests.                                            |        No         | Operational approval workflow pending.                    |

</div>

The platform layer is ahead of the original four table demonstration. It
declares and tests the core Silver subset
<span class="mark">findings</span> ,
<span class="mark">finding_location</span> ,
<span class="mark">hwm</span> , <span class="mark">repositories</span> ,
<span class="mark">applications</span> ,
<span class="mark">app_repo_mapping</span> , and
<span class="mark">suppression_rules</span> . It also ships one
implemented application attribution path: a platform linker that
populates <span class="mark">silver.app_repo_mapping</span> by matching
application codes embedded in repository names to the application
inventory. CMDB relationship traversal, explicit repository link
columns, and fuller connector side repository writers remain incomplete,
so this is evidence for one attribution path rather than the full
attribution story. The <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> exercises the
<span class="mark">deterministic_code_match</span> state from
<a href="#tab:attribution-state-model" data-reference-type="autoref"
data-reference="tab:attribution-state-model">[tab:attribution-state-model]</a>.
The remaining states describe framework behavior that is not yet
demonstrated by separate implementation paths.

The analytics layer is implemented as evidence for the thesis rather
than as a production service. It includes five Gold datasets (
<span class="mark">app_risk_posture_daily</span> ,
<span class="mark">mttr_by_source_severity_weekly</span> ,
<span class="mark">coverage_matrix</span> ,
<span class="mark">dedup_link_overlap</span> , and
<span class="mark">cwe_owasp_heatmap</span> ), one Gold view (
<span class="mark">app_repo_findings_open</span> ), two Online Table
resources, suppression rules, and a Databricks App exposing score lookup
and policy checks before commit. Tests cover pure Python aggregation
helpers, Spark write paths where marked, suppression logic, and mocked
application queries. The thesis does not claim production deployment,
production latency, or model training evidence.

At commit <span class="mark">e58bb7c</span> the source tree contains 38
<span class="mark">test\_\*.py</span> files and 413 test functions under
<span class="mark">src/connectors/</span> ,
<span class="mark">src/platform/</span> , and
<span class="mark">src/analytics/</span> . The count includes tests that
require live systems and N/A marker tests. The Limitations section
states which paths are backed by fixtures or deferred.

### Discussion

#### Contract of three categories

Every source in the sample resolved to one of the three connector
categories or to the artifact ingestion pattern of
<a href="#sec:ingestion-patterns" data-reference-type="autoref"
data-reference="sec:ingestion-patterns">[sec:ingestion-patterns]</a>. No
source required another connector category. The Lakeflow Connect and
<span acronym-label="sdk" acronym-form="singular+short">sdk</span> cases
produce visibly different layouts: ServiceNow has no Python ingestion
file of substance, while GitHub has a small flat
<span class="mark">ingest.py</span> composed of
<span acronym-label="sdk" acronym-form="singular+short">sdk</span>
calls. Both preserve the module layout prescribed by the framework, with
platform lock in on one side and per source client knowledge on the
other.

#### Declarative mapping

Connectors share severity and status normalization helpers in
<span class="mark">src/platform/silver.py</span> and keep lookup tables
as YAML alongside the connector code. The
<span class="mark">mapping.yml</span> files document the intended
derivation for every source. In the current <span acronym-label="mvp"
acronym-form="singular+short">mvp</span>, the mapping is applied by
Python helpers and Spark code for each source rather than by a generic
declarative applicator. SonarQube and <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> <span acronym-label="zap"
acronym-form="singular+short">zap</span> demonstrate Spark transforms
that write rows to <span class="mark">silver.findings</span> . Several
other connectors still expose Spark wrappers that return only the target
schema while their mapping helpers at row level are tested. Aligning the
<span acronym-label="mvp" acronym-form="singular+short">mvp</span> with
the declarative mapping prescription of
<a href="#sec:transformation-patterns" data-reference-type="autoref"
data-reference="sec:transformation-patterns">[sec:transformation-patterns]</a>
is a <a href="#sec:future-work" data-reference-type="autoref"
data-reference="sec:future-work">[sec:future-work]</a> thread.

#### Iteration Summary

Review caught the iterations below. Each one is classified against the
acceptance criterion in
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a>: **framework gap** (a
specification extension would have prevented the issue and would
generalize), **source specific issue** (not generalizable beyond one
source), or **environment setup** (setup or infrastructure outside
framework scope). Earlier iterations before the structural redesign
exposed three framework gaps: a hand written shared
<span acronym-label="http" acronym-form="singular+short">http</span>
primitive that introduced an unsanctioned fourth ingestion category, a
missing boundary validator on incremental state inputs, and a
misconfigured retry policy on the GitHub client. The redesign closed all
three by enforcing the layering rule of
<a href="#sec:impl-layering-rule" data-reference-type="autoref"
data-reference="sec:impl-layering-rule">[sec:impl-layering-rule]</a> and
by binding the connector contract to the colocated test suite. The
findings below are from the reviewer cycle after the redesign.

- **Layering boundary that the redesign closed.** The layout before the
  redesign mixed top level <span class="mark">tests/</span> ,
  <span class="mark">config/</span> ,
  <span class="mark">resources/</span> , <span class="mark">sql/</span>
  , and <span class="mark">infra/terraform/</span> folders, and the
  platform layer predeclared resources for specific connectors. This
  permitted exactly the failure mode that the unsanctioned fourth
  ingestion category had exposed. The redesign moved every component to
  its own folder, deleted the predeclared resources from the platform
  layer, and stated the layering rule explicitly. **Framework gap.** The
  framework now states three install layers with no upward or sideways
  setup code dependencies, and the data level <span acronym-label="scm"
  acronym-form="singular+short">scm</span> first ordering is recorded
  separately as a job time constraint.

- **Schema drift between <span acronym-label="sql"
  acronym-form="singular+short">sql</span> <span acronym-label="ddl"
  acronym-form="singular+short">ddl</span> and PySpark types.**
  Splitting the <span class="mark">sql/</span> tree into per layer
  ownership exposed inconsistencies between the
  <span acronym-label="ddl" acronym-form="singular+short">ddl</span> for
  the silver tables and the <span class="mark">StructType</span>
  definitions in <span class="mark">src/platform/schemas.py</span> . The
  reviewer flagged the drift, and the implementation now includes
  schema/DDL contract tests for the realized Silver subset. Connector
  side writers for <span class="mark">silver.repositories</span> remain
  partial, and <span class="mark">silver.app_repo_mapping</span> is
  populated by the platform name and application code linker rather than
  by every source side relationship path. **Framework gap.** The
  framework should hold a single source of truth for silver schemas.
  <a href="#sec:future-work" data-reference-type="autoref"
  data-reference="sec:future-work">[sec:future-work]</a> carries the
  consolidation as a thread.

- **Secret scope mismatch in the GitHub ingest entry.** The post deploy
  bootstrap script defines a secret scope named
  <span class="mark">mvp-connectors</span> . The GitHub ingest entry
  point read from a scope named <span class="mark">appsec</span> , a
  residue from an earlier prototype. The reviewer caught the mismatch
  during the bootstrap script review. **Environment setup.** The fix
  aligned the entry point with the documented scope name.

- **Worktree pollution.** Several review cycles caught files that the
  redesign deleted reappearing on disk and being staged for inadvertent
  reintroduction (likely an editor or antivirus recreating them).
  Reviewers caught the pattern before bad commits landed. **Environment
  setup.** The pattern is not attributable to the framework.

- **Cron schedule collision between GitHub and SonarQube.** The GitHub
  and SonarQube connector jobs were originally scheduled with
  overlapping quartz cron expressions, so both jobs would dispatch on
  the same minute mark and contend for the shared cluster. The reviewer
  flagged the collision and the SonarQube schedule was offset to a non
  aligned minute. **Source specific issue.** The correction is specific
  to two job schedules and does not generalize.

- **IRSA OIDC trust policy gaps.** Migrating each connector Terraform
  runtime under
  <span class="mark">src/connectors/\<source\>/runtime/</span> exposed
  incomplete trust policy details on the IAM Roles for Service Accounts
  (IRSA) bindings. The reviewer required full trust policy declarations
  and explicit framework user inputs for OIDC issuer URLs. **Environment
  setup.** The corrections concern <span acronym-label="aws"
  acronym-form="singular+short">aws</span> account setup and are
  documented per connector under the
  <span class="mark">runtime/README.md</span> file.

Two of the six findings after the redesign classify as framework gaps.
Both name a specific consolidation the framework should hold (the
layering rule, a single source of truth for silver schemas). Three
classify as environment setup and one as a source specific issue. The
reviewer cycle caught all six before the commits landed, which is the
empirical evidence behind the claim that the skill chain plus reviewer
pattern catches named defect classes.
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> lifts these findings to a
defended claim about where the framework holds and where it admits
further specification.

## Conclusion

### Thesis Outcomes and Contributions

This thesis delivers the three contributions announced in the abstract.
The first is a **requirements specification** for an application
security data platform, grounded in
<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a>. The full specification
is published on the documentation site and attached as
`appsec-mvp-docs.zip`, because it is too long for an appendix. The
second is a **reusable and extensible framework**
(<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a>) covering reference
architecture, data model, and the medallion based pipeline  from source
records to consumption. The third is a **Databricks MVP reference
implementation**
(<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>) with
generated connector modules for nine selected data sources, explicit
evidence levels in
<a href="#sec:impl-results" data-reference-type="autoref"
data-reference="sec:impl-results">[sec:impl-results]</a>, and the
implementation archive attached as `appsec-mvp.zip`.

In design science terms, the framework is the artifact .
<a href="#ch:analysis" data-reference-type="autoref"
data-reference="ch:analysis">[ch:analysis]</a> establishes problem
relevance, and
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> demonstrates
the artifact through the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span>. Evaluation comes from
requirement linked tests, the traceability matrix, and the
<span acronym-label="ai" acronym-form="singular+short">ai</span>
instantiability assessment. Two limits remain: the
<span acronym-label="ai" acronym-form="singular+short">ai</span>
evaluation criterion was finalized after early reviewer cycles, and
design alternatives are recorded only in the iteration summary.

The framework is **reusable** because
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> introduced no
new connector level design decisions beyond which sources to onboard. It
is **extensible** because onboarding a new source reduces to the five
step procedure of
<a href="#sec:impl-methodology" data-reference-type="autoref"
data-reference="sec:impl-methodology">[sec:impl-methodology]</a>:
category resolution, module instantiation, mapping specification,
layered testing, and skill chain pass with reviewer supervision.
ServiceNow on Lakeflow Connect and GitHub on PyGitHub are concrete
examples of the same contract supporting different integration patterns.

### Evaluation of AI Instantiability

<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> aimed the framework
outputs at an <span acronym-label="ai"
acronym-form="singular+short">ai</span> coding agent. The original
target was fully autonomous generation from the agent [skill
catalog](https://vkraus.github.io/appsec-mvp/connectors/scm/skills/).
The <span acronym-label="mvp" acronym-form="singular+short">mvp</span>
was produced by invocations of that catalog under reviewer subagent
supervision (Subagent-Driven Development).

#### Acceptance criterion

A correction counts as a **framework gap** when extending the
specification (schema pattern, connector contract from
<a href="#sec:connector-contract" data-reference-type="autoref"
data-reference="sec:connector-contract">[sec:connector-contract]</a>, or
declarative artifact) would have produced the right output on first pass
and the extension would generalize. Corrections tracing to **source
specific issues** or **environment setup** (setup, authentication,
infrastructure) do not count against the framework.

#### Empirical outcome

The four-skill chain ran across all nine source specifications,
producing connector modules for each source and validation evidence.
<a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a>
enumerates the defects the reviewer cycle caught: a layering boundary
(framework gap), schema drift between <span acronym-label="sql"
acronym-form="singular+short">sql</span> <span acronym-label="ddl"
acronym-form="singular+short">ddl</span> and PySpark types (framework
gap), a secret scope mismatch (environment setup), worktree pollution
(environment setup), a cron schedule collision (source specific issue),
and IRSA OIDC trust policy gaps (environment setup). Two of six classify
as framework gaps. Evidence lives in the [documentation
site](https://vkraus.github.io/appsec-mvp/).

#### Claim defended

The defended claim is limited to supervised connector generation. The
skill catalog produced connector artifacts for nine sources, and
reviewer subagents caught the defect classes listed in
<a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a>.
<a href="#sec:impl-results" data-reference-type="autoref"
data-reference="sec:impl-results">[sec:impl-results]</a> separates
generated artifacts, live source exercise, and Spark wrapper
completeness.

This does not prove autonomous generation. The platform layer and
analytics layer were hand written. The evidence comes from one framework
user, the author, acting as both implementer and reviewer of the
evaluation, without inter rater reliability or an independent grader. A
controlled study with multiple framework users would be needed to
measure autonomy. The open schema drift gap and the remaining
implementation items also have to be closed before a stronger autonomy
claim can be made.

### Limitations

The <span acronym-label="mvp" acronym-form="singular+short">mvp</span>
is a working reference rather than a production ready integration. It is
**platform specific**: it runs on Databricks over
<span acronym-label="aws" acronym-form="singular+short">aws</span>
object storage, the only combination exercised end to end. **Live tenant
exercise** is partial: of the nine connectors, ServiceNow, GitHub,
SonarQube, Semgrep, and <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> <span acronym-label="zap"
acronym-form="singular+short">zap</span> have been exercised against
live source systems during the construction of this thesis. The
remaining four (GitLab, Dependency-Track, TruffleHog,
<span acronym-label="aws" acronym-form="singular+short">aws</span>
<span acronym-label="waf" acronym-form="singular+short">waf</span>) pass
their unit tests against fixtures but have not been exercised against a
live tenant. The connector contract in
<a href="#sec:connector-framework" data-reference-type="autoref"
data-reference="sec:connector-framework">[sec:connector-framework]</a>
is written to be cloud and platform agnostic in principle, but it has
not been ported to Snowflake, Microsoft Fabric, or an on premises
platform, so the portability claim rests on contract design alone, with
no second demonstrated implementation.

**Reproducibility** requires a Databricks workspace with Unity Catalog,
an <span acronym-label="aws" acronym-form="singular+short">aws</span>
account with an S3 bucket and federated credentials, a Lakeflow Connect
entitlement, a ServiceNow developer instance, and a GitHub Personal
Access Token (<span acronym-label="pat"
acronym-form="singular+short">pat</span>). The Declarative Automation
Bundle, formerly Databricks Asset Bundle , deploys every workspace
resource the bundle format covers natively. The post deploy shell script
<span class="mark">src/platform/scripts/bootstrap.sh</span> creates the
secret scope container, Unity Catalog storage credential, and Unity
Catalog external location. Per connector Terraform modules under
<span class="mark">src/connectors/\<source\>/runtime/</span> provision
source side cloud infrastructure. The archives attached to this thesis,
<span class="mark">appsec-mvp.zip</span> and
<span class="mark">appsec-mvp-docs.zip</span> , cannot reproduce the
build without these entitlements.

Several **open implementation items** remain, but they are narrower than
the framework gaps before the redesign summarized in
<a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a>.
Connector population of <span class="mark">silver.repositories</span> is
partial: GitHub writes the standard narrow repository fields, while
wider target fields and GitLab parity remain future work. Application
attribution has one implemented path, not the full CMDB relationship
story. <span class="mark">silver.app_repo_mapping</span> is populated by
a platform linker over <span class="mark">silver.applications</span> and
<span class="mark">silver.repositories</span> , using application codes
embedded in repository names. Parallel CMDB relationship paths through
<span class="mark">cmdb_rel_ci</span> , explicit repository link
columns, and fuller connector side repository writers remain pending.
Several Spark connector wrappers currently return empty Silver
DataFrames with target schemas while their mapping helpers at row level
are tested. SonarQube and <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> <span acronym-label="zap"
acronym-form="singular+short">zap</span> have Spark transforms that emit
rows. Some notebook entry wrappers generated by skills remain
placeholders. Dependency-Track live dltool execution and the
<span acronym-label="aws" acronym-form="singular+short">aws</span>
<span acronym-label="waf" acronym-form="singular+short">waf</span> boto3
sampled request fallback remain deferred, while the WAF log stream path
is the preferred design. Inherited error handling sharp edges remain in
<span class="mark">bootstrap.sh</span> and the ServiceNow Terraform
runtime, both flagged for hardening.

The analytics and serving layer is implemented as evidence for the
thesis rather than a production service. It includes five Gold datasets,
one Gold view, two Online Table resources, suppression rules, and a
Databricks App. The tests are backed by fixtures, mocked, or marked for
Spark/live execution as appropriate. The thesis does not claim
production deployment, measured serving latency, or trained
<span acronym-label="ml" acronym-form="singular+short">ml</span> models.

The **variation** of the selected sources is biased toward
<span acronym-label="rest" acronym-form="singular+short">rest</span>
<span acronym-label="json" acronym-form="singular+short">json</span>
<span acronym-label="api" acronym-form="plural+short">apis</span> with
token authentication (five of the nine: GitHub, GitLab, ServiceNow,
SonarQube, Dependency-Track). <span acronym-label="aws"
acronym-form="singular+short">aws</span> <span acronym-label="waf"
acronym-form="singular+short">waf</span> consumes a log stream from
Kinesis Data Firehose to S3 with SigV4 service credentials rather than a
bearer token, <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> <span acronym-label="zap"
acronym-form="singular+short">zap</span> follows an artifact pattern,
and the two file based sources (Semgrep, TruffleHog) deliver via S3
instead of an interactive <span acronym-label="api"
acronym-form="singular+short">api</span>. Source categories not
demonstrated include SOAP, gRPC, syslog, Kafka event streams, binary
telemetry, and push only webhook native sources. The contract is written
to accommodate these, but evidence is absent on a category by category
basis.

### Future Work

#### Implementation backlog

**Closing the remaining framework gap.** The layering boundary gap was
closed by the structural redesign. The schema drift gap remains open. A
single source of truth for silver schemas resolving the drift between
<span acronym-label="sql" acronym-form="singular+short">sql</span>
<span acronym-label="ddl" acronym-form="singular+short">ddl</span> and
PySpark <span class="mark">StructType</span> definitions is the
precondition for any stronger <span acronym-label="ai"
acronym-form="singular+short">ai</span> autonomy claim.

**Completing the declarative mapping applicator and Spark wrapper
wiring.**
<a href="#sec:transformation-patterns" data-reference-type="autoref"
data-reference="sec:transformation-patterns">[sec:transformation-patterns]</a>
treats <span class="mark">mapping.yml</span> as the authoritative
specification consumed by a generic applicator, but the
<span acronym-label="mvp" acronym-form="singular+short">mvp</span>
applies mappings through Python helpers and Spark code for each source.
Completing the applicator and replacing the remaining wrappers with
Spark transforms that emit rows would move new source onboarding closer
to configuration than code.

**Realizing the remaining prescribed silver tables.** The framework
prescribes 15 silver tables
(<a href="#sec:entity-model" data-reference-type="autoref"
data-reference="sec:entity-model">[sec:entity-model]</a>). The
<span acronym-label="mvp" acronym-form="singular+short">mvp</span>
realizes the core subset <span class="mark">applications</span> ,
<span class="mark">repositories</span> ,
<span class="mark">findings</span> ,
<span class="mark">finding_location</span> ,
<span class="mark">hwm</span> ,
<span class="mark">app_repo_mapping</span> , and
<span class="mark">suppression_rules</span> . Future iterations should
add the remaining entity tables ( <span class="mark">teams</span> ,
<span class="mark">commits</span> ,
<span class="mark">pull_requests</span> ,
<span class="mark">pipeline_runs</span> ,
<span class="mark">dependencies</span> ,
<span class="mark">branch_policies</span> ), the reference tables (
<span class="mark">vulnerabilities</span> from the
<span acronym-label="nvd" acronym-form="singular+short">nvd</span>,
<span class="mark">epss_scores</span> ,
<span class="mark">kev_entries</span> ), and the remaining relationship
table <span class="mark">finding_cve_mapping</span> . Cross tool overlap
is currently computed in Gold rather than stored in a separate
<span class="mark">dedup_links</span> table. Adding a persisted dedup
relationship remains a future extension.

**Finishing job orchestration and bootstrap hardening.** Some notebook
wrappers generated by skills still need full job orchestration, and the
remaining Spark wrappers need implementation. The bootstrap script and
ServiceNow runtime need the hardening pass named in Limitations.

**Live analytics evidence and downstream triage.** The rule based Gold
layer and Databricks App now exist, so the next step is to run them
against live data from multiple sources, measure serving latency, and
connect them to downstream triage workflows.

#### Research extensions

**Replication of <span acronym-label="ai"
acronym-form="singular+short">ai</span> instantiability.** The
evaluation in this thesis used one framework user, the author, and
reviewer subagent cycles. A controlled study with several framework
users, a fixed source onboarding task, and independent grading would
measure how well the skill chain transfers beyond the author and how far
the framework remains from autonomous connector generation.

**Large Language Model assisted triage and correlation.** The Gold layer
provides application risk posture, overlap, coverage, and remediation
metrics. Large Language Model assisted triage and correlation over these
tables is a natural extension and would exercise the data model of
<a href="#sec:data-model" data-reference-type="autoref"
data-reference="sec:data-model">[sec:data-model]</a> in the direction it
was designed for.

# Appendices

## Generative AI Use Disclosure

This appendix expands the Declaration on the Use of Artificial
Intelligence from the front matter of this thesis. The five sections
below disclose each use in the same order as the front matter
declaration. The central use is the <span acronym-label="ai"
acronym-form="singular+short">ai</span> assisted construction of the
reference implementation
(<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a>), which is
evaluated in <a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> rather than treated as
incidental assistance.

The grammar and language style assistance described in the first section
below used the Overleaf <span acronym-label="ai"
acronym-form="singular+short">ai</span> assistant on the thesis
manuscript . All other <span acronym-label="ai"
acronym-form="singular+short">ai</span> assistance reported in this
appendix used Claude models (Anthropic) accessed through the Claude Code
<span acronym-label="cli" acronym-form="singular+short">cli</span> ,
with model versions spanning Claude Opus 4.5 through Claude Opus 4.7
over the drafting period of the thesis .

### Text Editing

<span acronym-label="ai" acronym-form="singular+short">ai</span>
assistance feature in Overleaf online editor was used for grammar
checking, style refinement, synonym replacement, sentence rephrasing,
and other editing of the content I originally authored . I relied on the
assistant throughout my drafts to identify errors, tighten phrasing, and
highlight inconsistencies. I accepted, rejected, or revised the
suggestions. I did not rely on any <span acronym-label="ai"
acronym-form="singular+short">ai</span> assistant to autonomously
generate thesis content. I wrote all new text material in the Overleaf
editor, and only afterward revised it with <span acronym-label="ai"
acronym-form="singular+short">ai</span> support.

Several review cycles were carried out across the entire thesis using
the Claude Code tool with Claude Opus models to condense it to its
target length . These iterations rephrased longer passages into more
concise wording and relocated some details into the attached
<span acronym-label="mvp" acronym-form="singular+short">mvp</span>
documentation, which contains the requirements specification and
reference material per data source. The restructuring decisions were
mine. The <span acronym-label="ai"
acronym-form="singular+short">ai</span> assistant proposed cuts and
rephrasing that I accepted, rejected, or revised.

The research question, chapter structure, major contributions, and
central claims are all mine. Positioning against prior work
(<a href="#sec:related-work" data-reference-type="autoref"
data-reference="sec:related-work">[sec:related-work]</a>) and the
conceptual domain model
(<a href="#sec:data-entities" data-reference-type="autoref"
data-reference="sec:data-entities">[sec:data-entities]</a>) were also
authored by me. Literature selection is mine, Claude Code was used to
generate most bibliography entries in LaTeX format . Several entries
point at vendor product pages and white papers (used as primary sources
for product capabilities and feature claims) instead of peer reviewed
literature. These are flagged inline with the specific claim each one
supports.

### Images

<span acronym-label="ai" acronym-form="singular+short">ai</span>
assistance was used to generate TikZ source for figures from my sketches
and textual descriptions of the content and layout. I reviewed and
revised the figures for correctness and readability.

### Source Code (`appsec-mvp.zip`)

The reference implementation in
<a href="#ch:implementation" data-reference-type="autoref"
data-reference="ch:implementation">[ch:implementation]</a> (attached to
this thesis as `appsec-mvp.zip`) was built across three distinct
<span acronym-label="ai" acronym-form="singular+short">ai</span>
assisted workflows, all using Claude Code with Anthropic Claude Opus
models .

The first workflow predates the public `appsec-mvp` repository. Four
connectors (ServiceNow, GitHub, Semgrep, <span acronym-label="owasp"
acronym-form="singular+short">owasp</span> <span acronym-label="zap"
acronym-form="singular+short">zap</span>) were manually coded by me
during the analysis phase, with Claude Code used conversationally for
boilerplate and refactoring , and committed as the initial repository
snapshot. They have since been re-emitted by the skill chain. The
current connector modules in the repository are output of the chain for
all nine connectors, with the evidence levels and remaining wrapper gaps
stated in <a href="#sec:impl-results" data-reference-type="autoref"
data-reference="sec:impl-results">[sec:impl-results]</a>.

The second workflow was the connector skill chain published in the
documentation site (MVP Documentation section below). It ran across all
nine selected source specifications, producing the connector artifact
set for each source and validation evidence. Each pass wrote evidence
rows to the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> documentation (an
Implementation log entry and a Validation table keyed by requirement
IDs).

The third workflow was the structural redesign that centered the
implementation on Databricks, run on a separate branch and merged
through pull request \#2. It applied the Subagent-Driven Development
pattern from the Superpowers plugin for Claude Code (brainstorm, then
spec, then plan, then execute) using artifacts under
`docs/superpowers/{specs,plans}/` in the `appsec-mvp` repository . Each
task was implemented by a fresh Opus subagent and then reviewed by a
separate specification compliance subagent and a separate code quality
subagent across two reviewer cycles . The reviewer cycles caught the
defect classes recorded in
<a href="#sec:iteration-summary" data-reference-type="autoref"
data-reference="sec:iteration-summary">[sec:iteration-summary]</a>: a
layering boundary, schema drift between <span acronym-label="sql"
acronym-form="singular+short">sql</span> <span acronym-label="ddl"
acronym-form="singular+short">ddl</span> and PySpark types, a secret
scope mismatch, worktree pollution, a cron schedule collision, and IRSA
OIDC trust policy gaps. The same Subagent-Driven pattern with paired
reviewers was also applied to skill chain runs in the second workflow.

This is my main <span acronym-label="ai"
acronym-form="singular+short">ai</span> use.
<a href="#sec:ai-eval" data-reference-type="autoref"
data-reference="sec:ai-eval">[sec:ai-eval]</a> evaluates it. The four
skills published on the [documentation
site](https://vkraus.github.io/appsec-mvp/platform/reference/connector-skills/)
are <span class="mark">analyze-source</span> ,
<span class="mark">provision-source</span> ,
<span class="mark">generate-connector</span> , and
<span class="mark">validate-implementation</span> . They are an
<span acronym-label="ai" acronym-form="singular+short">ai</span>
assisted companion to the requirements specification.

### MVP Documentation (`appsec-mvp-docs.zip`)

The [<span acronym-label="mvp" acronym-form="singular+short">mvp</span>
documentation](https://vkraus.github.io/appsec-mvp/), attached to this
thesis as `appsec-mvp-docs.zip`, is <span acronym-label="ai"
acronym-form="singular+short">ai</span> assisted content.

I authored the four skills on the [skills
page](https://vkraus.github.io/appsec-mvp/platform/reference/connector-skills/)
in Claude Code, using the Anthropic skill writing skill . Each skill
carries one <span class="mark">SKILL.md</span> for the role and one
<span class="mark">references/\<category\>.md</span> for each
application security category exercised by the <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> (CMDB, SCM, SAST, SCA, Secrets,
DAST, WAF), totaling 32 authored files across the four skills. Container
scanning and <span acronym-label="iac"
acronym-form="singular+short">iac</span> scanning are part of the
framework finding categories enumerated at
<a href="#sec:silver-findings-design" data-reference-type="autoref"
data-reference="sec:silver-findings-design">[sec:silver-findings-design]</a>
but are not exercised by any <span acronym-label="mvp"
acronym-form="singular+short">mvp</span> connector, so the skill catalog
does not yet ship reference pages for them. The layout follows the
published Anthropic recommendation for skills that span multiple
variants, defended in the Extension Blueprint section of
<a href="#ch:framework" data-reference-type="autoref"
data-reference="ch:framework">[ch:framework]</a> . I iterated each skill
until it produced the intended output. The skill chain was then used to
generate connector code for the reference implementation, as disclosed
in the Source Code section above.

### Supporting Tools

I used <span acronym-label="ai" acronym-form="singular+short">ai</span>
assistance in Claude Code for maintaining LaTeX script files that were
used to build this document .
