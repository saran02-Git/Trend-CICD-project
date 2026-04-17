# Node.js App CI/CD – Jenkins, Docker, Terraform, AWS

Project Overview:

This project demonstrates a complete CI/CD pipeline to build, containerize, and deploy a Node.js web application to an AWS EC2 instance using Jenkins, Docker, and Terraform.
The focus is on CI/CD implementation, infrastructure automation, deployment, and basic observability of the system.

## What I Learned:

Built this to practice real-world DevOps workflows end-to-end:
Jenkins pipeline automation
Terraform infrastructure provisioning
Docker containerization
AWS EC2 deployment
Monitoring system performance using Grafana dashboards

Prerequisites:

AWS account with IAM permissions
GitHub account
DockerHub account
Jenkins (EC2 or local VM)
Terraform installed and configured with AWS credentials
Docker installed locally and on the Jenkins agent
Node.js runtime

---

Architecture:

GitHub → Jenkins → Docker Build → AWS EC2 → Application (Port 3000) → Grafana (real-time metrics visualization via Prometheus)

---

Workflow:

1. Code pushed to GitHub
2. Jenkins triggered (webhook or polling)
3. Jenkins pipeline
   Checkout code
   Install dependencies
   Build Docker image
   Push image
4. Terraform provisions EC2 instance and security groups
5. Jenkins deploys the container to EC2
6. Application runs on port 3000
7. System and workload metrics are collected and visualized in Grafana dashboards

## Project Structure :

app/        - Node.js application
jenkins/    - Jenkins pipeline configuration
terraform/  - Infrastructure as Code
k8s/        - Kubernetes configuration for monitoring setup

Deployment Files
Jenkinsfile → CI/CD pipeline definition
Dockerfile → Application container build
terraform/main.tf → Infrastructure provisioning

Application Access
The application runs on EC2 via Docker:
http://15.207.106.146:3000/

Monitoring & Verification:
Grafana dashboards provide real-time visibility into CPU usage, memory consumption, and network activity
Jenkins logs are used to verify pipeline stages including build, image creation, and deployment

## Challenges Faced:

Debugging slow or failed Git pushes
Accidentally committing large Terraform provider files (~700MB)
Handling GitHub file size limitations and repository cleanup
Configuring .gitignore correctly for Terraform directories
Setting up and integrating monitoring with Grafana

Outcome

Fully functional CI/CD pipeline
Automated Docker-based deployment to AWS EC2
Application successfully running and accessible on port 3000
Monitoring dashboards implemented for observing system performance

## Conclusion

This project demonstrates practical DevOps capabilities including CI/CD pipeline design, infrastructure automation using Terraform, containerized deployments with Docker, and cloud hosting on AWS EC2.
It also reflects hands-on experience in debugging real-world issues and implementing monitoring using Grafana for better system visibility.

That’s my pipeline story — thanks for checking it out.
