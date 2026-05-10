# Sanns Store — Full-Stack E-Commerce Prototype

> A luxury e-commerce prototype built with React + Vite (frontend) and Node.js + Express + Prisma (backend).

---

## Project Structure

```
sanns-store/
├── sanns-store-frontend/   ← Vite + React + TypeScript + Tailwind + Zustand
└── sanns-store-backend/    ← Node.js + Express + TypeScript + Prisma (SQLite)
```

---

## Prerequisites

| Tool | Version |
|------|---------|
| Node.js | ≥ 18.x |
| npm | ≥ 9.x |

---

## Quick Start (Both Together)

Open **two terminal windows** and follow the steps below.

---

## Backend Setup

```bash
cd sanns-store-backend

# 1. Install dependencies
npm install

# 2. Create environment file
cp .env.example .env
# Edit .env if needed (default SQLite requires no changes)

# 3. Generate Prisma client
npx prisma generate

# 4. Push schema to database (creates dev.db)
npx prisma db push

# 5. Seed the database with 8 sample products
npx ts-node prisma/seed.ts

# 6. Start the dev server
npm run dev
```

The API will be available at: **http://localhost:3001**

**One-liner (steps 1–5):**
```bash
npm install && npx prisma generate && npx prisma db push && npx ts-node prisma/seed.ts
```

### API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/health` | Health check |
| GET | `/api/products` | All products |
| GET | `/api/products?category=accessories` | Filter by category |
| GET | `/api/products/featured` | Featured products |
| GET | `/api/products/:id` | Single product |
| POST | `/api/products` | Create product |
| PATCH | `/api/products/:id` | Update product |
| DELETE | `/api/products/:id` | Delete product |
| POST | `/api/orders` | Create order |
| GET | `/api/orders/:id` | Get order by ID |
| GET | `/api/orders?email=...` | Orders by email |
| PATCH | `/api/orders/:id/status` | Update order status |

### Create Order — Example Payload

```json
POST /api/orders
{
  "customerName": "Jane Doe",
  "customerEmail": "jane@example.com",
  "items": [
    { "productId": "clxxx...", "quantity": 1 },
    { "productId": "clyyy...", "quantity": 2 }
  ]
}
```

---

## Frontend Setup

```bash
cd sanns-store-frontend

# 1. Install dependencies
npm install

# 2. (Optional) Set API URL if backend runs on a different port
# Create a .env file:
echo "VITE_API_URL=http://localhost:3001/api" > .env

# 3. Start the dev server
npm run dev
```

The app will be available at: **http://localhost:5173**

> **Note:** The frontend includes **mock data fallback**. If the backend is not running, the app will still work with 8 sample products loaded from `src/services/api.ts`.

---

## Features

### Frontend
- **Dark / Light mode** — persisted in localStorage via Zustand
- **Responsive design** — mobile-first with Tailwind CSS
- **Cart** — slide-in drawer, quantity controls, persisted across sessions
- **Product pages** — hero, catalog with filters/search/sort, detail view
- **Animations** — staggered entrance, hover effects, smooth transitions
- **API + Fallback** — gracefully uses mock data when backend is offline

### Backend
- **RESTful API** with Express + TypeScript
- **Prisma ORM** with SQLite (zero-config) or PostgreSQL
- **CORS** configured for the frontend origin
- **Input validation** and structured error responses
- **Stock management** — auto-decrements on order creation (transactional)
- **Request logging** with Morgan

---

## Design System

| Token | Dark Mode | Light Mode |
|-------|-----------|------------|
| Background | `#0c0a08` | `#faf8f4` |
| Card | `#181614` | `#ffffff` |
| Text | `#f0ede6` | `#0c0a08` |
| Accent (Gold) | `#c4a35a` | `#c4a35a` |
| Border | `#2a2520` | `#e0dbd0` |

**Fonts:** Cormorant Garamond (display) + DM Sans (body)

---

## Production Build

### Frontend
```bash
cd sanns-store-frontend
npm run build
# Output in ./dist — deploy to Vercel, Netlify, etc.
```

### Backend
```bash
cd sanns-store-backend
npm run build
# Compiled to ./dist
npm start
```

---

## Switching to PostgreSQL

1. Edit `sanns-store-backend/prisma/schema.prisma`:
   ```prisma
   datasource db {
     provider = "postgresql"
     url      = env("DATABASE_URL")
   }
   ```

2. Update `.env`:
   ```
   DATABASE_URL="postgresql://USER:PASSWORD@HOST:5432/sanns_store"
   ```

3. Re-run migrations:
   ```bash
   npx prisma migrate dev --name init
   npx ts-node prisma/seed.ts
   ```

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend Framework | React 18 + Vite |
| Language | TypeScript |
| Styling | Tailwind CSS |
| State | Zustand (with persistence) |
| Routing | React Router v6 |
| HTTP Client | Axios |
| Icons | Lucide React |
| Backend | Node.js + Express |
| ORM | Prisma |
| Database | SQLite (dev) / PostgreSQL (prod) |
| Fonts | Google Fonts |

---

*Built with care for the extraordinary. — Sanns Store*
