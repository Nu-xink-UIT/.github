# 🏆 Gold Price Analytics Platform

Welcome to the **Gold Price Analytics Platform** organization. This enterprise-grade, event-driven data platform architecture is designed to ingest, stream, process, and analyze real-time domestic (SJC) and international gold price data.

Our system architecture transitions from automated cloud infrastructure provisioning to real-time stream processing and modern data warehousing techniques.

---

## 🏗️ System Architecture

The platform is architected as a decoupled, microservices-based data ecosystem deployed on Google Cloud Platform (GCP) and managed via Kubernetes (GKE).



### Core Data Flow:
1. **Ingestion:** Dedicated Python producers scrape high-frequency gold price data from multi-source APIs and websites.
2. **Streaming & Ingestion:** Data is published to distributed Apache Kafka raw topics hosted on Kubernetes.
3. **Transformation:** `dbt` orchestrates the Medallion Architecture layers (Bronze -> Silver -> Gold) directly inside ClickHouse.
4. **Storage & Analytics:** Columnar storage in ClickHouse optimizes high-speed analytical queries and downstream dashboards.

---

## 📂 Repository Navigation

The ecosystem is modularized into three core specialized repositories:

| Repository | Focus Area | Key Tech Stack |
| :--- | :--- | :--- |
| [🔗 platform-infra](https://github.com/YOUR_ORG/platform-infra) | **Infrastructure as Code & Cloud Ops** | GCP, Kubernetes (K8s), Docker, Cloud Networking |
| [🔗 kafka-integration](https://github.com/YOUR_ORG/kafka-integration) | **Real-time Data Ingestion & Streaming** | Apache Kafka, Python, Scrapy/APIs, K8s Pods |
| [🔗 dbt-clickhouse](https://github.com/YOUR_ORG/dbt-clickhouse) | **Modern Data Warehousing & Modeling** | dbt Core, ClickHouse, Medallion Architecture, SQL |

---

## 🚀 Key Architectural Highlights

* **Infrastructure-as-Platform:** Fully containerized services running on a Kubernetes cluster, allowing independent scaling of ingestion producers and storage clusters.
* **Event-Driven Resilience:** Apache Kafka acts as a durable buffer, ensuring zero data loss during high-volatility market spikes.
* **High-Performance Analytics:** Leveraging ClickHouse's columnar vector execution and optimized table engines (e.g., `ReplacingMergeTree`) to handle time-series gold price data seamlessly.
* **Data Governance & Quality:** `dbt` handles automated schema validation and data freshness tests before pushing aggregated metrics to the Gold layer.

---
*Maintained by the Data Engineering Team. For deployment instructions, please navigate to the respective repositories.*
