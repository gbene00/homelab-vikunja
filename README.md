# **Homelab Vikunja**

This repository contains the full GitOps-driven Kubernetes platform for my personal homelab, running on Azure Kubernetes Service. The cluster and all workloads are fully managed declaratively using FluxCD, ensuring reproducibility, security, and automated reconciliation of the entire stack.
I have chosen the Vikunja, because it's an open-source task and project management application designed to help stay organized and productive.

## **What This Repository Includes**

### **GitOps Platform (FluxCD)**

 - Automated deployment and reconciliation of all cluster resources
 - Git as the single source of truth
 - Declarative definitions for applications, infrastructure components, CRDs, and secrets

### **Security & Secrets**

 - Integrated Azure Key Vault for application secrets
 - Secrets mounted via Secrets Store CSI Driver
 - Sensitive information encrypted with SOPS & AGE keys

### **Networking & Ingress**

 - Nginx Ingress Controller deployed via HelmRelease
 - Fully automated TLS certificates using Cert-Manager & Let’s Encrypt
 - HTTPS for all exposed services
      - Vikunja
      - Prometheus
      - Grafana

### **Monitoring & Observability**

 - kube-prometheus-stack (Prometheus & Grafana)
 - Ingress exposure for Grafana & Prometheus

### **Applications**

 - Vikunja (task management app) deployed with:
     - Postgres StatefulSet
     - Key Vault–backed secrets
     - HTTPS ingress and domain configuration

### **Infrastructure (Terraform-driven)**

 - Azure resources:
     - AKS cluster
     - Storage account + Blob containers
     - Key Vault

### **Automated Dependency Updates (Renovate)**

 - Renovate scans the repository and automatically creates pull requests for:
     - New container image versions
     - Updated Helm charts
     - Ensures the cluster stays up to date safely, with manual PR approval

### **Backup**

 - Velero integrated with Azure Blob Storage
 - Restic NodeAgent for persistent volume backups
 - Kubernetes object & PVC backups
 - Weekly Velero schedules
