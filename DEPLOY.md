# Deploy Guide

## Recommended setup

- Frontend: Vercel or Netlify
- Backend: Render, Railway, VPS, or Docker hosting
- Database: PostgreSQL for production

## Frontend environment variable

Set this on Vercel/Netlify:

```env
VITE_API_URL=https://your-backend-domain.com/api
```

## Important CORS setting on backend

Your backend `.env` should include the frontend URL:

```env
ALLOWED_ORIGINS=https://your-frontend-domain.vercel.app
```

For multiple origins:

```env
ALLOWED_ORIGINS=http://localhost:5173,https://your-frontend-domain.vercel.app
```

## Production test checklist

1. Open `/catalog` and confirm products load.
2. Open a product detail page.
3. Add item to cart.
4. Checkout with name and email.
5. Confirm order appears in `/orders`.
