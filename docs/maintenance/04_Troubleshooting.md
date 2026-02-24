# 04. Troubleshooting & Health Checks

Collabase is designed to catch and report errors before they cause data issues. Here is how to diagnose common problems.

## 1. Connection Lost Overlay
If you see a black screen saying **"Connection Lost"**:
- **Cause**: The application cannot talk to the Postgres database.
- **Solution**: 
  - Check if the database container is running: `docker ps`.
  - Check database logs: `docker compose logs db`.
  - Ensure the `DATABASE_URL` in your `.env` is correct.

## 2. Logs & Diagnostics
To see what the application is doing in real-time:
```bash
docker compose logs -f app
```

### Checking the Health Endpoint
Collabase has a built-in health check used by Docker. You can check it manually:
```bash
curl http://localhost:3000/api/health
```
- **200 OK**: The system is `READY` and healthy.
- **503 Service Unavailable**: The system is in a setup or update state (normal during first run).

## 3. Container Management
- **Restart everything**: `docker compose restart`.
- **Hard reset (Keep data)**: `docker compose down && docker compose up -d`.
- **Rebuild image**: Should typically not be needed for customers, but can be done with `docker compose up -d --build`.

## 4. Permission Errors
If the application cannot write files (e.g., uploads fail):
- Ensure the `collabase_data` and `shared-home` folders on the host are writable by the user running Docker.
- Re-run `./migrate-data.sh` to fix permissions.
