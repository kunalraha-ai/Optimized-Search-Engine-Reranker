🔍 Optimized Semantic Search Microservice
[
�
Load image
](https://python.org)
[
�
Load image
](https://fastapi.tiangolo.com)
[
�
Load image
](https://docker.com)
[
�
Load image
](https://trychroma.com)
"Search is not just about matching keywords; it is about understanding intent."
🚀 Overview
A high-performance RAG (Retrieval-Augmented Generation) microservice designed for low-latency semantic search on CPU — no GPU required.
Uses BGE-M3 (Bi-Encoder) optimized for semantic mapping, achieving ~1s latency on standard CPU hardware. Fully containerized and production-ready.
This mimics the architecture used in modern RAG pipelines to ensure LLMs receive only the most relevant context — without the infrastructure overhead.
🏗️ Architecture
graph LR
    A["Client"] -->|Query| B("FastAPI Backend")
    B -->|Embed Query| C{"BGE-M3 Bi-Encoder"}
    C -->|Query Vector| D["ChromaDB"]
    D -->|Top-K Results| B
    B -->|Ranked Results| A
⚡ Key Features
BGE-M3 Bi-Encoder — optimized for semantic mapping and multilingual search
~1s latency on CPU — no GPU required, runs on any standard machine
ChromaDB — persistent vector storage with fast similarity search
Dockerized — single command deployment
FastAPI — production-grade async API
🚀 Quick Start
Prerequisites
Docker & Docker Compose installed
Run the Container
docker-compose up --build -d
Test the API
POST http://localhost:8000/search
Example Request:
{
    "query": "What are the contract obligations?",
    "top_k": 5
}
Example Response:
{
    "status": "success",
    "results": [
        {
            "rank": 1,
            "text": "The contractor must deliver within 30 days...",
            "score": 0.92
        }
    ],
    "count": 5
}
🛠 Tech Stack
Layer
Technology
Language
Python 3.10
Framework
FastAPI
Embeddings
BGE-M3 Bi-Encoder
Vector Store
ChromaDB
Container
Docker (Debian Slim)
🔧 Troubleshooting
Container won't start:
# Check logs
docker compose logs -f
Slow first query:
BGE-M3 model loads on first request — subsequent queries hit ~1s latency
Port already in use:
# Change port in docker-compose.yml
ports:
  - "8001:8000"
📄 License
MIT
