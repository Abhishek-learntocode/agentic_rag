# Project Setup

Developed by Abhishek

Purpose
- Minimal, developer-focused instructions to run this RAG-based paper ingestion and search service locally.

Requirements
- Docker & Docker Compose
- Python 3.12+
- `uv` (UV package manager) for this project
- Recommended: 8GB RAM, 20GB free disk

Quick start (Unix / macOS)

```bash
git clone <repository-url>
cd production-agentic-rag
cp .env.example .env
uv sync
docker compose up --build -d
```

Quick start (Windows PowerShell)

```powershell
git clone <repository-url>
cd production-agentic-rag
Copy-Item .env.example .env
uv sync
docker compose up --build -d
```

Verify
- API health: `http://localhost:8000/api/v1/health`
- API docs: `http://localhost:8000/docs`
- Gradio UI: `http://localhost:7861`
- Airflow: `http://localhost:8080`
- OpenSearch Dashboards: `http://localhost:5601`

Notes
- Edit `.env` to configure OpenSearch, database, and embedding/LLM credentials before starting.
- Airflow credentials are generated at `airflow/simple_auth_manager_passwords.json.generated`.
- Source code lives in the `src/` folder. Example notebooks are in `notebooks/`.
- Run unit and integration tests with `pytest`.

Troubleshooting
- If services fail to start, run `docker compose logs --follow` to inspect logs.
- On low-memory machines, start only required services by editing `docker compose` commands.

License
- See LICENSE in the repository root.

If you prefer a different developer name or additional brief instructions (e.g., CI, deployment), tell me the preferred text.
