# Deploying Sauki Don Al'umma (DigitalOcean App Platform) - Quick Guide

## Overview
This guide shows how to deploy the app (frontend + backend) to DigitalOcean App Platform using your GitHub repo or by uploading this ZIP.

## 1) Prepare repo
1. Unzip the package locally.
2. `git init` -> `git add .` -> `git commit -m "Initial sauki deploy"`
3. Create a GitHub repo and `git remote add origin <your-repo-url>` then `git push -u origin main`.

## 2) Create a Managed MySQL Database (DigitalOcean)
1. In DigitalOcean dashboard -> Databases -> Create -> MySQL
2. Choose a small plan (db-s-1vcpu-1gb recommended)
3. Create database and note the connection string (user, password, host, port, database)

## 3) Create App (App Platform)
1. DigitalOcean -> Apps -> Create App
2. Connect your GitHub repo and select the repo branch (main)
3. App Platform will detect services. Configure two components:
   - Frontend: `frontend` directory (build command: `npm install && npm run build`, run command: `npm run preview`)
   - Backend: `backend` directory (start command: `npm install && npm run start`), port: 4000
4. In App settings -> Environment Variables paste values from `.env.example` replacing placeholders with real values (MYSQL_* from step 2 and VTPASS test keys are already set in .env.example)
5. Add Managed Database resource if not already created and link to the app (or paste MYSQL_* values)

## 4) Migrations
The backend runs simple SQL migrations on startup if it can connect to MySQL. Make sure the DB user has permission to create tables.

## 5) Deploy & Test
1. Click Deploy. Wait 2-5 minutes for build & deploy.
2. Visit the frontend URL (e.g. https://<your-app>.ondigitalocean.app)
3. Register a user, test buying (sandbox VTPASS), and verify wallet & commission flows.

## Admin credentials (default)
- Email: admin@sauki.com
- Phone: 08000000000
- Password: Sauki12345
(Please change immediately after first login — you can update via SQL or admin UI)
