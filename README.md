# flowstateconsulting.com

Static website for Flow State Technologies — a home for app privacy policies,
legal, screenshots, and usage tips for **MyCaddyMan** and **SafelySolo**, with
links out to the App Store and Google Play. No build step, no dependencies:
plain HTML + one CSS file, served by GitHub Pages.

## Structure

```
.
├── index.html                    # Landing: hero, both apps, tips, store links
├── styles.css                    # Shared design system (whole site)
├── 404.html                      # Branded not-found page
├── .nojekyll                     # Serve files as-is (skip Jekyll)
├── assets/                       # Screenshots + official store badges (see its README)
├── mycaddyman/privacy/index.html # → /mycaddyman/privacy/
├── safelysolo/privacy/index.html # → /safelysolo/privacy/
└── terms/index.html              # → /terms/
```

Each policy lives in its own folder so the published URL is clean and stable —
which is exactly what you paste into the store listings:

- App Store Connect (MyCaddyMan) → `https://flowstateconsulting.com/mycaddyman/privacy/`
- App Store Connect + Play Console (SafelySolo) → `https://flowstateconsulting.com/safelysolo/privacy/`

## Deploy (free, public repo)

1. Create a **public** repo and push these files to the `main` branch.
2. Repo **Settings → Pages** → *Build and deployment* → **Deploy from a branch** →
   `main` / `/ (root)` → **Save**.
3. In a minute or two the site is live at `https://<your-username>.github.io/<repo>/`.

Paths in this site are relative, so it works both at that project URL and later
at the custom domain — no changes needed when you switch.

### Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Custom domain (do this at your Squarespace renewal)

You don't need this to go live — the github.io URL works now. When you're ready
to move `flowstateconsulting.com`:

1. **Settings → Pages → Custom domain** → enter `flowstateconsulting.com` → Save.
   (GitHub writes a `CNAME` file to the repo.) Add and verify the domain under
   your account settings first to prevent takeover.
2. At whichever DNS host holds the domain, add GitHub Pages records:
   - **Apex** `flowstateconsulting.com` → four **A** records:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
     (and the matching **AAAA** records for IPv6). *Confirm the current values in
     GitHub's docs — they're stable but worth a glance.*
   - **www** → **CNAME** → `<your-username>.github.io`
3. Wait for DNS, then tick **Enforce HTTPS** in Settings → Pages.
4. **Don't forget email:** when you move DNS, re-create your Google Workspace
   **MX** records and any **SPF / DKIM / DMARC (TXT)** records at the new host,
   or mail will stop. Verify by sending yourself a test message.
5. Only after the site + email check out, cancel the Squarespace website plan.

## Before you publish the legal pages — checklist

The privacy and terms pages are **starting drafts, not legal advice.** Each file
has a review note at the top of its source. Work through this:

- [ ] Replace every `[BRACKETED]` placeholder (dates, contact email, store URLs).
- [ ] Confirm each data-practice statement matches what the app actually does.
- [ ] MyCaddyMan: confirm whether round data stays on-device or syncs; name any
      analytics/crash SDK, or state there's none.
- [ ] SafelySolo: confirm the SMS provider (drafted as **Twilio**), whether
      location is stored or only passed at send time, and the contacts flow.
- [ ] Make each policy consistent with the App Store "App Privacy" label and
      (SafelySolo) the Google Play "Data safety" form.
- [ ] Set a real contact address (`privacy@` / `hello@`) that you monitor.
- [ ] Replace the placeholder store buttons with the official Apple / Google
      badges and real listing URLs (see `assets/README.md`).
- [ ] Drop in real screenshots (see `assets/README.md`).
- [ ] Consider a lawyer's review, especially SafelySolo's terms and liability.

## Notes

- GitHub Pages free tier limits: 1 GB published site, 100 GB/month soft
  bandwidth, 10 builds/hour — far beyond what this site needs.
- Fonts (Hanken Grotesk + Newsreader) load from Google Fonts via `<link>`; no
  files to manage. Swap to self-hosted later if you'd rather avoid the request.
