# 🏆 Gold Price Analytics Platform

Welcome to the **Gold Price Analytics Platform** organization. This enterprise-grade, event-driven data platform architecture is designed to ingest, stream, process, audit, and analyze high-frequency market data from domestic (**SJC**), international (**Goldprice**), and cryptocurrency (**Binance**) assets in real-time.

Our infrastructure transitions seamlessly from Cloud Ingestion and Event Streaming to Modern Data Warehousing via a robust Lambda Architecture, ensuring absolute data consistency and observability.

---

## 🏗️ System Architecture

The platform is engineered as a decoupled, microservices-based data ecosystem deployed on Google Cloud Platform (GCP) and fully containerized via Kubernetes.

// data flow demonstation will be deployed here.



### 🔄 End-to-End Data Flow
1. **Speed Layer (Real-time):** Automated Python scrapers containerized on Kubernetes pods continuously ingest high-frequency source data and publish events to Apache Kafka topics. The native ClickHouse Kafka Engine, combined with Materialized Views, streams this data directly into columnar tables, achieving an end-to-end processing latency of under 5 seconds.
2. **Batch Layer (Reconciliation):** Raw ingestion files are persistently backed up to a Google Cloud Storage data lake. Scheduled dbt core jobs execute every 6 hours, utilizing ClickHouse table functions to fetch and re-sync this historical data to eliminate any streaming message loss.
3. **Serving & Presentation:** The optimized ClickHouse OLAP engine processes multi-dimensional analytical queries, delivering low-latency metrics directly to downstream Grafana and Google Looker real-time dashboards.

---

## 📂 Repository Navigation

To maximize maintainability and scalability, our ecosystem is modularized into three specialized public repositories:

| Repository | Focus Area | Core Tech Stack |
| :--- | :--- | :--- |
| [🔗 platform-infra](https://github.com/Nu-xink-UIT/platform-infra) | **Infrastructure as Code & Cloud Ops** | GCP, GKE, Kubernetes (K8s), Docker, Cloud Networking, Prometheus |
| [🔗 kafka-integration](https://github.com/Nu-xink-UIT/kafka-intergration) | **Real-time Data Ingestion & Streaming** | Apache Kafka, Python, Scrapy, Custom APIs, K8s Pods |
| [🔗 dbt-clickhouse](https://github.com/Nu-xink-UIT/dbt-clickhouse) | **Modern Data Warehousing & Transformation** | dbt Core, ClickHouse OLAP, Medallion Architecture, SQL |

---

## 🎯 Personal Skill Mapping

By designing and executing this platform, the engineering team has achieved deep industry-level proficiency across the following technical domains:
* **Data Infrastructure Architecture:** Devising decoupled distributed topologies (Kafka, ClickHouse, Kubernetes) and optimizing cloud operational expenditures.
* **Advanced Analytical Engineering:** Mastery over `dbt` state testing, relational data-lake layering, and optimizing columnar databases for high-velocity time-series datasets.
* **Enterprise GitOps:** Productionizing modern Continuous Integration flows, developing security RBAC standards.

---

## 🤝 Acknowledgments

We would like to express our deepest gratitude to our mentors, for their invaluable guidance, architectural insights, and continuous support throughout the development of this project.