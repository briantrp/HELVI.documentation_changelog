# 02. First Run & Initialization

Once your containers are running, Collabase requires a one-time initialization to set up the database and create your root administrator account.

## Step 1: Access the Setup Wizard
Open your browser and navigate to:
`http://your-server-ip:3000`

The **Lifecycle Guard** will detect that the system is uninitialized and automatically redirect you to the **Setup Wizard**.

## Step 2: Database Initialization
1. You will see the **"Welcome to Collabase"** screen.
2. Click **"Initialize System"**.
3. A terminal-style console will appear on the screen. It will stream the live output of `prisma migrate deploy` as it builds your database schema.
4. Wait for the green "Success" message.

## Step 3: Security Onboarding (Admin Creation)
Once the database is ready, the system will transition to the **Onboarding** view.
1. Enter your **Name**.
2. Enter your **Email** (this will be your login username).
3. Choose a **Secure Password** (minimum 8 characters).
4. Enter an **Application Title** (e.g., "Company Knowledge Base").

## Step 4: Completion
Click **"Finalize Setup"**. You will be redirected to the login page. Use your new credentials to log in.

The system is now in `READY` state and fully operational.
