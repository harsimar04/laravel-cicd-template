# Architecture

# Overview

This project provides a reusable CI/CD template for Laravel applications using GitHub Actions.

The architecture is designed to automate code validation, staging deployments, and production deployments while following Git best practices. The deployment layer is designed to be reusable and can be configured for Hostinger Shared Hosting or any SSH-accessible Linux server.

---

# High Level Architecture

```text
                Developer
                    │
                    ▼
           Feature Branch
                    │
                    ▼
            GitHub Repository
                    │
                    ▼
           GitHub Actions (CI)
                    │
        Run Tests & Validation
                    │
                    ▼
             Staging Branch
                    │
                    ▼
      Automatic Staging Deployment
                    │
             Health Validation
                    │
                    ▼
              Main Branch
                    │
(Optional Manual Production Approval)
                    │
                    ▼
      Production Deployment
                    │
                    ▼
      Hostinger Shared Hosting
```

---

# Components

## GitHub Repository

Stores the Laravel application source code and manages the Git workflow.

Responsibilities:

* Version Control
* Branch Management
* Pull Requests

---

## GitHub Actions

Provides Continuous Integration and Continuous Deployment.

Responsibilities:

* Build
* Test
* Deployment Automation

---

## Deployment Target

The deployment target is Hostinger Shared Hosting.

The deployment mechanism uses SSH and therefore can be adapted to any Linux hosting provider supporting SSH access.

---

## Laravel Application

Handles all business logic.

Responsibilities:

* HTTP Requests
* Database Operations
* Artisan Commands
* Configuration Management

---

## Health Check Endpoint

The application exposes a simple health endpoint.

```text
GET /health
```

This endpoint is used to verify that deployments complete successfully.

---

# Branch Strategy

```text
feature/*
        │
        ▼
GitHub Actions CI
        │
        ▼
staging
        │
Automatic Deployment
        │
        ▼
main
        │
(Optional Approval)
        ▼
Production Deployment
```

---

# Deployment Process

1. Developer pushes changes.
2. CI pipeline executes automatically.
3. Tests are executed.
4. Code is merged into the staging branch.
5. Staging deployment starts automatically.
6. Health endpoint is validated.
7. Code is merged into the main branch.
8. Production deployment is triggered.
9. (Optional) Manual approval can be configured using GitHub Environments.

---

# Security

The template does not store deployment credentials in the repository.

Sensitive values are managed through GitHub Secrets.

Examples:

* DEPLOY_HOST
* DEPLOY_USER
* DEPLOY_SSH_KEY
* DEPLOY_PATH
* APP_URL

---

# Design Goals

* Reusable
* Hosting Provider Independent
* GitHub Native
* Secure Secret Management
* Easy to Extend
* Production Ready

