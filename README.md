# 🌍 Multi-Cloud GitOps Fleet Management

This repository demonstrates a fully automated, multi-cloud Kubernetes architecture. 

It uses **Terraform** to provision underlying infrastructure across AWS and Azure, and relies on **Flux CD** to manage cluster state, infrastructure add-ons, and application workloads synchronously across both environments via GitOps.

## 🏗️ Architecture Overview

*(Pro-tip: Create a diagram using draw.io or excalidraw and embed the image here)*
`![Architecture Diagram](./assets/arch-diagram.png)`

1. **Infrastructure as Code (Terraform):** - Provisions an Amazon EKS cluster and an Azure AKS cluster.
   - Bootstraps the Flux v2 controllers into both clusters.
2. **Configuration as Data (Flux):** - Both clusters monitor the `gitops-fleet/` directory in this repository.
   - Base add-ons (monitoring, ingress) are applied universally.
   - Custom configurations are applied using Flux Kustomization patches per cluster.

## 🚀 Workload: Cross-Cloud AI Agent
To demonstrate workload portability, this setup automatically deploys a containerized Python AI agent to both the EKS and AKS clusters simultaneously just by merging a PR to the `apps/` directory.

## 💻 Tech Stack
- **Clouds:** AWS (EKS, VPC, IAM), Azure (AKS, VNet, Entra ID)
- **IaC:** Terraform
- **GitOps / CI-CD:** Flux CD, Helm
- **Workload:** Docker, Python

## 🛠️ Setup Instructions
Instructions on how to authenticate Terraform with AWS/Azure, execute the runbooks, and verify the GitOps reconciliation loop are detailed in the `infrastructure/` directory.
