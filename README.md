# Kyusi Sunday Sketchers — Interactive Prototype

Phase 1 website prototype with the KSS 1st Anniversary event and an interactive Sketchbook.

## Sketchbook interaction

- Desktop: click previous/next, drag the page, or use keyboard arrows.
- Mobile: swipe left/right.
- The placeholder artwork lives inside the turning page, so it rotates with the page.
- Replace the placeholder artwork with real KSS sketches later.

## Current event

Fiestang Pinoy — KSS 1st Anniversary
Sunday, 4 October 2026
Racket Room Cubao
94 10th Ave, Cubao, Quezon City
Programme: 9:40 AM–12:40 PM
Capacity: 24 places

The event artwork, sketches, and documentation photos remain placeholders.

## Organiser area

The page also carries the organiser admin panel (login-gated, `#admin`) that used
to live in the separate `Sunday-Sketch` repo: budget, run-of-show, groups,
live event-day timer, and other planning content. It renders no planning data
itself — everything is fetched from Supabase only after a signed-in session
passes `is_admin()` under Row Level Security. See `supabase-schema.sql` and
`migrations/` for the backend.
