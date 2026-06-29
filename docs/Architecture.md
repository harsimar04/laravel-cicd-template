# Architecture

## Overview

This template provides a reusable CI/CD framework for Laravel applications using GitHub Actions and AWS EC2.

The deployment pipeline automates testing, deployment, and application validation.

---

## Architecture

```text
Developer
     │
     ▼
Git Push
     │
     ▼
GitHub Repository
     │
     ▼
GitHub Actions
     │
 SSH
     ▼
AWS EC2
     │
     ▼
Git
     │
Composer
     │
Laravel
     │
PHP-FPM
     │
Nginx
     │
     ▼
End Users
```

---

## Components

### GitHub

* Source Code
* Branch Management
* Pull Requests

### GitHub Actions

* Continuous Integration
* Continuous Deployment

### AWS EC2

Hosts the Laravel application.

### Nginx

Web server responsible for serving the Laravel application.

### PHP-FPM

Processes PHP requests.

### Laravel

Application framework.

---

## Deployment Flow

Feature Branch

↓

CI Pipeline

↓

Pull Request

↓

Merge into Staging

↓

Automatic Deployment

↓

Health Check

↓

Merge into Main

↓

Production Deployment

---

## Notes

For demonstration purposes, both the staging and production GitHub environments currently deploy to the same EC2 instance.

In production, each environment should use separate infrastructure.

