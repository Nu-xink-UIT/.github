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

## 🛠️ Production-Grade Implementation Details

### 1. Advanced Data Modeling & Optimization
* **Audit & Discovery:** Multi-source schema synchronization handling flat/nested JSON payloads. Standardized core financial metrics (`price_buy`, `price_sell`, `unit`, `source_name`, `gold_type`) to build uniform target schemas.
* **Business Glossary & Reference Base Price:** Implemented a robust data resolution strategy utilizing weighted averages and outlier removal algorithms to protect the analytics layer against single-source data signal distortion.
* **Medallion Architecture Pattern:**
  * **Bronze:** Optimized Kafka Connect and native Kafka Engines running concurrent streams.
  * **Silver:** Modular `dbt` jobs managing automated data deduplication, strict currency conversion units (VND/Lượng and USD/oz), and active timezone alignment.
  * **Gold (Star Schema):** Built high-performance central fact tables (`fact_gold_prices`) connected to optimized dimension attributes (`dim_sources`, `dim_gold_types`, `dim_date`, `dim_time`).
* **Physical ClickHouse Optimization:** Heavy partitions structured on multi-index Sorting Keys (`timestamp`, `gold_type`), enabling complex sub-range analytical query responses in **under 100ms**.

### 2. Orchestration & Transform
* **Kubernetes Deployment:** Specialized multi-stage `dbt` Docker images deployed via declarative K8s manifests (`ConfigMaps`, `Secrets`), ensuring decoupled environment configurations.
* **DAG Scheduling & Recovery:** Complex Directed Acyclic Graphs (DAGs) orchestrated via **Airflow**, enforcing data-freshness dependencies, strict service level agreements (SLAs), and self-healing automated retry loops.
* **ClickHouse Computation Optimization:** Utilizing advanced engines (`ReplacingMergeTree`, `AggregatingMergeTree`, `SummingMergeTree`) to guarantee automated background deduplication and real-time pre-aggregations (hourly averages, daily high/low tickers).
* **CI/CD & GitOps Integration:** Fully automated CI/CD workflows using GitHub Actions.
*
### 3. Data Governance, Quality
* **Data Quality Framework:** Enforced mandatory integrity restrictions (`not_null`, `unique`) on operational schemas. Implemented specialized singular business rules to detect financial anomalies (e.g., sudden >50% price deviations within a 1-minute window).


### 4. Data Serving
* **Real-time Analytics:** Highly responsive Grafana Dashboards displaying real-time financial market tickers, OHLC (Open-High-Low-Close) candlesticks, and localized arbitrage detection graphs across competing sellers.


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