# Laravel CI/CD Template

## Overview

This repository provides a reusable CI/CD template for Laravel applications using GitHub Actions and AWS EC2.

The project demonstrates a complete deployment workflow, including continuous integration, automated deployments, health validation, and environment-based deployments.

---

## Features

* GitHub Actions Continuous Integration
* GitHub Actions Continuous Deployment
* AWS EC2 Deployment
* Nginx + PHP-FPM
* Composer Dependency Installation
* Laravel Database Migration
* Laravel Optimization
* Health Check Endpoint (`/health`)
* Branch-based Deployment Strategy
* GitHub Environments
* SSH-based Deployment

---

## Branch Strategy

```
feature/*
      │
      ▼
GitHub Actions CI
      │
      ▼
staging
      │
      ▼
Automatic Deployment
      │
      ▼
main
      │
      ▼
Production Deployment
```

---

## Deployment Flow

1. Push code
2. GitHub Actions starts
3. Connect to EC2 over SSH
4. Pull latest code
5. Install Composer dependencies
6. Run migrations
7. Optimize Laravel
8. Reload PHP-FPM
9. Reload Nginx
10. Verify `/health`

---

## Server Stack

* Ubuntu 26.04
* Nginx
* PHP 8.5
* Composer
* Laravel
* GitHub Actions

---

## GitHub Environments

This template includes two deployment environments:

* staging
* production

For demonstration purposes, both environments currently deploy to the same EC2 instance. In a production setup, these environments should use separate infrastructure and independent GitHub Environment secrets.

---

## Required GitHub Secrets

Repository / Environment secrets:

* EC2_HOST
* EC2_USER
* EC2_SSH_KEY

---

## Health Endpoint

```
GET /health
```

Expected response:

```json
{
  "status": "ok"
}
```

---

## Project Structure

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

## Documentation

Additional documentation is available in the `docs` directory.

* Architecture
* Deployment
* Rollback
* SOP

---

## License

MIT

