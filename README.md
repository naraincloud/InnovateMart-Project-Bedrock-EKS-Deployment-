# InnovateMart — Project Bedrock (EKS Deployment)

## Project Overview
Project Bedrock involved deploying InnovateMart’s new **microservices retail application** to a production-grade **Amazon EKS** cluster. The goal was to create a scalable, automated, and secure environment for future development.

---

## Tasks Completed

### 1. Infrastructure as Code (IaC)
- Provisioned a **VPC** with public and private subnets for proper network segmentation.
- Deployed an **EKS cluster** using Terraform.
- Configured **IAM roles and policies** for the cluster and developer access.
- Created separate node groups for application workloads.

### 2. Application Deployment
- Deployed the **retail-store-sample-app** microservices to the EKS cluster.
- Initially ran all dependencies (databases and message brokers) as in-cluster containers.
- Verified all services were running and accessible via `kubectl`.

### 3. Developer Access
- Created an IAM user `innovatemart-dev` with **read-only access** to the EKS cluster.
- User can view cluster resources, pods, logs, and services but cannot make changes.
- Provided `kubeconfig` instructions for developers to connect securely.

### 4. CI/CD Automation
- Built a **GitHub Actions pipeline** to automate Terraform deployments:
  - Feature branches trigger `terraform plan`.
  - Merges to main trigger `terraform apply`.
- AWS credentials are stored securely in GitHub secrets.

### 5. Bonus Enhancements (Optional)
- Configured **managed databases** using AWS RDS for PostgreSQL/MySQL and DynamoDB for carts.
- Installed **AWS Load Balancer Controller** and created an Ingress resource for the frontend.
- Set up **Route 53 domain** and **ACM SSL certificate** for secure HTTPS access.

---

## Architecture Summary
- **VPC** with public and private subnets.
- **EKS Cluster** running microservices.
- **IAM user** for read-only developer access.
- Optional: Managed persistence layer and secure ingress.

---

## Outcome
- Fully automated deployment of the application to EKS.
- Secure and segmented network ready for production workloads.
- Developer access and CI/CD pipeline established for ongoing operations.

---

## Next Steps
- Scale EKS nodes based on workload.
- Move remaining services to managed AWS services for persistence.
- Extend CI/CD to support application updates and monitoring.
