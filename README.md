# IMDB Sentiment Analysis – MLOps Pipeline

A complete MLOps pipeline for sentiment analysis on the **IMDB movie reviews dataset**, leveraging **MLflow**, **DVC**, **GitHub**, **Amazon EKS**, and **S3** for end-to-end model development, tracking, and deployment.

---

## Table of Contents

* [Project Overview](#project-overview)
* [Features](#features)
* [Architecture](#architecture)
* [Setup Instructions](#setup-instructions)
* [Data Management with DVC](#data-management-with-dvc)
* [Training & Experiment Tracking](#training--experiment-tracking)
* [Model Deployment](#model-deployment)
* [Project Structure](#project-structure)
* [Contributing](#contributing)
* [License](#license)

---

## Project Overview

This project implements a **sentiment analysis model** on IMDB movie reviews while following **MLOps best practices**:

* Versioned datasets using **DVC**.
* Model experimentation and tracking using **MLflow**.
* Code versioning and collaboration via **GitHub**.
* Model deployment on **Amazon EKS (Kubernetes)**.
* Data and model artifact storage in **Amazon S3**.

The goal is to maintain reproducibility, scalability, and ease of deployment in production.

---

## Features

* Train **NLP models** (e.g., Logistic Regression, Random Forest, or Transformers) on IMDB reviews.
* Experiment tracking with **MLflow** (metrics, parameters, models).
* Dataset versioning using **DVC**.
* Artifact storage on **S3**.
* Deployment-ready Docker container orchestrated on **EKS**.
* Fully reproducible pipeline from raw data to deployed service.

---

## Architecture

```
IMDB Dataset (raw) --> DVC versioning --> Preprocessing --> Model Training
      |                                      |
      +--> S3 storage for dataset             +--> MLflow tracking
                                               |
                                               +--> Docker Container --> EKS Deployment
```

---

## Setup Instructions

### Prerequisites

* Python 3.10+
* Git
* Docker
* AWS CLI configured
* Kubectl & eksctl

### Clone Repository

```bash
git clone https://github.com/yourusername/imdb-mlops.git
cd imdb-mlops
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Data Management with DVC

### Initialize DVC

```bash
dvc init
```

### Configure Remote Storage (S3)

```bash
dvc remote add -d s3remote s3://your-bucket-name/imdb-dvc
dvc remote modify s3remote access_key_id <YOUR_AWS_ACCESS_KEY>
dvc remote modify s3remote secret_access_key <YOUR_AWS_SECRET_KEY>
```

### Add & Push Data

```bash
dvc add data/raw/imdb.csv
dvc push
git add data/.gitignore data.dvc
git commit -m "Add raw IMDB dataset with DVC"
git push origin main
```

---

## Training & Experiment Tracking

### Run Training with MLflow

```bash
mlflow run src/train --experiment-name imdb-sentiment
```

### MLflow UI

```bash
mlflow ui
# Open http://localhost:5000
```

**Track:**

* Model parameters
* Accuracy & F1 metrics
* Model artifacts

---

## SOON TO BE PUSHED TO THIS REPO


## Model Deployment

### Build Docker Image

```bash
docker build -t imdb-sentiment:latest .
```

### Push to AWS ECR

```bash
aws ecr create-repository --repository-name imdb-sentiment
docker tag imdb-sentiment:latest <aws_account_id>.dkr.ecr.<region>.amazonaws.com/imdb-sentiment:latest
docker push <aws_account_id>.dkr.ecr.<region>.amazonaws.com/imdb-sentiment:latest
```

### Deploy on Amazon EKS

```bash
eksctl create cluster --name imdb-cluster --region <region>
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

Your service should now be accessible via the EKS Load Balancer.

---

## Project Structure

```
imdb-mlops/
├── data/
│   ├── raw/
│   └── processed/
├── src/
│   ├── train.py
│   ├── evaluate.py
│   └── utils.py
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
├── requirements.txt
├── dvc.yaml
├── Dockerfile
└── README.md
```

---

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch
3. Commit changes
4. Push and create a Pull Request

---

## License

MIT License © 2025 – Ayush Kumar



## MOTION IN DEVELOPMENTS

# MLFLOW

<img width="1890" height="799" alt="Screenshot 2025-08-17 164945" src="https://github.com/user-attachments/assets/d47c8f1f-2b55-40e6-9705-e8801ce40545" />
<img width="1888" height="732" alt="Screenshot 2025-08-17 164231" src="https://github.com/user-attachments/assets/4538878c-91e4-46f2-ac9c-53820d1046ee" />

<img width="1447" height="479" alt="Screenshot 2025-08-17 163827" src="https://github.com/user-attachments/assets/79530dae-1474-441d-a62b-960bfa6207b2" />
<img width="1664" height="723" alt="Screenshot 2025-08-17 163104" src="https://github.com/user-attachments/assets/82cd6419-8373-40e5-975d-0e5e9ffc936a" />

<img width="1493" height="731" alt="Screenshot 2025-08-17 161823" src="https://github.com/user-attachments/assets/887f33fd-a49d-4674-9f35-a332f656f202" />
<img width="952" height="793" alt="Screenshot 2025-08-17 155059" src="https://github.com/user-attachments/assets/363c1ae8-f737-448f-8edd-71be3734c963" />




# GITHUB ACTIONS

<img width="1887" height="723" alt="image" src="https://github.com/user-attachments/assets/3adea5c9-3642-4247-9c47-4189a54af422" />


<img width="1406" height="640" alt="image" src="https://github.com/user-attachments/assets/9bfa1ca5-6857-4b92-ae37-e7c83ac17589" />


<img width="1854" height="868" alt="image" src="https://github.com/user-attachments/assets/71add755-f3ae-4ca7-a9f5-df7d2e777eaf" />








