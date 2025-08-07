# Expedia-Scale Real-Time Travel Recommendation System

This project is a production-grade, full-stack, multi-stage travel recommendation system designed to mimic real-world systems at scale (e.g., Expedia, Booking.com, Airbnb). It leverages modern machine learning architectures, distributed processing, real-time ingestion, and scalable microservices.

---

## 🚀 Project Goals

- Build a modular, end-to-end pipeline for travel and product recommendations.
- Achieve industry-grade performance, scalability, and maintainability.
- Develop a realistic multi-stage recommendation engine using:
  - Two-Tower Model for candidate generation
  - GBDT for fine ranking
  - Learn-to-Rank for final reranking
- Deploy a REST API backend (Flask or FastAPI) supporting real-time querying.
- Integrate Apache Kafka for real-time event ingestion (clicks, views, likes, etc.)
- Store large-scale datasets and models in S3, PostgreSQL, and feature store.
- Schedule CI/CD and training jobs using Apache Airflow.
- Containerize and orchestrate via Docker and Kubernetes.
- Monitor services and performance using Prometheus + Grafana.

---

## 🧠 Machine Learning Models

### Stage 1: Candidate Generation (Two-Tower Deep Learning Model)
- Learns embeddings for users and items separately.
- Trained to retrieve top-N travel products using vector similarity.
- Fast recall using approximate nearest neighbors.

### Stage 2: Filtering Layer
- Removes blocked, invalid, recently recommended, and duplicate listings.
- Ensures diversity and quality of the recommendations.

### Stage 3: Fine Ranking (Gradient Boosted Decision Trees)
- Scores each candidate based on rich feature vectors (e.g., CTR, item popularity, user behavior).
- Trained on offline metrics like NDCG, MAP, Precision@K.

### Stage 4: Re-ranking (Learn-to-Rank)
- Reorders top-k results based on personalization and intent.
- Focused on optimizing user engagement and conversion.

---

## 🏗️ Tech Stack

| Component          | Technology                           |
|-------------------|--------------------------------------|
| Storage           | AWS S3, PostgreSQL                   |
| Real-time Ingestion | Apache Kafka                         |
| Feature Store     | SageMaker Feature Store (or Feast)   |
| Processing Engine | Apache Spark                         |
| ML Training       | TensorFlow (DL), XGBoost (GBDT)      |
| Experiment Tracking | MLflow                              |
| Serving API       | Flask or FastAPI                     |
| CI/CD + Scheduling| Apache Airflow                       |
| Monitoring        | Prometheus + Grafana                 |
| Containerization  | Docker                               |
| Orchestration     | Kubernetes                           |
| Frontend (Planned)| ReactJS + Spring Boot                |

---

## 🗂 Datasets Used

- **RecSys Challenge 2021 (Booking.com)** – Large-scale session-based travel recommendation data.
- **Expedia Hotel Recommendations (Kaggle)** – Historical bookings and hotel click logs.
- **Airbnb New User Bookings (Kaggle)** – Classify user intent and cold-start behavior.

---

## 📦 System Components

1. **Data Ingestion Service**
   - Consumes user events from the frontend (e.g., views, clicks).
   - Streams data to Kafka topics in real-time.
   - Stores raw logs in S3 and writes structured records to PostgreSQL.

2. **Data Processing with Spark**
   - Processes large-scale historical logs from S3.
   - Generates feature sets, user embeddings, and interaction histories.
   - Publishes features to the feature store and precomputes ANN indexes.

3. **Model Training Pipeline**
   - Orchestrated via Apache Airflow:
     - Two-tower model (TensorFlow)
     - GBDT model (XGBoost)
     - Learn-to-rank model
   - Training artifacts stored in S3.
   - Experiment logs tracked using MLflow.

4. **Real-time REST API (Flask/FastAPI)**
   - Accepts user requests and sessions.
   - Fetches cached/precomputed candidates.
   - Applies filtering, ranking, and reranking in sequence.
   - Returns top-N personalized recommendations with metadata.

5. **Monitoring & Logging**
   - Prometheus scrapes metrics from API + Airflow + Kafka.
   - Grafana dashboard monitors latency, throughput, CTR, etc.

---

## 🧪 Sprint Structure

| Sprint | Goal |
|--------|------|
| Sprint 1 | Dataset ingestion, schema design, and data lake setup |
| Sprint 2 | Apache Kafka ingestion, Spark setup, feature engineering |
| Sprint 3 | Train Two-Tower candidate model + ANN index |
| Sprint 4 | Train GBDT fine ranking + filtering layer |
| Sprint 5 | Learn-to-Rank model + Airflow CI/CD pipelines |
| Sprint 6 | Flask/FastAPI REST API, serving pipeline, metrics & monitoring |

---

## 🧑‍💻 Development Mode

To run locally:

```bash
docker-compose up --build
```
To test Airflow:

```bash
Copy
Edit
cd airflow_pipeline
docker-compose up
```
To deploy models via Flask:

```bash
Copy
Edit
cd server
python app.py
```

## ✅ Key Features
💡 Real-time personalization

🔄 Model versioning and tracking with MLflow

⚙️ Fully automated CI/CD pipeline

📉 Re-ranking for optimized engagement

⚡ ANN search for high-performance recall

📊 Grafana dashboards to monitor system health

## 📚 Learning Objectives
Master large-scale ML systems & pipelines

Understand candidate generation vs ranking separation

Gain experience with real-world tools used in industry

Build a recruiter-facing, resume-grade project

Demonstrate full-stack MLOps and backend engineering proficiency

## 💼 Future Plans
Implement full frontend 

Add feedback collection (like/dislike, filters)

Add personalization over time (user segmentation, intent prediction)

Implement AB testing
