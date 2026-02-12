# NLP Agent with Medallion architecture & CI/CD pipeline.

This project implements an **NLP agent** built on the **medallion architecture (bronze → silver → gold)** within Databricks, combined with a **CI/CD workflow** to ensure reproducibility, quality, and automated deployment.

---

## 📂 Project Structure

### Medallion Architecture in Databricks
- **Bronze layer** → ingestion of raw data (logs, annotations, initial airlines flights dataset).
- **Silver layer** → cleaning, normalization, and enrichment (e.g., NLP preprocessing: tokenization, text normalization).
- **Gold layer** → data ready for agent consumption:
  - *Inference features*: variables prepared for prediction.
  - *Annotation metrics*: indicators of label quality and distribution.

### Agent in the Repository
- Notebook/service acting as the agent entrypoint (`Agent.ipynb` → later migrated to Python script).
- Functions for inference and annotation workflows.
- Connection to **Gold** tables for prepared data.

### CI/CD Workflow
- **Linting and unit tests** with `pytest`.
- **Build** → package the agent as a Docker container.
- **Deploy** → run on Databricks Jobs or an AWS EKS cluster.
- **Infrastructure as code** → Terraform to describe resources (clusters, storage, pipelines).

### Practical Integration
- Folder `/src` → agent code.
- Folder `/workflows` → medallion pipeline definitions.
- Folder `/docs` → documentation and examples.
- `.github/workflows/ci.yml` → CI/CD pipeline.
- In Databricks:
  - Delta Lake for Bronze/Silver/Gold layers.
  - Databricks Repos configured to sync with GitHub.

---

## 📊 Gold Dashboard
The project includes a **Databricks SQL dashboard** showcasing:
- Class balance (`is_delayed`).
- Average delays by airline.
- Average delays by day of the week.
- Temporal distribution of delays.

This dashboard demonstrates consumption of the **Gold** layer and can be integrated into the README with screenshots or SQL queries.

---

## 📌 Notes
- Initially developed in **Databricks Community Edition**, with potential migration to Trial or paid workspaces for advanced integrations.
- The medallion architecture ensures reproducibility and scalability in data pipelines

