# Fix Vercel Build — Prerender & Tiptap CSS Crash

## Context

Vercel build failed with:
1. Meeting page crash: ENOENT for Tiptap `default-stylesheet.css` during prerender
2. 9 dashboard routes error on "Dynamic server usage" with headers()

## Fix

Add `export const dynamic = 'force-dynamic'` to `src/app/(dashboard)/layout.tsx`
— all dashboard routes are authenticated so they can never be static.

## Verification

- tsc --noEmit zero errors
- vitest run 193 passing
- Vercel build succeeds
