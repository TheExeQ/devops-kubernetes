# DevOps Kubernetes Deployment

This repository contains Kubernetes deployment configuration for managing application infrastructure using Helm and ArgoCD.

The project demonstrates a GitOps-driven approach to deploying and managing services on Kubernetes, with infrastructure defined as version-controlled, declarative manifests.

## Overview

The deployment setup handles core infrastructure concerns such as:

- Packaging Kubernetes resources into a reusable Helm chart
- Managing application and database deployments declaratively
- Automating delivery through ArgoCD GitOps workflows
- Handling persistent storage and internal service networking

This keeps deployments consistent, reduces manual intervention, and ensures every change is traceable through Git.

## Project structure

```
devops-kubernetes/
├── argocd/          # ArgoCD application manifests
└── helm/            # Helm chart for the deployment
```

## Technologies

- **Kubernetes** - Container orchestration platform
- **Helm** - Package manager for templated manifests
- **ArgoCD** - GitOps continuous delivery
- **PostgreSQL** - Database backend
- **GitHub Container Registry** - Container image hosting

## Quick start

### Prerequisites

- A running Kubernetes cluster
- Helm 3.x installed
- ArgoCD installed in the cluster

```bash
helm repo add argo https://argoproj.github.io/argo-helm
helm install argocd argo/argo-cd --namespace argocd --create-namespace
```

### Deploy

```bash
kubectl apply -f argocd/applications/
```

Or install directly with Helm:

```bash
helm install books-app ./helm/books-app
```

## Configuration

Default values are defined in the Helm chart's `values.yaml`. Override at install time as needed:

```bash
helm install books-app ./helm/books-app --set replicaCount=5
```

## Goals

- Provide a reusable Kubernetes infrastructure-as-code setup
- Demonstrate GitOps deployment with ArgoCD
- Keep the configuration easy to extend without heavy maintenance
