# Laravel CI/CD Template

## Overview

This repository provides a reusable CI/CD template for Laravel applications using GitHub Actions.

The template automates testing, deployment, and production releases while following Git best practices and a pull request based workflow.

Although the template is designed to support Hostinger Shared Hosting, it can also be adapted to any SSH-accessible Linux server by updating the deployment configuration.

---

# Features

* GitHub Actions Continuous Integration
* Automated Staging Deployment
* Automated Production Deployment
* Pull Request Workflow
* Branch Protection Ready
* Manual Production Approval Support (GitHub Environments)
* Health Check Endpoint
* Laravel Optimization
* Reusable Deployment Template
* Deployment Documentation
* Rollback Guide

---

# Branch Strategy

```
feature/*
      │
      ▼
GitHub Actions CI
      │
      ▼
staging
      │
Automatic Staging Deployment
      │
      ▼
main
      │
(Optional Manual Approval)
      │
      ▼
Production Deployment
```

---

# Deployment Workflow

1. Developer pushes code.
2. GitHub Actions executes the CI pipeline.
3. Tests are executed.
4. Code is merged into the staging branch.
5. Staging deployment begins automatically.
6. Application health is validated.
7. Code is merged into the main branch.
8. Production deployment begins.
9. (Optional) Manual approval can be enabled using GitHub Environments.

---

# Deployment Target

The template is configured for:

* Hostinger Shared Hosting (SSH Recommended)

The deployment layer is generic and can also be adapted for any SSH-accessible Linux hosting provider by updating the deployment secrets.

---

# GitHub Secrets

Required Secrets

```
DEPLOY_HOST
DEPLOY_USER
DEPLOY_SSH_KEY
DEPLOY_PATH
APP_URL
```

---

# Repository Structure

```
.github/
    workflows/

docs/

app/
bootstrap/
config/
database/
public/
resources/
routes/
storage/
tests/
```

---

# Health Check

Endpoint

```
GET /health
```

Example Response

```json
{
    "status": "ok"
}
```

---

# Manual Production Approval

The workflow supports manual approval before production deployment using GitHub Environments.

Configure the Production environment in GitHub and assign required reviewers if your organization requires deployment approval.

---

# Documentation

Additional documentation is available in the **docs/** directory.

* Architecture
* Deployment
* GitHub Setup
* Hostinger Deployment
* Rollback
* Standard Operating Procedure

---

# Requirements

* PHP 8.3+
* Composer
* Git
* Laravel
* GitHub Actions
* SSH Access (Recommended)

---

# License

MIT License

