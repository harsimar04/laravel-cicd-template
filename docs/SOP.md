# Standard Operating Procedure

## Development Workflow

1. Create a feature branch.
2. Develop the feature.
3. Push changes.
4. Verify CI passes.
5. Open a Pull Request.
6. Merge into `staging`.
7. Validate deployment.
8. Merge into `main`.
9. Production deployment starts automatically.

---

## Deployment Verification

Confirm:

* GitHub Actions completed successfully.
* Laravel application is accessible.
* `/health` returns HTTP 200.
* Nginx is running.
* PHP-FPM is running.

---

## Troubleshooting

### Deployment Failed

Check:

* GitHub Actions logs
* Nginx logs
* Laravel logs

### SSH Failure

Verify:

* EC2 is running.
* SSH key is valid.
* GitHub Secrets are configured.

### Health Check Failure

Verify:

* Laravel is running.
* PHP-FPM is active.
* Nginx is active.
* `/health` endpoint is accessible.

