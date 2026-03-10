# QEI2026 Website (GitHub + Netlify)

This repository contains the static website for the **Quantum Energy Initiative Workshop 2026 (QEI2026)**.

The site is deployed on **Netlify** from this GitHub repository. Any change pushed/merged into the `main` branch triggers an automatic redeploy.

---

## 1) Repository structure

This is a static site (no build system). Netlify publishes a specific folder called the **Publish directory**.

Typical structure:

- REPO ROOT  
  - (PUBLISH_DIR)  
    - `index.html`  
    - `assets/` (logos, PDFs, images)

IMPORTANT:
- Netlify will only publish the folder configured as **Publish directory**.
- Make sure you edit the `index.html` inside that folder.

---

## 2) How to edit the website

### Option A — Edit directly on GitHub (easiest)
1. Open this repo on GitHub.
2. Navigate into the **Publish directory** folder (the folder that contains `index.html`).
3. Click `index.html`.
4. Click the pencil icon (Edit).
5. Make changes.
6. Click **Commit changes** with a message (e.g., “Update deadline”, “Add sponsor logo”).
7. Netlify will redeploy automatically.

### Option B — Edit locally (recommended for bigger changes)
1. Clone the repository:
   - `git clone <REPO_URL>`
   - `cd <REPO_NAME>`
2. Edit the file:
   - Open `(PUBLISH_DIR)/index.html` in VS Code (recommended) or any editor.
3. Commit and push:
   - `git add .`
   - `git commit -m "Describe your change"`
   - `git push`
4. Netlify redeploys automatically.

---

## 3) How to preview changes before publishing

### Quick preview (works for most edits)
- Open `(PUBLISH_DIR)/index.html` by double-clicking it (opens in your browser).

### More accurate preview (recommended, matches a real web server)
From the Publish directory, run:
- `python3 -m http.server 8000`

Then open:
- `http://localhost:8000/`

---

## 4) Where to edit common content in index.html

Tip: Use your editor’s search to jump quickly.

### A) Registration link and deadlines
Search for:
- `section id="registration"`
and update:
- the deadline text
- the registration link URL

Also update the hero “Register (free)” button:
Search for:
- `Register (free)`
and update its `href`.

### B) Speakers list
Search for:
- `section id="speakers"`
Edit the list items inside `<ul> ... </ul>`.

### C) Venue / travel
Search for:
- `section id="venue"`
Edit the cards inside the `<div class="cards"> ... </div>`.

### D) Sponsors and logos
Search for:
- `section id="sponsors"`

To add a sponsor logo:
1. Put the logo file in `(PUBLISH_DIR)/assets/` (preferred: SVG).
2. Add a new logo block inside the sponsor grid:

Example:
- `<div class="logo-card">`
  - `<a href="https://SPONSOR-SITE" ...>`
    - `<img src="assets/SPONSOR.svg" alt="Sponsor name logo">`

#### Light / dark sponsor logo switching (optional)
If a sponsor provides two variants (e.g., white for dark theme and black for light theme), use:

- `<img class="sponsor-logo-dark" src="assets/LogoWhite.svg" alt="Sponsor logo">`
- `<img class="sponsor-logo-light" src="assets/LogoBlack.svg" alt="Sponsor logo">`

The CSS will show/hide them automatically when the “Toggle light” button is used.

### E) PDFs (e.g., hotel list)
1. Upload the PDF into `(PUBLISH_DIR)/assets/` (example: `assets/hotels.pdf`)
2. Link it in the page:
- `<a class="btn" href="assets/hotels.pdf" target="_blank" rel="noopener">Download hotel list (PDF)</a>`

---

## 5) How deployment works (Netlify)

- Netlify is connected to this GitHub repository.
- Every push to `main` triggers a deploy.
- You can see deploy status in Netlify → your site → **Deploys**.

### If the website shows “Page not found” (Netlify 404 page)
This almost always means the **Publish directory** is wrong.

To fix:
1. Netlify → Site configuration (or Site settings)
2. Build & deploy → Build settings
3. Set **Publish directory** to the folder that contains `index.html`
4. Trigger a new deploy

---

## 6) How collaborators can help without sharing your Netlify credentials

You do NOT need to share your Netlify password.

Recommended approach:
- Add collaborators to GitHub:
  - GitHub repo → Settings → Collaborators → Invite
- They edit and push changes (or open Pull Requests)
- Netlify deploys automatically from GitHub

Optional safer workflow (recommended):
- Contributors open Pull Requests
- An organizer reviews and merges into `main`

Rollback:
- Netlify keeps deploy history:
  - Netlify → Deploys → select a previous deploy → Publish deploy

---

## 7) Public vs Private repository — should we worry?

### Is it dangerous to have the repo public?
Usually NO, as long as you do not store secrets.

Safe to keep public:
- `index.html`
- sponsor logos and PDFs
- event dates, venue, speaker list, contact email

Do NOT put in the repo:
- passwords
- API keys / tokens
- private emails/phone numbers
- anything you would not want searchable on the web

Recommendation:
- If this repo only contains public website content: Public is generally fine.
- If you want tighter control or less visibility: Make it Private and invite collaborators.

Important:
- Even if the repo is private, the WEBSITE is still public (normal for a conference site).

---

## 8) Contact
For questions about the event:
- contact@quantum-energy-initiative.org
