# Assets

Drop image files here and reference them from the pages.

## Screenshots

Add your real app screenshots and swap them into `index.html` where the phone
placeholders are (search the file for `ph-note`). Suggested names:

- `mycaddyman-01.png`, `mycaddyman-02.png`
- `safelysolo-01.png`, `safelysolo-02.png`

Replace a placeholder block like this:

```html
<div class="screen">
  <p class="ph-note">Screenshot<code>assets/mycaddyman-01.png</code></p>
</div>
```

with:

```html
<div class="screen">
  <img src="assets/mycaddyman-01.png" alt="MyCaddyMan hole view showing green distances">
</div>
```

Tip: export at roughly 2x the display size (e.g. ~600px wide) so they stay crisp
on retina screens. Keep the whole repo under ~1 GB (GitHub Pages limit) — for a
handful of screenshots you'll be nowhere near it.

## Store badges (important — use the official ones)

The store buttons in `index.html` are plain placeholders. Replace them with the
official badge artwork so you comply with Apple's and Google's brand guidelines:

- **Apple — "Download on the App Store":**
  https://developer.apple.com/app-store/marketing/guidelines/
- **Google Play — "Get it on Google Play":**
  https://play.google.com/intl/en_us/badges/

Download the official badge image, drop it in this folder (e.g.
`app-store-badge.svg`, `google-play-badge.png`), and link it to your listing:

```html
<a href="https://apps.apple.com/app/idXXXXXXXXX">
  <img src="assets/app-store-badge.svg" alt="Download MyCaddyMan on the App Store" height="48">
</a>
```
