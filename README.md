# Got Some Dough — Website

The live, single-page website for **Got Some Dough**, a speciality gourmet cookie bakehouse in Koramangala, Bengaluru.
Freshly baked. 100% eggless.

Static site: no build step, no server. Upload this folder to any static host (GitHub Pages, Netlify, Vercel) and it works.

---

## Folder structure

```
Website/
├── index.html                      ← the website (open this)
├── .nojekyll                       ← tells GitHub Pages to serve files as-is
├── README.md                       ← this file
├── assets/
│   ├── fonts/                      ← brand fonts (kebab-case names)
│   │   ├── mont-heavy.otf          ← headlines, nav, buttons, prices
│   │   ├── mont-regular.otf        ← body copy
│   │   └── comalle.otf             ← script accent ("come on" in the footer)
│   ├── images/
│   │   ├── brand/                  ← gsd-logo.svg, gsd-favicon.svg, gsd-apple-touch-icon.png, gsd-share-preview.jpg
│   │   ├── cookies/                ← one transparent photo per flavour: cookie-<flavour-name>.webp
│   │   └── sections/               ← section photography: <section>-<description>.jpg
│   └── js/
│       ├── runtime/dc-runtime.js   ← renders the page template (from Claude Design)
│       └── vendor/                 ← React 18.3.1, self-hosted (no CDN dependency)
├── docs/
│   ├── design-system.md            ← colours, type, spacing, components, motion
│   └── design-tokens.json          ← the same tokens, machine-readable
└── source/
    └── got-some-dough.design-canvas.dc.html  ← editable original from Claude Design (for reference)
```

### Naming convention
- **All lowercase, kebab-case**, no spaces: `cookie-apple-crumble.webp`, not `Apple Crumble.png`.
- **Prefix by type**: `gsd-` for brand assets, `cookie-` for flavours, `<section>-` for section photos.
- **Images**: `.webp` for cut-out cookies (small + transparent), `.jpg` for photography, `.svg` for logos/icons.
- Cookie photos: square-ish, transparent background, ~600px, cookie centred.

---

## Publish on GitHub Pages

1. Go to **github.com → New repository** → name it `gotsomedough` → Public → **Create repository**.
2. On the empty repo page click **uploading an existing file** (or **Add file → Upload files**).
3. Drag in **everything inside this `Website` folder** (not the folder itself), including `.nojekyll`.
   *Tip (Mac): press ⌘⇧. in Finder to show hidden files like `.nojekyll`.*
4. Click **Commit changes**.
5. Go to **Settings → Pages** → *Source*: **Deploy from a branch** → branch `main`, folder `/ (root)` → **Save**.
6. After 1–2 minutes the site is live at `https://<your-username>.github.io/gotsomedough/`.

### Custom domain (optional)
1. **Settings → Pages → Custom domain** → enter e.g. `gotsomedough.in` → Save.
2. At your domain provider add DNS records:
   - `A` records for `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - `CNAME` for `www` → `<your-username>.github.io`
3. When the check passes, tick **Enforce HTTPS**.

### Updating later
Edit the file on GitHub (pencil icon) or upload a replacement with the **same file name and path**, then commit. Pages redeploys automatically.

---

## How ordering works
There is no payment system. The cart builds a WhatsApp message and opens a chat with **+91 87222 01666**:
- Single cookies are ₹200 each. Box of 4 = ₹700, Box of 8 = ₹1,200 (flavours chosen on the flip card).
- The customer adds their name, Pickup or Delivery (+ address) and optional notes.
- **Continue on WhatsApp** opens WhatsApp with the order typed out. The cart is remembered in the browser if they come back.

### Where to change things in `index.html`
Search (⌘F) for:
| To change | Search for |
|---|---|
| Flavours, names, photos | `cookies = [` |
| Single cookie price | `PRICE = 200` |
| Box sizes and prices | `boxes: [` |
| WhatsApp number | `918722201666` (appears twice: footer link + checkout) |
| Opening hours (Open/Closed badge) | `hr >= 12 && hr < 22` (appears twice) |
| Ingredients list | `ingredients: [` |
| Address / maps link | `Koramangala` |

---

## Before going live — checklist
- [ ] **Font licence:** `mont-heavy.otf` is the *DEMO* version — buy the commercial web licence for Mont (Heavy + Regular) and swap the file (keep the same name). Check Comalle's licence covers web use.
- [ ] **Instagram handle:** currently `@gotsomedough` (placeholder) — search `instagram.com/gotsomedough`.
- [ ] **Email:** currently `hello@gotsomedough.com` (placeholder) — search `hello@`.
- [ ] **Photo rights:** confirm rights for `sections/ingredients-flatlay.jpg`; `cookie-biscoff.webp` shows the Lotus logo.
- [ ] Test an order end-to-end on a phone (WhatsApp opens with the message).
- [ ] Optional: add Google Analytics / Meta Pixel if you want visit tracking.

---

## Notes
- The page needs JavaScript (all modern browsers). Content is rendered by `assets/js/runtime/dc-runtime.js`.
- Visitors who set "reduce motion" on their device get the site without animations.
- Open/Closed badge and checkout notice use Bengaluru time (Tue–Sun, 12 PM–10 PM; Monday closed).
