# AI Personal Infrastructure Assistant



## Current Status



**This project is currently in the planning and architecture phase.**



The repository serves as a living design document and development roadmap. Components will be implemented incrementally as I progress through the learning journey.







##  Vision & Learning Sandbox

**AI Personal Infrastructure Assistant** is a self-hosted, local-first system monitoring and infrastructure management assistant powered by local Artificial Intelligence. 



>  **Project Status: Learning Sandbox & Technical Playground**

> This project is designed as my personal ultimate testing ground. My primary goal is not just to build a tool, but to learn, experiment, and push my engineering limits. Throughout this journey, I will be teaching myself development, advanced agentic workflows, self-hosted AI architecture, secure networking, and robust DevOps practices from scratch.



---



##  The Problem

Managing a home server, lab, or office infrastructure often means drowning in raw metrics, confusing log streams, and cryptic alerts. Traditional monitoring tools (like standard dashboards) tell you *what* is failing, but they don't tell you *why* or *how to fix it*. 



Furthermore, relying on public cloud AI APIs (like OpenAI or Anthropic) introduces significant privacy issues, continuous per-token costs, and an internet dependency that a local network monitoring tool simply shouldn't have.



**The Solution:** An intelligent, autonomous system agent that runs completely inside the local network. It collects system health data, buffers it securely, and feeds it into a fully local Large Language Model (LLM) combined with a local Vector Database (RAG) to provide real-time, context-aware diagnostics and automated, safe remediation steps without any data ever leaving the LAN.



---



##  System Architecture

The project is built as a highly decoupled Monorepo consisting of:

*   `/agent` - A multi-platform system resource harvester (Python) featuring local log/metric buffering and network batching.

*   `/backend` - High-performance core API (FastAPI) handling business logic, authentication, and AI pipeline routing.

*   `/frontend` - A responsive, modern real-time operations dashboard (React + TypeScript).

*   `/infra` - Local orchestration, networking, and observability stack.



---



##  Planned Tech Stack



### Backend Core

*   **Framework:** FastAPI (Python) - asynchronous, high-performance routing.

*   **Database:** PostgreSQL + `pgvector` (for vector embeddings and semantic search).

*   **Migrations:** Alembic.

*   **Async Tasks & Queue:** Celery + Redis.

*   **Authentication:** JWT (JSON Web Tokens) with role-based access control (RBAC).



### Local AI Architecture

*   **Inference Server:** Ollama / vLLM (utilizing local GPU acceleration).

*   **Open-Source LLMs:** Llama-3-8B-Instruct / Mistral-7B-Instruct / Qwen-2.5-7B.

*   **Embeddings:** `bge-m3` or `nomic-embed-text` for completely offline vector generation.

*   **AI Validation:** Pydantic Structured Outputs & custom safety command blacklists (Guardrails).



### Agent (Harvester)

*   **Language:** Python.

*   **Data Collection:** `psutil` (CPU, RAM, Disks), `smartmontools` (SMART health), Docker Engine API.

*   **Networking:** HTTPX (client-server model over LAN), customized with offline buffering, batching, and exponential backoff retries.



### Frontend

*   **Framework:** React + TypeScript (Scaffolded with Vite).

*   **State & Data Fetching:** TanStack Query (React Query).

*   **Real-time Stream:** WebSockets for live charts.

*   **Charts:** Recharts.



### DevOps, Security & Observability

*   **Containerization:** Docker & Docker Compose.

*   **Reverse Proxy & Security:** Traefik with internal TLS termination (LAN encryption) and GPU rate limiting.

*   **CI/CD:** GitHub Actions (Automated linting, multi-arch Docker builds, Semantic Releases).

*   **Observability:** Prometheus (metrics), Grafana (dashboards), Loki (centralized logs), and OpenTelemetry (distributed tracing).



---



##  Roadmap & Milestones

*   **Phase 1: Foundations & Backend Core**  - Setup, C4 Architecture, FastAPI skeleton, and DB migrations.

*   **Phase 2: Agent v1 & Containerization**  - Metric harvesting, Docker Compose orchestration, and LAN network architecture.

*   **Phase 3: Frontend & Real-time**  - React dashboard and WebSocket implementation.

*   **Phase 4: Sovereign AI Integration (MVP)**  - Local Ollama/vLLM inference, `pgvector` RAG potok, and structured output.

*   **Phase 5: Advanced AI, Security & Production**  - Trend analysis, local TLS encryption, CI/CD pipeline, and full observability.



---



## 📄 License

This project is licensed under the **MIT** License - see the `LICENSE` file for details.

