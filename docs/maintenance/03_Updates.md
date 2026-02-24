# 03. Updates & Database Management

Collabase features a self-healing update mechanism that ensures your data is safe while the system evolves.

## How to Update Collabase
To update to a newer version:
1. Navigate to your installation folder.
2. Update the image version in `docker-compose.yml` or simply pull the latest if using tags:
   ```bash
   docker compose pull
   docker compose up -d
   ```

## Standardized Database Migrations
Collabase uses **Prisma Migrations** to manage database changes.

### Automated Updates
On every boot, the application checks if the database matches the current code requirements.
- **If new tables are needed**: The system will automatically detect the **PENDING_UPDATE** state.
- **Data Safety**: Migrations add new tables or columns. They **never delete** your existing data.

### The Update Experience
If you update to a version that requires manual confirmation:
1. Users will see a **"Maintenance Required"** screen.
2. You (as Admin) click **"Apply System Update"**.
3. The system streams the migration logs to your browser.
4. Once finished, the system returns to `READY` state and users are allowed back in.

## Backups
Your data lives in the host folders created during installation:
- `./db_data`: The raw Postgres database files.
- `./collabase_data`: User uploads and attachments.
- `./shared-home`: Configuration and cache.

**CRITICAL**: Always back up these directories before performing a major version update.
