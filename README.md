# Techno Cloud API

FastAPI-based cloud-ready REST API with Docker containerization, AWS ECR image registry, and automated CI/CD deployment to Amazon EKS via GitHub Actions.

---

## Overview

Techno Cloud API is a lightweight backend service designed as a deployment-ready foundation for scalable cloud applications.

### Current Features

* FastAPI backend
* Root endpoint (`/`)
* Health check endpoint (`/health`)
* Dockerized deployment
* GitHub Actions CI/CD pipeline
* AWS ECR image build & push
* Amazon EKS Kubernetes deployment restart automation

---

## Tech Stack

### Backend

* Python 3.10
* FastAPI
* Uvicorn

### DevOps / Cloud

* Docker
* GitHub Actions
* AWS ECR (Elastic Container Registry)
* AWS EKS (Elastic Kubernetes Service)
* Kubernetes (`kubectl`)

---

## Project Structure

```bash
techno-cloud-api/
│── main.py                 # FastAPI application
│── Dockerfile              # Container build config
└── .github/
    └── workflows/
        └── deploy.yml      # CI/CD pipeline for AWS
```

---

## API Endpoints

### GET `/`

Returns API status message.

**Response:**

```json
{
  "message": "Techno API Running"
}
```

---

### GET `/health`

Returns service health status.

**Response:**

```json
{
  "status": "ok"
}
```

---

## Local Development Setup

### 1. Clone Repository

```bash
git clone https://github.com/yourusername/techno-cloud-api.git
cd techno-cloud-api
```

### 2. Install Dependencies

```bash
pip install fastapi uvicorn boto3
```

### 3. Run Locally

```bash
uvicorn main:app --reload
```

### 4. Access API

```bash
http://127.0.0.1:8000/
```

### FastAPI Docs

```bash
http://127.0.0.1:8000/docs
```

---

## Docker Deployment

### Build Image

```bash
docker build -t techno-api .
```

### Run Container

```bash
docker run -p 8000:8000 techno-api
```

---

## AWS CI/CD Pipeline

### Workflow Trigger

Pipeline runs automatically on push to:

```bash
main
```

### Build Stage

* Checkout repository
* Configure AWS credentials
* Login to AWS ECR
* Build Docker image
* Tag image
* Push image to ECR

### Deploy Stage

* Configure AWS credentials
* Install kubectl
* Connect to EKS cluster
* Verify cluster connection
* Restart Kubernetes deployment

---

## Required GitHub Secrets

Set these in:

**GitHub Repository → Settings → Secrets and variables → Actions**

```env
AWS_ACCESS_KEY
AWS_SECRET_KEY
```

---

## AWS Infrastructure Requirements

Before deployment, ensure:

* ECR repository exists:

```bash
techno-api
```

* EKS cluster exists:

```bash
techno-cluster
```

* Kubernetes deployment exists:

```bash
techno-api
```

---

## Example Kubernetes Restart Command

```bash
kubectl rollout restart deployment techno-api
```

---

## Security Notes

### Recommended Improvements

* Use `requirements.txt`
* Pin dependency versions
* Add environment variable management
* Add HTTPS ingress
* Add Kubernetes manifests (`deployment.yaml`, `service.yaml`)
* Add logging and monitoring
* Replace root AWS credentials with IAM roles

---

## Future Roadmap

* Authentication (JWT)
* Database integration (PostgreSQL / DynamoDB)
* API versioning
* Rate limiting
* Monitoring with Prometheus/Grafana
* Terraform infrastructure as code
* Blue/Green deployment

---

## Example `requirements.txt`

```txt
fastapi
uvicorn
boto3
```

---

## Author

**Sofian Hidayat**

Engineer-focused cloud backend foundation project for scalable API systems.

---

## License

MIT License
