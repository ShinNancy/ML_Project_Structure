# ML_Project_Structure

### 🔹 `config/` — Configuration Management

All environment-specific settings live here.

* `local.yaml` — Development configuration
* `prod.yaml` — Production configuration

Keeping configuration separate from code makes deployments safer, cleaner, and easier to maintain.

---

### 🔹 `data/` — Data Lifecycle Management

Data is organized by transformation stage:

* `01-raw/` — Original, immutable data
* `02-preprocessed/` — Cleaned and standardized data
* `03-features/` — Feature-engineered datasets
* `04-predictions/` — Model outputs

This structure makes the data flow explicit and easy to understand for anyone joining the project.

---

### 🔹 `notebooks/` — Exploration & Prototyping

Used **only** for:

* Exploratory Data Analysis (EDA)
* Baseline experiments
* Visualization

All production logic is moved to `src/` to avoid notebook dependency issues such as:

> “Run cells in the wrong order and everything breaks.”

---

### 🔹 `scripts/` — Entrypoints

Clear and explicit entrypoints for core workflows:

* `train.py` — Model training
* `predict.py` — Batch or real-time inference

Training and inference are treated as **first-class workflows**, not side effects of notebooks.

---

### 🔹 `src/` — Core Source Code

This is where Machine Learning becomes **software engineering**.

* `data/` — Data loading and validation
* `features/` — Feature engineering pipelines
* `models/` — Model definitions and wrappers
* `training/` — Training logic
* `inference/` — Prediction logic

Code in this folder is modular, reusable, and testable.

---

### 🔹 `tests/` — Automated Testing

Even minimal tests significantly improve reliability.

They help to:

* Catch silent pipeline failures
* Enable confident refactoring
* Support long-term scalability

---

### 🔹 Docker & CI/CD

* `Dockerfile` and `docker-compose.yml` ensure reproducible environments
* CI pipelines (GitHub Actions, GitLab CI, etc.) can be easily integrated

Deployment and automation are considered **from day one**, not as an afterthought.

---

### 🔹 Environment Files

* `.env` files isolate secrets and environment variables

This prevents the classic problem:

> “It works on my machine”

---

### 🔹 Dependency Management

* `requirements.txt` — Production dependencies
* `requirements-dev.txt` — Development and testing tools

This keeps production environments lightweight, secure, and easier to debug.
