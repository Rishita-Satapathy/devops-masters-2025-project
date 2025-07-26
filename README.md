flowchart TD
  %% Direction top to bottom
  direction TB

  %% Developer
  subgraph DEV["👨‍💻 Developer"]
    A1["💻 Push Code to GitHub"]
  end

  %% GitHub Actions CI/CD Flow
  subgraph CICD["🔁 CI/CD with GitHub Actions"]
    B1["⚙️ GitHub Actions Workflow"]
    B2["🔍 tfsec - Terraform Security Scan"]
    B3["🔐 Trivy - Docker Image Scan"]
    B4["🔑 Sealed Secrets CLI"]
  end

  %% AWS Infra
  subgraph AWS["☁️ AWS Infrastructure via Terraform"]
    C1["📦 S3 Bucket\n(Artifact Storage)"]
    C2["🏗️ CodeBuild\n(Build & Test)"]
    C3["🚀 CodeDeploy\n(EC2 Deployment)"]
    C4["🔁 CodePipeline\n(CI/CD Orchestrator)"]
    C5["🔐 IAM Roles & Policies"]
  end

  %% Kubernetes Cluster
  subgraph K8S["📦 Kubernetes Cluster"]
    D1["🧩 SealedSecrets Controller"]
    D2["🛠️ Workload using Secrets"]
    D3["☸️ Kubernetes Workloads"]
  end

  %% Flow connections
  A1 --> B1
  B1 --> B2
  B1 --> B3
  B1 --> B4
  B1 --> C4

  C4 --> C1
  C4 --> C2
  C4 --> C3
  C4 --> C5

  B4 --> D1
  D1 --> D2
  C3 --> D3
