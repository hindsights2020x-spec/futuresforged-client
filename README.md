# FuturesForged — Retail Client (recovery backstop)

**Status:** RECOVERY BACKSTOP captured 2026-06-21 from the live deployment
`https://ffpreview.vercel.app`. This is NOT yet the Vercel-linked canonical repo —
see "Canonicalization TODO" below.

## What this is
The live retail client is a **single-file static HTML app** (`index.html`, ~111 KB).
All other routes (`/portal`, `/chart`, …) 404 — there is no multi-page tree and no
framework build (no `_next`/`/assets`). The served root IS the source. This repo
captures it so the freshest source isn't trapped in a disposable Vercel sandbox.

## Backend
- Supabase project: `osxwkgmjwtdyvqwlfyre` (`https://osxwkgmjwtdyvqwlfyre.supabase.co`)
  - tables: `bars`, `l2_book`, `signals`, `signal_routes`, `customers`
  - L2 edge function gates the L2 panel to `elite` (Desk) / `l2_addon=true`
- Tiers: `starter` / `pro` / `elite` (=Desk); `l2_addon` boolean = $35/mo L2 unlock
- The client embeds the Supabase **publishable/anon** key (public by design).
  The **service_role** key is NOT here and must never be committed.

## Deploy (static — no build step)
Upload `index.html` to the Vercel project, or `vercel deploy` from a linked dir.
Keep the deployed URL stable — shipped desktop exes are thin shells pointing at it.

## Canonicalization TODO (must run on the machine/account that owns the Vercel project)
1. Link this repo to the `ffpreview` Vercel project (the connected MCP account has no
   teams and cannot see it — it lives in Tom's personal Vercel or the Cowork sandbox).
2. Reconcile vs the stale Drive "Retail Launch" copy (its dashboard.html is May 29).
3. Archive Retail Launch; confirm `git clone → deploy` reproduces ffpreview.
