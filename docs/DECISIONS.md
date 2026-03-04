# Architectural Decision Log

This document records the key architectural choices made during the implementation of the observability stack.

## 1. OpenTelemetry Collector Topology
**Decision:** Deployed a Gateway + Agent (DaemonSet) topology.
**Rationale:** 
* **DaemonSet (Agent):** Ensures node-level metrics (hostmetrics) are collected efficiently and acts as a local endpoint for application telemetry, avoiding cross-node traffic for initial ingestion.
* **Deployment (Gateway):** Centralizes processing (tail-based sampling, batching, memory limiting) before sending data to the Elastic APM server. It simplifies credential management since only the gateway needs to authenticate with the backend.

## 2. Infrastructure Monitoring Approach
**Decision:** Used [Elastic Agent / Metricbeat] for infrastructure monitoring.
**Rationale:** 
*(Explain why Fleet-managed Elastic Agents or standalone Beats were chosen over alternatives)*

## 3. Sampling Strategy
**Decision:** Configured Tail-Based Sampling at the Gateway.
**Rationale:** 
* To capture 100% of error traces for debugging.
* To capture a baseline (e.g., 10%) of successful traces to keep storage costs manageable while providing statistical visibility into performance.

## 4. RUM vs Backend Correlation
**Decision:** 
*(Detail how W3C trace context is propagated from the browser SDK through the ingress to the backend services)*

## 5. Dashboarding Decisions
**Decision:** 
*(Explain the choice of RED metrics layout, Business KPIs vs. Technical metrics segregation)*
