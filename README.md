# Optimized Semantic Search Microservice

> "Search is not just about matching keywords — it's about understanding intent."

A high-performance RAG (Retrieval-Augmented Generation) microservice designed for **low-latency semantic search on CPU** — no GPU required.

---

## Overview

Uses **BGE-M3 (Bi-Encoder)** optimized for semantic mapping and multilingual search, achieving **~1s latency on standard CPU hardware**. Fully containerized and production-ready.

This mimics the architecture used in modern RAG pipelines — ensuring LLMs receive only the most relevant context, without the infrastructure overhead.

---

## Architecture

```
Client
  └─► FastAPI Backend
        └─► BGE-M3 Bi-Encoder (Embed Query)
              └─► ChromaDB (Query Vector Store)
                    └─► Top-K Results
                          └─► Ranked Results
```

---

## Key Features

- ✅ No GPU required — runs on any standard machine
- ✅ ChromaDB — persistent vector storage with fast similarity search
- ✅ Dockerized — single command deployment
- ✅ Production-grade async FastAPI

---

## Quick Start

**Prerequisites:** Docker & Docker Compose

```bash
# Clone and run
docker-compose up --build -d
```

Test the API:

```bash
curl -X POST http://localhost:8000/search \
  -H "Content-Type: application/json" \
  -d '{"query": "What are the contract obligations?", "top_k": 5}'
```

Example response:

```json
{
  "status": "success",
  "results": [
    { "rank": 1, "text": "The contractor must deliver within 30 days...", "score": 0.92 }
  ],
  "count": 5
}
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3.10 |
| Framework | FastAPI |
| Embeddings | BGE-M3 Bi-Encoder |
| Vector Store | ChromaDB |
| Container | Docker (Debian Slim) |

---

## Troubleshooting

**Container won't start?**
```bash
docker compose logs -f
```

**Slow first query?**
BGE-M3 loads on first request — subsequent queries hit ~1s latency.

**Port already in use?**
Change port in `docker-compose.yml`:
```yaml
ports:
  - "8001:8000"
```

---

## License

MIT
