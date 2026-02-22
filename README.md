📊 Telco Churning Prediction — End-to-End MLOps Project

Predict customer churn in a telecom environment using a production-ready machine learning pipeline — from data validation and training to API serving and containerized deployment.

The system runs locally and is designed to be deployed on cloud platforms such as AWS ECS/Fargate.

🚀 Project Highlights

✔ End-to-end ML pipeline
✔ MLflow experiment tracking & reproducibility
✔ FastAPI inference service
✔ Gradio web interface
✔ Docker containerization
✔ GitHub Actions CI/CD
✔ Cloud-deployment ready architecture

🎯 Problem Statement

Customer churn directly impacts telecom revenue. This system predicts customers likely to churn, enabling proactive retention strategies.

💡 Business Value

Identify high-risk customers early

Enable targeted retention campaigns

Reduce churn-related revenue loss

Provide accessible predictions via API & UI

🧠 System Architecture
🔹 Training Pipeline
Data → Validation → Preprocessing → Feature Engineering
→ XGBoost Training → MLflow Logging
🔹 Serving Pipeline
API/UI → Model Load → Feature Transform → Prediction
🏗 Architecture Overview
✅ ML Pipeline

Training Pipeline

Data validation using Great Expectations

Feature engineering & preprocessing

XGBoost model training

MLflow experiment logging

Artifact storage for reproducibility

Serving Pipeline

FastAPI REST API (/predict)

Gradio UI (/ui)

MLflow model loading

Feature alignment & transformation

Real-time predictions

🔬 Machine Learning Pipeline
Data Validation

Tool: Great Expectations

Ensures schema & value correctness

Validation results logged to MLflow

Feature Engineering

Binary encoding (Yes/No → 0/1)

One-hot encoding for categorical features

Boolean normalization

Deterministic transformations for reproducibility

Model

XGBoost Classifier

Handles class imbalance via dynamic weighting

Optimized hyperparameters

Metrics Tracked

Precision

Recall

F1 Score

ROC-AUC

Training & prediction time

Data quality status

📦 MLflow Experiment Tracking

Experiment Name: Telco Churn
Tracking URI: ./mlruns

Logged Artifacts

Trained model

Feature columns

Preprocessing pipeline

Launch MLflow UI
mlflow ui --backend-store-uri file:./mlruns
🌐 API & Web Interface
FastAPI Endpoints
Endpoint	Method	Description
/	GET	Health check
/predict	POST	Churning prediction
/ui	—	Gradio interface
Prediction Output

Likely to churn

Not likely to churn

🖥 Run Locally
1️⃣ Install dependencies
pip install -r requirements.txt
2️⃣ Run the training pipeline
python scripts/run_pipeline.py --input data/raw/Telco-Customer-Churn.csv --target Churn
3️⃣ Start the API & UI
python -m uvicorn src.app.main:app --host 0.0.0.0 --port 8000
4️⃣ Open in browser

API docs:

http://localhost:8000/docs

Gradio UI:

http://localhost:8000/ui
🐳 Run with Docker
Build image
docker build -t telco-churn-app .
Run container
docker run -p 8000:8000 telco-churn-app
🧪 Testing
Data & feature pipeline
python scripts/test_pipeline_phase1_data_features.py
Model training & evaluation
python scripts/test_pipeline_phase2_modeling.py
API endpoints
python scripts/test_fastapi.py
🔁 CI/CD Pipeline

GitHub Actions Workflow

On push to main:

Build Docker image

Push image to Docker Hub

Ready for deployment

Required Secrets

DOCKERHUB_USERNAME

DOCKERHUB_TOKEN

☁️ Cloud Deployment (Optional)

This project is structured for deployment using:

AWS ECS Fargate

Application Load Balancer

CloudWatch Logs

Secure networking

Deployment can be enabled when needed.

📁 Project Structure
data/
  raw/
  processed/

scripts/
src/
  app/
  features/
  serving/
  utils/

mlruns/
artifacts/
⚙️ Model Configuration

n_estimators: 301

learning_rate: 0.034

max_depth: 7

scale_pos_weight: dynamic (class imbalance)

🛠 Tech Stack
Machine Learning

XGBoost

Scikit-learn

Pandas, NumPy

Backend & Serving

FastAPI

Uvicorn

Gradio

MLOps & Tooling

MLflow

Great Expectations

Docker

GitHub Actions

Cloud-Ready Infrastructure

AWS ECS Fargate

Application Load Balancer

CloudWatch Logs

🚧 Challenges & Solutions

Feature mismatch during inference
→ enforced feature order from training artifacts

Container import errors
→ configured PYTHONPATH=/app/src

Model loading inconsistencies
→ standardized MLflow artifact loading

Local vs container path differences
→ environment-specific loading logic

🔮 Future Improvements

Automated cloud deployment pipeline

Model drift monitoring

Canary deployments & rollback

Feature store integration

Real-time analytics dashboard

👨‍💻 Author

Roshan
Machine Learning & Backend Developer