# **Homelab Vikunja**

This repository contains the full GitOps-driven Kubernetes platform for my personal homelab, running on Azure Kubernetes Service. The cluster and all workloads are fully managed declaratively using FluxCD, ensuring reproducibility, security, and automated reconciliation of the entire stack.

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
 - HTTPS for all exposed services (Grafana, Prometheus, Vikunja

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
