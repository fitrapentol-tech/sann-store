# Deploy Guide — Sanns Store Backend

## Local check

```bash
npm install
cp .env.example .env
npm run db:push
npm run db:seed
npm run build
npm start
```

Health check:

```bash
curl http://localhost:3001/api/health
```

## Render / Railway / VPS

Recommended production database: PostgreSQL.

Set environment variables:

```env
DATABASE_URL="postgresql://USER:PASSWORD@HOST:5432/sanns_store?schema=public"
NODE_ENV=production
ALLOWED_ORIGINS=https://your-frontend-domain.com
```

Build command:

```bash
npm install && npm run build
```

Start command:

```bash
npm start
```

After the database is configured, run once:

```bash
npx prisma migrate deploy
npm run db:seed
```

## SQLite note

SQLite is fine for local development. For cloud hosts with ephemeral filesystems, use PostgreSQL.
