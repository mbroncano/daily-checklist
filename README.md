# Homework PWA

A dead-simple installable web app that shows Alex his current homework list.
No accounts, no backend, no build step. Plain HTML/CSS/JS.

## Files
- `index.html` — the whole app (fetches `data.json` on load and every 5 min)
- `data.json` — the homework list. **This is the only file that changes.**
- `manifest.webmanifest`, `sw.js`, `icons/` — PWA plumbing (installable, offline shell)

## The data model
Each item in `data.json`:

```json
{ "id": "stable-unique-id", "subject": "Math", "title": "MATHia M1T3L1-4",
  "kind": "laptop" | "paper" | "school", "dueLabel": "Due Thu Oct 15, 3:30pm",
  "note": "Done inside MATHia.", "status": "open" | "verified" }
```

- `open` — shows under Laptop / Paper / At school with a tappable circle.
  Alex taps it → turns orange, "I did it" (stored in his phone's localStorage,
  keyed by item `id`, so keep ids stable across updates).
- `verified` — shows under "Done and verified" with a green check. Only set
  this once Canvas/PowerSchool confirms submission or a score.

## Deploy (pick one, all free)
1. **Cloudflare Pages / Netlify Drop**: drag the folder onto the deploy page. Done.
2. **GitHub Pages**: push the folder to a repo, enable Pages on the branch.
   Then updates = commit a new `data.json` (or point the fetch at the raw URL).
3. Any static host works; it just needs HTTPS for the service worker + install prompt.

Privacy: the URL is the only gate. Use an unguessable path or subdomain
(e.g. `hw-<random>.pages.dev`), don't link it anywhere public, and keep grades
out of `data.json` (notes here carry scores only because this seed came from
tonight's verified check — trim them if you prefer).

## Install on Alex's phone
Open the URL → Share → **Add to Home Screen**. It launches full-screen like an app.

## Updating the list
Replace `data.json` with a fresh one and redeploy (or, on GitHub Pages, just
commit it). Muse regenerates `data.json` after each morning/evening homework
check; wire that output to your host of choice (git commit, API upload, etc.).
