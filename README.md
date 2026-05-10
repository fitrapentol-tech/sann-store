# Sanns Store Frontend

Luxury e-commerce storefront built with React, Vite, TypeScript, Tailwind CSS, Zustand, and React Router.

## Quick Start

```bash
npm install
cp .env.example .env
npm run dev
```

Open http://localhost:5173.

## Connect to Backend

Make sure the backend is running on http://localhost:3001. The default API URL is:

```env
VITE_API_URL=http://localhost:3001/api
```

For production, replace it with your deployed backend URL:

```env
VITE_API_URL=https://your-backend.onrender.com/api
```

## Build

```bash
npm run build
npm run preview
```

The production output is in `dist`.

## Pages

- `/` - home page
- `/catalog` - catalog with search, filter, and sort
- `/products/:id` - product detail
- `/checkout` - checkout flow
- `/orders` - order lookup by email

## Deployment

### Vercel

1. Import this folder as a Vercel project.
2. Set Environment Variable: `VITE_API_URL=https://your-backend-url/api`
3. Deploy.

### Netlify

1. Import this folder.
2. Build command: `npm run build`
3. Publish directory: `dist`
4. Set Environment Variable: `VITE_API_URL=https://your-backend-url/api`

### Docker

```bash
docker build -t sanns-store-frontend .
docker run -p 8080:80 sanns-store-frontend
```

## Notes

If the backend is offline, product listing falls back to mock data so the UI can still be previewed.
