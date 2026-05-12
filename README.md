# Velox Search

Velox Search is a low-latency, modular backend search service designed to handle fast document indexing, ranking, and retrieval across large-scale text collections. The system decouples heavy background ingestion from client request handling to ensure optimal throughput and scalability.

## 🚀 Key Features

* **Modular Search Pipeline:** Structured document processing pipeline featuring isolated indexing, TF-IDF ranking, and retrieval stages.
* **Asynchronous Processing:** Leverages Redis Queue (RQ) to process heavy document ingestion tasks in the background without blocking API endpoints.
* **Performance Caching:** Integrated Redis caching layers to store frequent queries, significantly slashing search response latencies.
* **Traffic Control:** Built-in API rate limiting middlewares to safeguard system resources against high-volume traffic spike vulnerabilities.
* **Lightweight Storage:** Uses an optimized SQLite relational database layer for persistent metadata and inverted index tracking.

## 🛠️ System Architecture

1. **Ingestion Layer:** RESTful endpoints built with FastAPI receive raw documents asynchronously.
2. **Task Broker:** Redis Queue offloads incoming documents to background workers for ingestion and text parsing.
3. **Indexing Core:** Text tokenization, stop-word removal, and inverted index mapping written natively in Python.
4. **Storage & Cache Layer:** SQLite handles fast index state persistence while Redis manages immediate query caches and access controls.

## 💻 Tech Stack

* **Backend:** Python (FastAPI)
* **Task Management & Caching:** Redis (RQ, Rate Limiting)
* **Database:** SQLite (SQL)
* **Frontend Demo:** Next.js (React Framework)

## 🔧 Installation & Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com
   cd VeloxSearch/app
   ```

2. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Start the Redis Server:**
   ```bash
   redis-server
   ```

4. **Launch the FastAPI Server:**
   ```bash
   uvicorn main:app --reload
   ```
