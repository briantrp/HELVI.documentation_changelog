# 01. Installation Guide

This guide ensures a smooth installation of Collabase v0.10.4-beta using Docker.

## Prerequisites
- Docker and Docker Compose installed on the host machine.
- A domain name or public IP address mapped to your server.

## Step 1: Prepare the Environment
1. Create a directory for your Collabase installation:
   ```bash
   mkdir collabase && cd collabase
   ```
2. Copy the files from the `deploy-template` folder into your new `collabase` directory.
3. Initialize the persistence layers and environment:
   ```bash
   ./migrate-data.sh
   ```
   *This script creates the necessary volume folders (`collabase_data`, `db_data`, `shared-home`) with correct permissions.*

## Step 2: Configure Secrets
Edit the `.env` file created by the script:
```bash
nano .env
```
- **NEXTAUTH_SECRET**: Set this to a long, random string.
- **DATABASE_URL**: Ensure this matches your server's needs (default works out of the box).
- **NEXTAUTH_URL**: Change `http://localhost:3000` to your actual server IP or Domain.

## Step 3: Launch
Start the application and database:
```bash
docker compose up -d
```

Your system is now booting. Proceed to the **First Run Guide** to initialize the database.
