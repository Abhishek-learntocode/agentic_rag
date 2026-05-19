# Project Overview

Developer: Abhishek

Problem statement
- Ingest and index academic papers (arXiv) so users can search and ask questions about scientific content with reliable, explainable retrieval and generation.

High-level workflow
- Ingestion:
  - `src/services/arxiv/client.py` fetches metadata and PDFs from arXiv.
  - PDFs are parsed and cleaned; metadata is normalized and stored in PostgreSQL.

- Indexing:
  - Text is chunked into searchable units.
  - Chunks are indexed into OpenSearch for keyword/BM25 retrieval.
  - Optional embeddings are generated and stored for semantic search.

- Retrieval & RAG:
  - Hybrid search combines OpenSearch keyword results with embedding-based semantic matches.
  - A RAG pipeline assembles relevant chunks and passes them to an LLM (local or hosted) to generate answers.

- Orchestration & Automation:
  - Apache Airflow DAGs schedule ingestion and periodic re-indexing.
  - Docker Compose orchestrates local service startup for development.

- Observability & Integrations:
  - Optional Langfuse tracing and Redis caching for performance and monitoring.
  - Telegram bot and agent workflows provide conversational access and agentic decision logic.

Configuration and secrets
- Configuration is primarily in environment variables (`.env`). Sensitive values (API keys, tokens, DB passwords) should not be committed. The repo uses env-var references in `compose.yml` and default local passwords for developer convenience — update `.env` before running in any non-local environment.

Where to look in the code
- Core entrypoints: `src/main.py`, `src/gradio_app.py`.
- Service implementations: `src/services/` (arxiv, indexing, embeddings, ollama, opensearch, agents).
- API routes: `src/routers/` (ask, hybrid_search, agentic_ask).
- DAGs: `airflow/dags/`.

If you want, I can also add a short diagram or a one-page PDF summarizing this flow.
