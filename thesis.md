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
  - [Integration and Challenges](#integration-and-challenges)
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

### Application Inventory

#### Application Portfolio Management

#### Configuration Management Databases

#### Integration and Challenges

### Software Development

#### Source Code Management

#### Continuous Integration and Delivery

#### Issue Tracking

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
