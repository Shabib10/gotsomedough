# Got Some Dough — Website design system

The tokens and components used on gotsomedough's website. Machine-readable values live in `design-tokens.json`.

---

## 1. Colour

| Token | Hex | Use |
|---|---|---|
| `color.brand.pink` | `#EE2B76` | Hero, footer, primary buttons, active nav pill, accents |
| `color.brand.pink-hover` | `#D81F66` | Hover state of pink buttons |
| `color.surface.off-white` | `#FAF7F0` | Section backgrounds (carousel base, strip, ingredients, story), Box of 4 card, cart panel |
| `color.surface.white` | `#FFFFFF` | Menu section, inputs, cart pill, chips |
| `color.surface.card-grey` | `#F5F5F7` | Cookie cards ("Pick your cookie"), cart thumbnails |
| `color.surface.peach` | `#F9C9AF` | Gifting section background |
| `color.text.primary` | `#000000` | Text on light surfaces |
| `color.text.inverse` | `#FFFFFF` | Text on pink |
| `color.text.muted` | `#444444` | Helper text, flavour lists in cart |
| `color.feedback.error` | `#C0164F` | Form validation |
| `color.feedback.open` | `#1FAE5B` | "Open now" dot |
| `color.overlay` | `rgba(0,0,0,.35)` | Behind the cart panel |

**Pairing rules:** black on off-white/white/grey · white on pink · pink buttons on light cards, white buttons (pink text) on pink cards.

---

## 2. Typography

| Family | File | Role |
|---|---|---|
| **Mont Heavy** | `assets/fonts/mont-heavy.otf` | Headlines, nav, buttons, labels, prices, cookie names. Always weight 900. |
| **Mont Regular** | `assets/fonts/mont-regular.otf` | Body copy, sublines, footer details |
| **Comalle** | `assets/fonts/comalle.otf` | Script accent only — the footer line ("*come on* over.") |
| Noto Sans (Google) | — | Fallback glyphs only: ₹ (Black) and ಬೆಂಗಳೂರು (Kannada) |

### Scale
| Style | Size | Notes |
|---|---|---|
| Display / H1 | `clamp(40px, 7vw, 72px)` | Mont Heavy, line-height 1.05, tracking −0.035em |
| Section H2 | `clamp(36px, 6vw, 72px)` | Mont Heavy, line-height 1, tracking −0.035em |
| Box number (04 / 08) | 72px · 90px ≥1024px | Optically nudged left to align with the line below |
| Subline (hero) | `clamp(18px, 2.2vw, 25px)` | Mont Regular |
| Footer script line | 31–58px (fluid) | Comalle + Mont Regular |
| Strip ("made for sharing") | `clamp(18px, 3vw, 32px)` | Mont Heavy, uppercase |
| Card title (cookie name) | 20px · 15px <600px | Mont Heavy, uppercase |
| Body | 16px (paragraphs 16–20px fluid) | Mont Regular, line-height 1.45–1.6 |
| Nav / labels | 15px | Mont Heavy, uppercase, tracking +0.02em |
| Button | 13–15px | Mont Heavy, uppercase, tracking +0.02em |
| Small / helper | 12–13px | Mont Regular |

**Optical centring:** text inside pills uses `text-box: trim-both cap alphabetic` (class `.gsd-c`) so capitals sit dead-centre; lowercase uses `.gsd-x`.

**Casing:** headlines in sentence case ("We take cookies seriously"); nav, labels and buttons in UPPERCASE.

---

## 3. Layout & spacing

| Token | Value |
|---|---|
| Content max-width | 1200px (nav 1100px) |
| Section padding (vertical) | `clamp(56px, 9vw, 120px)` — Story: 56–120 top, 112–240 bottom |
| Section padding (horizontal) | `clamp(20px, 5vw, 64px)` |
| Grid gap | 20px (12px on phones) |
| Breakpoints | **600px** (phone) · **810px** (nav switches to mobile) · **1024px** (desktop) |

Menu grid: 2 columns <1024px, auto-fit (min 260px) on desktop. Footer: 4 columns → 2 (<1024) → 1 (<600).

---

## 4. Shape

| Token | Value | Use |
|---|---|---|
| `radius.pill` | 999px | All buttons, nav pills, cart pill, badges |
| `radius.card` | 28px (22px phone) | Cookie cards, gift box cards |
| `radius.input` | 14px | Form fields, picker rows |
| `radius.circle` | 50% | Add-to-cart button, empty cart button, box slots |
| Ingredients photo | `200px 200px 28px 28px` | Arched frame |

No drop shadows on cards; cookie cut-outs carry a soft drop-shadow.

---

## 5. Components

| Component | Spec |
|---|---|
| **Primary button** | Pink pill, white Mont Heavy uppercase, 44–54px tall. Hover: letter flip. |
| **Outline button** (hero "order now") | 2px white border pill on pink; hover fills white with pink text. |
| **Add-to-cart** | 38px pink circle, white + icon (stroke 3); becomes ✓ for 1.4s. |
| **Cart button** | White circle (42px) with box icon when empty → pill with count when items are added. |
| **Floating nav** | Bottom pill, off-white at 35% + 18px blur; active section = pink pill. Appears after scrolling past the hero. |
| **Cookie card** | Grey `#F5F5F7`, cookie photo 78% width, name + ₹200 + add button pinned to the bottom. |
| **Gift box card** | Flips to a flavour picker: slots row, scrollable list (4½ rows visible), "Surprise me", "Pick N more" → Add to cart. Tap a filled slot to break the cookie and remove it. |
| **Cart panel** | Off-white slide-in, 420px max. Items → name, pickup/delivery pills, notes → total → Continue on WhatsApp. |
| **Open/Closed badge** | Pill, white (open) or black (closed) with status dot; Bengaluru time. |

### Iconography
Simple stroked SVG, round caps. Plus/minus stroke 3 (minus 4.5 for legibility). Brand box icon (gable box + handle + smile) for the cart.

---

## 6. Motion

| Token | Value | Use |
|---|---|---|
| `ease.out` | `cubic-bezier(.2,.8,.2,1)` | Entrances, reveals, tilt return |
| `ease.in-out` | `cubic-bezier(.65,0,.35,1)` | Letter flip, card flip, carousel |
| Hero entrance | 0.8s, rise 18px, stagger 0.12s | Headline → subline → button |
| Section reveal | 0.9s, rise 56px, line stagger 0.14s | Direction-aware (up/down), replays |
| Letter flip | 0.5s, 2px gap (1px lowercase) | Nav + button hover |
| Carousel | 0.9s move every 2.4s | Hero cookies |
| Cookie tilt | up to 7.5°, highlight sweep | Pointer devices only |
| Gift card tilt | up to 6°, card dips toward pointer | Pointer devices only |
| Card float | 6px, 6s loop | Gift cards |
| Cookie break | 0.5s split + crumbs | Removing from a box |

All motion is disabled for visitors with *reduce motion* turned on.

---

## 7. Voice (website copy)
- Short, confident, a little cheeky: "We take cookies seriously" · "A proper cookie." · "Baked to Brag."
- Always lead with **eggless** where trust matters (hero subline, ingredients).
- Sentence case for headlines, full stops on short headlines.
