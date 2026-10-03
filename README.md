# Kyusi Sunday Sketchers — Website

Public site for KSS Vol. 8 — Alamat, Katha, at Likha (the KSS 1st Anniversary), with an interactive Sketchbook.

## Sketchbook interaction

- Desktop: click previous/next, drag the page, or use keyboard arrows. Toggle the magnifier to inspect artwork closely.
- Mobile: swipe left/right; the magnifier works with touch too.
- The artwork lives inside the turning page, so it rotates with the page.
- Sketchbook entries without artwork yet show an editorial "Sketch coming soon" placeholder rather than a dev-looking one — drop a real image path into the `pages` array in the script to replace it.

## Confirmed event details

KSS Vol. 8 — Alamat, Katha, at Likha (KSS 1st Anniversary)
Sunday, 4 October 2026 · 9:00 AM–1:00 PM (attendees asked to arrive early or on time)
Racket Room Collective, Cubao
94 10th Ave, Cubao, Quezon City
Capacity: 24 slots
Registration: ₱1,000 per person
Three rotating stations: A Lakapati (God of Agriculture), B Sitan (God of Death, nude, 18+), C Bathala (The Supreme God)

Light snacks and drinking water are provided; attendees may bring their own food.

Registration: limited slots; CTAs read "Limited slots only" and point to #register (enquiries via Instagram). After the event, switch the Registration section to "registration closed — thank you for joining us". The CTA config (`REGISTRATION_URL` near the top of the public `<script>` in `index.html`) is the single place to wire up the real registration link once it exists — every `[data-cta="register"]` element updates from it.

## Organiser area

There is currently no organiser/admin interface deployed on this site. It previously lived in a separate `admin.html` (unlinked from the public nav, `noindex`), but that's been removed for now so the public repo and deployed Pages site are 100% public-facing — being unlinked isn't real access control on a public repo, and it doesn't need to exist here while it's unused.

`supabase-schema.sql` and `migrations/` remain as the backend reference (tables + `is_admin()` Row Level Security policies) for whenever the organiser interface is reintroduced — most likely as a separate, privately-deployed app rather than a page in this public repo.

## Event-day check-in (`check-in/`)

`check-in/index.html` is the organisers' door check-in for Vol. 8. It is not linked from the site and is marked `noindex`. It needs no backend:

- At the door, open `/check-in/` and choose the attendee CSV (`handle, alt_handle, display_name, email, phone, party_key`). The file is read in the browser only. Emails and phone numbers are dropped on load and never stored or shown.
- **Setup link (no file needed):** `/check-in/#list=<base64url of the CSV>` loads the list on open. The part after `#` is never sent to the server, so the list only lives in the link the organisers share privately. The page removes it from the address bar after loading, and opening it again keeps existing check-ins. Generate it locally; never commit it.
- Search by name, handle or alt handle (a leading `@` is ignored). Select one or more people and check them in. Party members (same `party_key`) are pre-selected together.
- Each colour starts at a station, matching the event map: Cyan → A Lakapati, Red → B Sitan, Orange → C Bathala. Everyone still rotates through all three.
- Attendees can pick their starting station (the bar shows live seats per station). A full station can still be picked, with an over-capacity warning.
- Otherwise (Auto, the default) the colour is balanced: a colour the whole party fits in, then the smallest group, then Cyan → Red → Orange. 8 seats per colour; a 9th is allowed with a warning. Check-ins after the event start are tagged late ("Wait in LATAG").
- Move, Undo and Add walk-in are on the page. Settings has the times, seats per colour, and colour names (marked not confirmed).
- State is saved in that device's browser, so use **one device** for check-in. Use "Download results (CSV)" at the end, then "Clear all data on this device".

Never commit the attendee CSV or the results export: `*.csv` is in `.gitignore`.
