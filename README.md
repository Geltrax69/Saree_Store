# Saree Store

> ## Status: 🟡 In Progress
>
> <progress value="55" max="100"></progress>
> **Progress: 55%** — Working storefront UI; cart is session-only, no checkout.

<p align="center">
  <img src="banner.webp" alt="Saree Store banner" width="100%" />
</p>

![HTML](https://img.shields.io/badge/HTML-5-orange)
![CSS](https://img.shields.io/badge/CSS-3-blue)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow)

## What it is

A premium saree storefront in plain HTML/CSS/JS — no frameworks, no build step. Product cards (silk, cotton, Banarasi, Kanjeevaram, georgette…) are rendered dynamically from an `imageslinks` file of image URLs, with INR pricing, star ratings, bookmark toggles, and add-to-cart buttons that expand into quantity steppers. A cart badge in the navbar counts items with a pop animation.

## What works (verified)

- ✅ Dynamic product grid — cards built from the `imageslinks` URL list — `script.js`
- ✅ INR pricing with Indian number formatting (`₹ 12,500`) — `script.js`
- ✅ Ratings, descriptions, "Online exclusive" tag on the first product
- ✅ Add-to-cart → quantity stepper (+/−) per card — `attachEventListeners()`
- ✅ Cart badge counter with pop animation in the navbar
- ✅ Bookmark toggle per product
- ✅ Image fallback — broken URLs swap to a placeholder — `onerror` handler

> Verified by reading all three source files (473 lines total). Serve over HTTP — `fetch('imageslinks')` won't work from `file://`.

## Tech stack

| Layer | Tech |
|---|---|
| Markup | HTML5 |
| Styling | Vanilla CSS, Inter font |
| Logic | Vanilla JavaScript (no dependencies) |
| Data | `imageslinks` text file (one image URL per line) |

## How to run

```bash
# Serve over HTTP (required — fetch() fails on file://)
npx serve .
# or
python3 -m http.server 8000
# then open http://localhost:8000 (or :3000)
```

## Screenshots

No screenshots ship with the repo. The banner above is the visual; serve it locally to see the storefront.

## What you can add more

- [ ] Real cart page — the cart is just a badge counter; there's nowhere to review items
- [ ] Checkout flow — no payment, no order placement at all
- [ ] Cart persistence — refresh wipes the cart; use `localStorage`
- [ ] Product detail pages — click a saree for fabric, blouse, delivery info
- [ ] Search and filters — by fabric, price range, occasion
- [ ] Real product data — prices and ratings are randomly generated per load
- [ ] Wishlist persistence — bookmarks don't survive a refresh

## Project structure

```
Saree_Store/
├── index.html     # Navbar, hero, products container
├── script.js      # Product rendering, cart badge, quantity steppers
├── styles.css     # Storefront styling
└── imageslinks    # One product image URL per line
```

---
*README written after code audit on 2026-10-08.*
