# Rollback Guide

# Overview

This document describes the recommended rollback procedure for deployments using this Laravel CI/CD template.

The deployment workflow is intentionally designed to use Git-based rollbacks instead of maintaining filesystem backups, making the template reusable across different hosting providers.

---

# When to Roll Back

Rollback should be considered when:

* A deployment fails.
* Critical application errors are detected.
* Database changes are incompatible.
* Health checks fail after deployment.
* A production issue requires reverting to the last stable release.

---

# Rollback Procedure

## Step 1

Connect to the deployment server using SSH.

---

## Step 2

Navigate to the Laravel application directory.

```bash
cd /path/to/laravel/project
```

---

## Step 3

View the Git commit history.

```bash
git log --oneline
```

Locate the last known stable commit.

---

## Step 4

Reset the repository to the desired commit.

```bash
git reset --hard <commit_hash>
```

Replace `<commit_hash>` with the selected commit ID.

---

## Step 5

Install Composer dependencies.

```bash
composer install --no-dev --prefer-dist --optimize-autoloader
```

---

## Step 6

Run database migrations if required.

```bash
php artisan migrate --force
```

---

## Step 7

Optimize the Laravel application.

```bash
php artisan optimize
```

---

## Step 8

Verify the deployment.

Example:

```text
GET /health
```

The application should return HTTP 200.

---

# Rollback Checklist

* Previous stable commit identified
* Repository successfully reset
* Composer dependencies installed
* Laravel optimized
* Health endpoint responding successfully

---

# Notes

This template intentionally avoids automatic filesystem backups because backup strategies differ between hosting providers.

Git-based rollback provides a simple, reusable, and provider-independent rollback mechanism suitable for reusable CI/CD templates.

