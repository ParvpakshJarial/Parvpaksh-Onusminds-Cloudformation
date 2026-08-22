# OnusMinds Cloudformation Pvt. Ltd. — Corporate Website

Full-stack corporate website: React frontend + FastAPI backend + MongoDB.

## What's inside
- `frontend/` — React app (pages, admin panel, animations)
- `backend/` — FastAPI server (forms, news CMS, site content, auth, activity log)

## Run locally

### 1. Requirements
- Node.js 18+ with yarn (`npm install -g yarn`)
- Python 3.10+
- MongoDB running locally (or a free MongoDB Atlas connection string)

### 2. Backend
```bash
cd backend
python3 -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env            # then edit .env (see notes below)
uvicorn server:app --host 0.0.0.0 --port 8001 --reload
```
Backend runs on http://localhost:8001 (API: http://localhost:8001/api)

### 3. Frontend
```bash
cd frontend
cp .env.example .env            # points to http://localhost:8001 already
yarn install
yarn start
```
Website opens on http://localhost:3000 — admin panel at http://localhost:3000/admin

## .env notes (backend/.env)
- `MONGO_URL` — local: `mongodb://localhost:27017` or your Atlas string
- `JWT_SECRET` — any long random string
- `ADMIN_EMAIL` / `ADMIN_PASSWORD` — the owner account is auto-created on first run
- Email + storage keys are hosted services; keep them as-is while they're active

## Default owner logins (auto-created on first run)
- piyushjarial0307@gmail.com / Piyush@#@112301
- (Parvpaksh and Sunny accounts exist in the live database; recreate them via Team access)

## Deploy
- Static hosting: `cd frontend && yarn build` → upload `build/` (+ keep `public/.htaccess` for routing)
- VPS: see the VPS package guide (STEP_BY_STEP.md in the VPS zip)
