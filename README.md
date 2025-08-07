# Expedia-Scale Real-Time Recommendation System

A production-grade, multi-stage recommendation system designed to simulate the scale and complexity of industry leaders like Expedia, Airbnb, and Booking.com. This system supports **real-time recommendations**, **large-scale data ingestion**, and **multi-stage model inference** with **end-to-end MLOps** pipelines, infrastructure orchestration, and REST API serving.

---

## 🔍 Project Overview

This project simulates a real-world recommendation engine for travel and product recommendations. It is designed with **scalability**, **modularization**, and **real-time responsiveness** in mind. A **multi-stage architecture** is used for high-quality recommendations:

- **Candidate Generation**: Deep Learning Two-Tower Model (TensorFlow)
- **Filtering**: Removes blocked items, invalid listings, and previously shown items
- **Fine Ranking**: Gradient Boosted Decision Trees (GBDT)
- **Re-ranking**: Learn-to-Rank Model

---

## 🚀 Key Features

| Feature                     | Description |
|----------------------------|-------------|
| 🔄 Real-time Inference     | Supports real-time ingestion via **Kafka**, with cold-start mitigation |
| 🧠 Multi-Stage Modeling     | Combines DL embeddings, GBDT ranking, and LTR re-ranking |
| 💾 Feature Store           | Uses **SageMaker Feature Store** (or **Feast**, if free) |
| 🧬 Embeddings & Caching     | Fast recall with in-memory embeddings |
| 📦 Model Deployment        | Flask/FastAPI REST API + Docker + Kubernetes |
| 🛠 CI/CD                   | Apache Airflow for orchestration |
| 📈 Experiment Tracking     | Integrated with MLflow or TensorBoard |
| 📊 Monitoring              | Prometheus + Grafana stack |
| 🗃 Database                | PostgreSQL stores user interactions, views, clicks, etc. |
| ☁️ Data Storage           | AWS S3 stores raw and processed datasets |
| 📑 Dataset Sources        | RecSys Challenge 2021 (Booking.com), Airbnb New User Bookings, Expedia Hotel Recommendations |

---

## 🧱 System Architecture

