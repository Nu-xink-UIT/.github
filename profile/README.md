# 🏆 Gold Price Analytics Platform

Welcome to the **Gold Price Analytics Platform** organization. This enterprise-grade, event-driven data platform architecture is designed to ingest, stream, process, audit, and analyze high-frequency market data from domestic (**SJC**), international (**Goldprice**), and cryptocurrency (**Binance**) assets in real-time.

Our infrastructure transitions seamlessly from Cloud Ingestion and Event Streaming to Modern Data Warehousing via a robust Lambda Architecture, ensuring absolute data consistency and observability.

---

## 🏗️ System Architecture

The platform is engineered as a decoupled, microservices-based data ecosystem deployed on Google Cloud Platform (GCP) and fully containerized via Kubernetes.

// data flow demonstation will be deployed here.



### 🔄 End-to-End Data Flow
1. **Speed Layer (Real-time):** Source Data $\rightarrow$ Python Scrapers/Producers (K8s Pods) $\rightarrow$ Apache Kafka Topics $\rightarrow$ ClickHouse Kafka Engine $\rightarrow$ Materialized Views (MV) $\rightarrow$ Columnar Storage. (End-to-end latency: < 5s).
2. **Batch Layer (Reconciliation):** Raw Ingestion Files $\rightarrow$ Google Cloud Storage (GCS) Data Lake $\rightarrow$ dbt Scheduled Core Jobs (Every 6 Hours) $\rightarrow$ ClickHouse Table Functions.
3. **Serving & Presentation:** ClickHouse OLAP Engines $\rightarrow$ Grafana Real-time Dashboards.

---

## 📂 Repository Navigation

To maximize maintainability and scalability, our ecosystem is modularized into three specialized public repositories:

| Repository | Focus Area | Core Tech Stack |
| :--- | :--- | :--- |
| [🔗 platform-infra](https://github.com/YOUR_ORG/platform-infra) | **Infrastructure as Code & Cloud Ops** | GCP, GKE, Kubernetes (K8s), Docker, Cloud Networking, Prometheus |
| [🔗 kafka-integration](https://github.com/YOUR_ORG/kafka-integration) | **Real-time Data Ingestion & Streaming** | Apache Kafka, Python, Scrapy, Custom APIs, K8s Pods |
| [🔗 dbt-clickhouse](https://github.com/YOUR_ORG/dbt-clickhouse) | **Modern Data Warehousing & Transformation** | dbt Core, ClickHouse OLAP, Medallion Architecture, SQL |

---

## 🎯 Personal Skill Mapping

By designing and executing this platform, the engineering team has achieved deep industry-level proficiency across the following technical domains:
* **Data Infrastructure Architecture:** Devising decoupled distributed topologies (Kafka, ClickHouse, Kubernetes) and optimizing cloud operational expenditures.
* **Advanced Analytical Engineering:** Mastery over `dbt` state testing, relational data-lake layering, and optimizing columnar databases for high-velocity time-series datasets.
* **Enterprise GitOps:** Productionizing modern Continuous Integration flows, developing security RBAC standards.

---

## 🤝 Acknowledgments

We would like to express our deepest gratitude to our mentors, for their invaluable guidance, architectural insights, and continuous support throughout the development of this project.