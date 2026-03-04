# SRE Observability Assessment - ITStack Limited

This repository contains the deliverables for the Site Reliability Engineer Practical Implementation Assessment.

## Objective

To implement production-grade observability and infrastructure monitoring across a distributed microservices architecture (Google Online Boutique), exporting telemetry to the Elastic Stack via OpenTelemetry.

## Repository Structure

```text
sre-assessment/
├── otel-collector/           # Helm values and OpenTelemetry collector configs (Gateway & DaemonSet)
├── instrumentation/          # Per-service instrumentation code/patches
│   ├── frontend/             # Go: HTTP middleware, template spans, downstream gRPC
│   ├── cartservice/          # C#: .NET auto-instrumentation, Redis tracing, custom metrics
│   └── paymentservice/       # Node.js: auto-instrumentation, custom spans, errors
├── rum/                      # Browser SDK integration code for Frontend
├── dashboards/               # Kibana Saved Objects (NDJSON exports)
│   ├── service-health.ndjson
│   ├── rum-performance.ndjson
│   └── business-transactions.ndjson
├── infrastructure/           # Agent/Beat configs, alert rules
│   ├── elastic-agent-policies/ # Fleet policy exports
│   ├── postgres-integration/
│   ├── redis-integration/
│   ├── nginx-integration/
│   └── alerting-rules/       # Kibana rule exports (NDJSON)
├── docs/                     
│   └── DECISIONS.md          # Architectural decision log
└── README.md                 # Setup instructions and overview
```

## Setup Instructions

### Prerequisites
* Kubernetes Cluster (Minikube / EKS / AKS) with >2 nodes
* Helm v3 installed
* Access to an Elastic Stack (Elastic Cloud or self-hosted ECK)
* Google Online Boutique Sample Application deployed

### 1. Environment Deployment
*(Detailed instructions on deploying the cluster and sample app will go here)*

### 2. OpenTelemetry Collector Setup
*(Instructions to apply Helm charts from `otel-collector/`)*

### 3. Application Instrumentation
*(Instructions to apply modified service manifests from `instrumentation/`)*

### 4. Infrastructure Monitoring
*(Instructions for deploying Elastic Agents and importing policies from `infrastructure/`)*

### 5. Dashboards & Alerts
*(Instructions for importing NDJSON files from `dashboards/` and `infrastructure/alerting-rules/`)*

## Validation

*(Provide steps on how to generate traffic and view traces/metrics in Kibana)*
