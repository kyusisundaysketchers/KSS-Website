# Kyusi Sunday Sketchers — Website

Public site for the KSS 1st Anniversary — Fiestang Pinoy, with an interactive Sketchbook.

## Sketchbook interaction

- Desktop: click previous/next, drag the page, or use keyboard arrows. Toggle the magnifier to inspect artwork closely.
- Mobile: swipe left/right; the magnifier works with touch too.
- The artwork lives inside the turning page, so it rotates with the page.
- Sketchbook entries without artwork yet show an editorial "Sketch coming soon" placeholder rather than a dev-looking one — drop a real image path into the `pages` array in the script to replace it.

## Confirmed event details

Fiestang Pinoy — KSS 1st Anniversary
Sunday, 4 October 2026 · 8:30 AM–12:30 PM (doors open at 8:30 AM)
Racket Room Cubao
94 10th Ave, Cubao, Quezon City
Capacity: 24 slots

Registration is not yet open. The CTA config (`REGISTRATION_URL` near the top of the public `<script>` in `index.html`) is the single place to wire up the real registration link once it exists — every `[data-cta="register"]` element updates from it.

## Organiser area

The admin panel (login-gated, budget/run-of-show/groups/live event-day timer/etc.) lives in **`admin.html`**, a separate, unlinked page — it is intentionally not reachable from the public site's navigation or footer, and carries a `noindex` meta tag. It renders no planning data itself: everything is fetched from Supabase only after a signed-in session passes `is_admin()` under Row Level Security. See `supabase-schema.sql` and `migrations/` for the backend.

Note this repo is public, so `admin.html` is technically reachable by anyone with the URL — the real access boundary is Supabase RLS, not the page being unlinked. Treat it accordingly (don't put anything sensitive directly in the markup).
