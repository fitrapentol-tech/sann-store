# Sanns Store Fullstack

This ZIP contains:

- `sanns-store-frontend`: React + Vite + TypeScript + Tailwind storefront
- `sanns-store-backend`: Express + TypeScript + Prisma API

## Local quick start

Backend:

```bash
cd sanns-store-backend
npm install
cp .env.example .env
npm run db:generate
npm run db:push
npm run db:seed
npm run dev
```

Frontend:

```bash
cd sanns-store-frontend
npm install
cp .env.example .env
npm run dev
```

Open http://localhost:5173.

## Deploy

- Frontend: Vercel or Netlify
- Backend: Render, Railway, Docker, or VPS

Set `VITE_API_URL` in the frontend to your backend URL plus `/api`.
Set `ALLOWED_ORIGINS` in the backend to your frontend URL.
