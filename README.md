# Syed Amais — Portfolio (Static, GitHub Pages ready)

A modern data-driven portfolio with a built-in admin panel. Pure static — no server, no build step. Drop it on **GitHub Pages**, **Netlify**, **Cloudflare Pages**, or any static host.

## Structure

```
.
├── index.html            # Public site (renders from JSON)
├── admin.html            # Admin panel (login + editor)
├── data/
│   ├── site.json         # Profile, hero, about, skills, services, process, contact, footer
│   ├── projects.json     # Project list
│   └── testimonials.json # Customer reviews
└── README.md
```

## Deploy to GitHub Pages

1. Create a public repo (e.g. `syed-portfolio`) and upload all of these files.
2. **Settings → Pages → Build and deployment → Source = Deploy from a branch**, branch `main`, folder `/ (root)`.
3. Wait ~60 seconds. Your site is live at `https://<username>.github.io/<repo>/`.
4. Admin lives at `https://<username>.github.io/<repo>/admin.html`.

## Admin login

Default credentials:

```
Username: admin
Password: admin123
```

**Change them immediately** via Admin → **Settings → Change admin credentials**.

## How editing works

The admin panel runs entirely in your browser. When you make a change, it's saved to your browser's `localStorage`, and the public site picks it up as a live preview **on your browser only**.

To publish changes for everyone:

1. Sign in to `/admin.html`.
2. Edit anything — name, hero, projects, testimonials, contact, etc.
3. Click **⬇ Export all JSON** in the top toolbar.
4. Three files download: `site.json`, `projects.json`, `testimonials.json`.
5. Replace the matching files in your repo's `/data/` folder (drag-and-drop in GitHub's web UI works fine).
6. Commit. GitHub Pages re-deploys in ~1 minute and the new content is live for all visitors.

## Sections that auto-hide

If you remove all items from a section in the admin, the entire section disappears from the public site (and the nav link to it):

- Stats
- Trusted-by / Recognised-for marquee
- Skills
- Projects (Selected Work)
- Services
- Process
- Testimonials (Praise)
- Social-link icons in the footer

So you can scale the page from minimal to full as your portfolio grows.

## Image uploads

Project covers and testimonial avatars are uploaded as base64 strings stored inside the JSON files. Keep them small (the admin enforces a 1.5 MB cap per image). For very large galleries, prefer a CDN URL instead of an upload.

## Local preview

`index.html` uses `fetch()` to load the JSON files, which won't work from a `file://` URL because of browser security rules. To preview locally:

```bash
cd "syed amais portfolio"
python3 -m http.server 8000
# open http://localhost:8000
```

(Any other static server works too — `npx serve`, `php -S`, etc.)

## Tech notes

- Tailwind via CDN (`cdn.tailwindcss.com`) — no build step.
- Inter + JetBrains Mono via Google Fonts.
- Theme toggle (dark/light) persists per visitor.
- Contact form has no backend; submissions open the visitor's mail client pre-filled with their message addressed to your contact email.

## Backup

The **Settings → Export JSON files** lets you save a snapshot any time. **Settings → Import JSON files** restores from a snapshot.
