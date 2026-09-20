<h1 align="center">Hamza Alsoodani</h1>

<p align="center">DevOps Engineer | Platform Engineer | Cloud Engineer</p>

<p align="center">London, UK</p>

I focus on AWS infrastructure defined in Terraform, secure CI/CD with GitHub Actions and OIDC, and container platforms on ECS Fargate and Kubernetes. My work centres on private networking, keyless authentication and automated delivery, with security scanning and health checks built into the pipeline.

I hold a degree in Computer Science from Queen Mary University of London. I've delivered two production-style platforms, a Gatus monitoring service on ECS Fargate and a GitOps-driven deployment on EKS, both described below.

## Projects

### [Gatus on ECS Fargate](https://github.com/HamzaAlsoodani/ecs-gatus-project)

A Gatus monitoring service on AWS ECS Fargate, served over HTTPS on a custom domain. The infrastructure is written in Terraform as five reusable modules (VPC, ECR, ALB, ECS and ACM), with remote state in S3.

- Tasks run in private subnets across two Availability Zones with no public IPs. Traffic enters through an HTTPS Application Load Balancer, and the containers accept port 8080 only from the load balancer's security group.
- GitHub Actions authenticates to AWS with OIDC, which removes long-lived access keys from the pipeline. Three workflows handle the image build and push to ECR, Terraform deployment and controlled teardown.
- Every release is checked against the live endpoint, and the pipeline fails unless it returns HTTP 200.
- A multi-stage build on a scratch base reduced the image from 69.5MB to 13.2MB, an 81% reduction.

### [Gatus on EKS](https://github.com/HamzaAlsoodani/EKS-Project)

The same service on Kubernetes, running on AWS EKS. The cluster, VPC and node groups are reusable Terraform modules, with state in S3 and locking in DynamoDB. Worker nodes sit in private subnets behind NGINX Ingress on a Network Load Balancer.

- ArgoCD deploys from Git and reverts any drift between the cluster and the repository.
- ExternalDNS and cert-manager automate DNS records and Let's Encrypt certificates through Route 53.
- Pods receive scoped AWS permissions through IRSA, with no static credentials.
- The pipelines run Checkov and TFLint against the Terraform, and a Trivy scan on the Docker image before it is pushed to ECR.
- Prometheus and Grafana provide cluster metrics. The image size fell from 223MB to 18MB.

## Tech stack

<p align="center">
  <img src="https://api.iconify.design/fa6-brands/aws.svg?color=%23FF9900" alt="AWS" title="AWS" height="42" />
  <img src="https://cdn.simpleicons.org/terraform/7B42BC" alt="Terraform" title="Terraform" height="42" />
  <img src="https://cdn.simpleicons.org/docker/2496ED" alt="Docker" title="Docker" height="42" />
  <img src="https://cdn.simpleicons.org/kubernetes/326CE5" alt="Kubernetes" title="Kubernetes" height="42" />
  <img src="https://cdn.simpleicons.org/helm/4F5BD5" alt="Helm" title="Helm" height="42" />
  <img src="https://cdn.simpleicons.org/argo/EF7B4D" alt="ArgoCD" title="ArgoCD" height="42" />
  <img src="https://cdn.simpleicons.org/githubactions/2088FF" alt="GitHub Actions" title="GitHub Actions" height="42" />
  <img src="https://cdn.simpleicons.org/prometheus/E6522C" alt="Prometheus" title="Prometheus" height="42" />
  <img src="https://cdn.simpleicons.org/grafana/F46800" alt="Grafana" title="Grafana" height="42" />
  <img src="https://cdn.simpleicons.org/nginx/009639" alt="NGINX" title="NGINX" height="42" />
  <img src="https://cdn.simpleicons.org/linux/FCC624" alt="Linux" title="Linux" height="42" />
  <img src="https://cdn.simpleicons.org/gnubash/4EAA25" alt="Bash" title="Bash" height="42" />
  <img src="https://cdn.simpleicons.org/python/3776AB" alt="Python" title="Python" height="42" />
  <img src="https://cdn.simpleicons.org/git/F05032" alt="Git" title="Git" height="42" />
</p>

## Contact

[alsoodanihamza6@gmail.com](mailto:alsoodanihamza6@gmail.com) | [hamza-alsoodani.com](https://hamza-alsoodani.com)
