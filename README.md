# Kyusi Sunday Sketchers — Website

Public site for KSS Vol. 8 — Alamat, Katha, at Likha (the KSS 1st Anniversary), with an interactive Sketchbook.

## Sketchbook interaction

- Desktop: click previous/next, drag the page, or use keyboard arrows. Toggle the magnifier to inspect artwork closely.
- Mobile: swipe left/right; the magnifier works with touch too.
- The artwork lives inside the turning page, so it rotates with the page.
- Sketchbook entries without artwork yet show an editorial "Sketch coming soon" placeholder rather than a dev-looking one — drop a real image path into the `pages` array in the script to replace it.

## Confirmed event details

KSS Vol. 8 — Alamat, Katha, at Likha (KSS 1st Anniversary)
Sunday, 4 October 2026 · 8:30 AM–12:30 PM (doors open at 8:30 AM)
Racket Room Cubao
94 10th Ave, Cubao, Quezon City
Capacity: 24 slots
Registration: ₱1,000 per person
Three rotating stations: Tala, Sitan, Bathala

Food is not included. Coffee is still under discussion and is deliberately not
advertised anywhere on the site until it is confirmed.

Registration is not yet open. The CTA config (`REGISTRATION_URL` near the top of the public `<script>` in `index.html`) is the single place to wire up the real registration link once it exists — every `[data-cta="register"]` element updates from it.

## Organiser area

There is currently no organiser/admin interface deployed on this site. It previously lived in a separate `admin.html` (unlinked from the public nav, `noindex`), but that's been removed for now so the public repo and deployed Pages site are 100% public-facing — being unlinked isn't real access control on a public repo, and it doesn't need to exist here while it's unused.

`supabase-schema.sql` and `migrations/` remain as the backend reference (tables + `is_admin()` Row Level Security policies) for whenever the organiser interface is reintroduced — most likely as a separate, privately-deployed app rather than a page in this public repo.
