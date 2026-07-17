# C4 Model – Container Diagram: AI Personal Infrastructure Assistant

## 1. Containers (System Components)

*   **Web Dashboard (Frontend)**: A React/TypeScript application providing the user interface for monitoring, system management, and AI interaction.
*   **Backend API (API Gateway)**: The central processing unit (FastAPI), managing authentication, data orchestration, Celery tasks, and AI communication.
*   **Database (PostgreSQL)**: The primary storage for application users, metrics history, alerts, and system configuration.
*   **Vector Database (pgvector)**: A specialized PostgreSQL extension storing documentation chunks for the RAG pipeline.
*   **System Agent**: A lightweight Python service deployed on monitored machines, responsible for telemetry collection and forwarding.
*   **Local LLM Server (Ollama / vLLM)**: A dedicated inference engine running open-source models, accessed by the backend via a REST API.
*   **Task Queue (Redis + Celery)**: Handles asynchronous tasks like disk scanning and metric aggregation.

## 2. Relationships

| From | Action | To |
| :--- | :--- | :--- |
| **User** | interacts with | **Web Dashboard** |
| **Web Dashboard** | calls REST/WS | **Backend API** |
| **Backend API** | stores/retrieves data | **Database** |
| **System Agent** | sends telemetry | **Backend API** |
| **Backend API** | queries context | **Vector Database** |
| **Backend API** | orchestrates inference | **Local LLM Server** |
| **Backend API** | triggers tasks | **Task Queue** |

## 3. Container Diagram (Mermaid)

```mermaid
graph TD
    User((System Administrator)) -->|Uses| Web[Web Dashboard]
    Web -->|HTTPS/WS| API[Backend API]
    
    subgraph "Central Server Cluster"
        API -->|SQL| DB[(PostgreSQL)]
        API -->|Vector Search| VDB[(pgvector)]
        API -->|Queue/PubSub| Redis[Redis + Celery]
        API -->|REST API| LLM[Local LLM Server]
    end
    
    Agent[System Agent] -->|HTTPS/TLS| API
    
    subgraph "External/Monitored"
        Agent -->|Collects| Infra[Monitored Infrastructure]
        LLM -->|RAG| KB[Knowledge Base]
    end