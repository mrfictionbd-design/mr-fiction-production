# MR. FICTION — Production Storefront

Dark luxury streetwear storefront for Bangladesh.

## Stack
- Static frontend optimized for Vercel
- Supabase Auth + database
- Supabase Edge Function checkout
- GitHub → Vercel deployment workflow

## Local
Open `index.html` with a local static server.

## Environment
The current Supabase project URL and public anon key are configured in the frontend. For a stricter production architecture, move public configuration into build-time environment variables and keep all secrets server-side.

## Deployment
Pushes to `main` are intended to create production deployments once this repository is connected to Vercel.

## Deployment status
GitHub is linked to the MR. FICTION Vercel project. Pushes to `main` trigger automatic deployments.
