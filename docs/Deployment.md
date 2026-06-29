# Deployment Guide

## Prerequisites

* Ubuntu EC2
* PHP
* Composer
* Nginx
* Git
* GitHub Repository

---

## CI Pipeline

Triggered on:

* feature/*
* staging
* main

Pipeline Steps

1. Checkout Repository
2. Install Dependencies
3. Generate Application Key
4. Configure Database
5. Run Migrations
6. Run Tests

---

## Staging Deployment

Triggered when code is merged into:

```
staging
```

Deployment Process

* SSH into EC2
* Pull latest code
* Composer Install
* Database Migration
* Laravel Optimization
* Reload PHP-FPM
* Reload Nginx
* Health Check

---

## Production Deployment

Triggered when code is merged into:

```
main
```

Uses the Production GitHub Environment.

Deployment steps are identical to staging.

---

## Health Validation

Endpoint:

```
GET /health
```

Deployment is considered successful only when the endpoint responds successfully.

