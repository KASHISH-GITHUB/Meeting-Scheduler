# Environment Setup

To fix the current issues, you need to create a `.env` file in the root directory with the following environment variables:

## Required Environment Variables

### Clerk Authentication
```
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key_here
CLERK_SECRET_KEY=your_clerk_secret_key_here
```

To get these keys:
1. Go to [Clerk Dashboard](https://dashboard.clerk.com/)
2. Create a new application or select an existing one
3. Go to API Keys section
4. Copy the Publishable Key and Secret Key

### Database
```
DATABASE_URL="postgresql://username:password@localhost:5432/scheduler_db"
```

You can use:
- **Local PostgreSQL**: Set up a local PostgreSQL database
- **Supabase**: Free PostgreSQL hosting
- **Railway**: Easy PostgreSQL deployment
- **Neon**: Serverless PostgreSQL

### Next.js (Optional)
```
NEXTAUTH_SECRET=your_nextauth_secret_here
NEXTAUTH_URL=http://localhost:3000
```

## Steps to Fix

1. Create a `.env` file in the root directory
2. Add the environment variables above
3. Replace the placeholder values with your actual keys
4. Restart the development server: `npm run dev`

## Database Setup

After setting up the DATABASE_URL:

1. Run database migrations:
   ```bash
   npx prisma migrate dev
   ```

2. Generate Prisma client:
   ```bash
   npx prisma generate
   ```

## Current Issues

The application is failing because:
1. **Missing Clerk keys**: Authentication can't initialize
2. **Missing DATABASE_URL**: Prisma can't connect to database
3. **Middleware errors**: Related to missing Clerk configuration 