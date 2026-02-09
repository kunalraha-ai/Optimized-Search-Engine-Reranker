# Pax Historia Semantic Search Engine

High-performance RAG (Retrieval-Augmented Generation) microservice designed for low-latency semantic search on CPU.

## ⚡ Key Features
- **Model:** BGE-M3 (Bi-Encoder) optimized for semantic mapping.
- **Performance:** ~1s latency on standard CPU (No GPU required).
- **Architecture:** Dockerized microservice (FastAPI + ChromaDB).

## 🚀 Quick Start

### Prerequisites
- Docker & Docker Compose installed.

### Run the Container
```bash
docker-compose up --build -d
Test the API
The search endpoint will be available at: POST http://localhost:8000/search

🛠 Tech Stack
Language: Python 3.10

Framework: FastAPI

Container: Docker (Debian Slim)
Private Repository.
