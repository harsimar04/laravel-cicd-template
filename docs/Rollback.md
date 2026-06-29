# Rollback Guide

## Purpose

If a deployment introduces issues, the application can be restored by deploying a previous stable commit.

## Procedure

SSH into the EC2 server.

Navigate to the application directory.

View commit history:

```bash
git log --oneline
```

Reset to a previous stable commit:

```bash
git reset --hard <commit-hash>
```

Install dependencies:

```bash
composer install
```

Optimize Laravel:

```bash
php artisan optimize
```

Reload services:

```bash
sudo systemctl reload php8.5-fpm
sudo systemctl reload nginx
```

Verify:

```
/health
```

