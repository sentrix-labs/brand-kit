# Sentrix Brand — Usage Guide

How to pick the right logo asset for any surface. This is the practical cheat-sheet — see `BRAND_GUIDE.md` for the underlying design system (palette, typography, clear-space).

If you take nothing else from this doc:

> **For nav, footer, and chrome that pairs the mark with a wordmark, use `svg/sentrix-mark-header.svg`.**
> **For coin/asset stamps (wallet balance, faucet hero), use `avatars/solid-bronze-gold/`.**
> Everything else is variations on those two.

## At a glance — pick by surface

| Surface | Asset | Why |
|---|---|---|
| Web nav (top bar) | `svg/sentrix-mark-header.svg` | Diamond + 4 pearl dots, no ring, no disc. Pearl dots survive at 32-56px display. |
| Footer | `svg/sentrix-mark-header.svg` (smaller size) | Same asset, just `size={22-28}` |
| App shell / breadcrumb | `svg/sentrix-mark-header.svg` | Same |
| Hero coin / wallet balance | `avatars/solid-bronze-gold/avatar-solid-bronze-gold-512.png` | Solid bronze coin with gold diamond. Reads as a "coin" stamp. |
| Faucet hero, asset cards | `avatars/solid-bronze-gold/*.png` | Same family |
| Big editorial moment (landing splash, social card) | `svg/sentrix-mark-header.svg` at 96-200px **OR** `avatars/single-ring-transparent/*.png` if you want the framed-coin look | Either works at hero size. The header SVG keeps the brand silhouette clean; the ring adds a "framed" feel. |
| Browser favicon | `favicon/favicon-{16,32}.png`, `favicon.ico` | Pre-rasterized, do NOT generate from SVG |
| iOS home screen | `app-icon/ios-appstore-1024.png` (or `favicon/apple-touch-icon.png`) | Pre-baked |
| Android home screen | `app-icon/android-playstore-512.png` + adaptive `android-adaptive-{foreground,background}-432.png` | Pre-baked |
| Twitter / X profile pic | `avatars/single-ring-transparent/*-1024.png` (light mode) or `single-ring-black/*-1024.png` (dark) | Per `avatars/README.md` recommendations |
| Discord, Telegram avatar | `avatars/single-ring-transparent/*-1024.png` | Same |
| Exchange listings (CoinGecko, CMC, Trust Wallet) | `exchange/coingecko-200.png`, `exchange/coinmarketcap-200.png`, `exchange/trustwallet-256.png` | Pre-cropped per platform spec |
| Print, future-proof | `avatars/*/avatar-*-2048.png` | Highest raster |

## Wordmark pairing — the canonical rule

When the mark sits next to a Sentrix wordmark (nav, footer, hero):

| Property | Value | Reason |
|---|---|---|
| Casing | `SENTRIX` (all caps) | Matches the iconic mark's formality. Mixed-case "Sentrix" undersells it. |
| Font family | Serif (Playfair Display in product apps) | Matches the editorial brand voice. |
| Letter-spacing | `tracking-[.04em]` for nav, up to `tracking-[.05em]` at hero size | Minimal — wide tracking (`.25em`+) reads as a section eyebrow, not a brand mark. |
| Weight | font-light (300) or font-normal (400) | Mark already carries visual weight; wordmark stays restrained. |
| Color | brand gold (`var(--gold)` / `#8A5A11`-ish) | Single color. No multi-color X accents. |
| Cap-height | ~60% of mark height | Mark visually slightly larger than the wordmark caps; vertically centered via `flex items-center`. |

**Reference (canonical):**

```tsx
<a href="/" className="flex items-center gap-3 text-[var(--gold)]">
  <SentrixLogo size={36} />
  <span className="font-serif text-[22px] font-light tracking-[.04em] uppercase leading-none">
    SENTRIX
  </span>
</a>
```

## Logo asset map (every Sentrix Chain file in this repo)

### SVG masters (`svg/`)

| File | What's in it | Use |
|---|---|---|
| **`sentrix-mark-header.svg`** | Diamond outline + filled inner diamond + 4 gold pearl dots (r=13 — sized for headers). No ring, no disc, transparent bg. | **Primary asset for all nav/footer/chrome.** |
| `sentrix-mark-header-mono-black.svg` | Same composition, all black | Light-bg surfaces (printed material, light theme nav) |
| `sentrix-mark-header-mono-white.svg` | Same composition, all white | Dark photography/video overlays where bronze reads too low contrast |
| `sentrix-mark-tight.svg` | Tight crop of the diamond + 4 pearl dots (r=11 — sized for hero, dots vanish below ~96px) | Hero only. Don't reach for it in nav. |
| `sentrix-logo-transparent.svg` | Same as tight but with viewBox padding | Hero only. |
| `sentrix-logo-full.svg` | Diamond + dots inside a SOLID BLACK CIRCLE | Stamp-on-light-bg hero. The black circle is a deliberate framing device, not a "ring outline". |
| `sentrix-logo-mono-black.svg` | Tight diamond + dots, all black, transparent bg | Light-bg hero |
| `sentrix-logo-mono-white.svg` | Tight diamond + dots, all white, transparent bg | Dark-bg hero |
| `sentrix-avatar-zoomed.svg` | Larger diamond + dots inside full black circle (r=512 fills viewBox) | Avatar contexts where a strong frame is wanted |

### PNG avatars (`avatars/`)

Each variant is rendered at 32 / 64 / 128 / 180 / 192 / 256 / 400 / 512 / 1024 / 2048 px. Use the size closest to your render dimension and let the browser scale up only when necessary.

| Variant | Composition | Suggested use |
|---|---|---|
| **`solid-bronze-gold/`** | Solid bronze disc + gold diamond + pearl dots. No ring outline. | **Primary "coin" stamp** — wallet balance pucks, faucet hero coin, asset cards. |
| `single-ring-transparent/` | Bronze ring (outer circle outline) + diamond + pearl dots, transparent bg | Avatars where a framed look is wanted on overlays |
| `single-ring-black/` | Same but on solid black bg | Twitter/Discord avatars (dark theme) |
| `single-ring-ivory/` | Same but on solid ivory bg | Print, light-theme avatars |
| `double-ring-black/` | Gold outer + bronze inner double-ring + diamond + dots, black bg | Premium "coin" feel for exchange listings, big avatars |
| `double-ring-ivory/` | Same on ivory | Print, premium light contexts |
| `solid-black/` | Solid black disc + diamond + dots | Avatars on light backgrounds where you want strong contrast |
| `solid-ivory/` | Solid ivory disc + diamond + dots | Avatars on dark backgrounds |

The "ring" in `*-ring-*` variants refers to a **circular outline** stroked around the diamond. If you want diamond + dots WITHOUT any circular framing, use `svg/sentrix-mark-header.svg` (the SVG renders cleanly at every size, no rasterizer artifacts).

### Other folders

| Folder | What's in it | Use |
|---|---|---|
| `favicon/` | favicon.ico, favicon-{16,32}.png, apple-touch-icon, android-chrome-{192,512}, mstile-150, safari-pinned-tab.svg, html-head-snippet.html, site.webmanifest | Web favicon set. Drop the snippet into `<head>`. |
| `app-icon/` | iOS App Store 1024, Android Play Store 512, Android adaptive bg+fg 432 | Mobile app submissions. |
| `mono/` | Tight diamond+dots renders in pure black or pure white at 256/512/1024 | Printed material, single-color contexts |
| `png-full/` | `sentrix-{16…4096}.png` — diamond+dots inside black circle, multiple sizes | Where the framed look is wanted but you can't ship SVG |
| `png-transparent/` | `sentrix-{16…4096}.png` — diamond+dots transparent bg, multiple sizes | Tight-crop diamond on transparent (raster fallback for the SVG header mark) |
| `social/` | x-banners, x-avatars, GitHub avatars | Pre-cropped for social platforms |
| `exchange/` | coingecko-200, coinmarketcap-{32,200}, listing-full-512, tokenlist-{32,128,256}, trustwallet-256 | Exchange + token-list submissions, pre-cropped |

## Sub-brands

The brand-kit also ships marks for **SentrisCloud** (the parent company) and **Sentrix Labs** (the protocol foundation). These follow the same rules but use their own marks (see `svg/sentriscloud-mark.svg`, `svg/sentrix-labs-mark.svg`). Don't pair the Sentrix Chain mark with a SentrisCloud or Labs wordmark — each brand owns its own pairing.

Sub-products of Sentrix Chain (faucet, scan, solux, coinblast) typically pair their own product wordmark with the Sentrix Chain mark. The exception is when a sub-product has its OWN visual identity (e.g., CoinBlast has a rocket motif) — in that case, the sub-product gets its own mark and the Sentrix Chain mark stays on the parent surfaces only.

## Don't

- Don't recolor outside the palette (`#8A5A11` bronze, `#DBC17F` gold, `#000000` black, `#FFFFFF` white). The mono variants are the only single-color renders.
- Don't add drop-shadow, glow, or gradient overlays.
- Don't stretch — preserve square aspect.
- Don't use `svg/sentrix-mark-tight.svg` or any of the `sentrix-logo-*` files at < 96px display. Their pearl dots vanish. Use `sentrix-mark-header.svg` (header-tuned dot radius) at smaller sizes.
- Don't pair the mark with a wide-tracked uppercase wordmark in nav chrome (`tracking-[.25em]` reads as a section eyebrow). Save wide tracking for hero size where there's room for it to breathe.
- Don't pair the mark with mixed-case "Sentrix" wordmark — the mark is iconic, the wordmark should match.
- Don't add a circular background (ring or solid disc) around the header mark unless you're specifically going for the "framed coin" hero look — the bare diamond is the brand silhouette.
- Don't generate favicons from any SVG at runtime. Use the pre-rasterized `favicon/` set — runtime rasterizers blow out small dots.

## Live reference implementations

Surfaces shipping in production. Match these when building new product chrome.

| Surface | Mark | Wordmark | Notes |
|---|---|---|---|
| sentrixchain.com nav | `sentrix-mark-header.svg` @ 36px | `SENTRIX` Playfair 22px font-light tracking-[.04em] uppercase | Default brand chrome |
| sentrixchain.com footer | `sentrix-mark-header.svg` @ 26px | `SENTRIX` Playfair 16px font-light tracking-[.04em] | Smaller proportional version of nav |
| sentrixchain.com hero (in-page) | (no inline mark — wordmark only) | `SENTRIX` Playfair 96px font-light tracking-[.05em] | Editorial display |
| scan.sentrixchain.com nav | `sentrix-mark-header.svg` @ 32px | `SENTRIX` Playfair 18px font-light + sans `Scan` subtitle | Sub-brand pattern |
| faucet.sentrixchain.com hero | `solid-bronze-gold` @ 96px | `Sentrix Faucet` Playfair 44px tracking-tight | Hero coin context |
| solux.sentriscloud.com balance puck | `solid-bronze-gold` @ inline | (no wordmark — paired with SRX numeric) | Asset value stamp |
| coinblast.sentrixchain.com nav | (sub-brand — rocket motif, not the Sentrix Chain mark) | `CoinBlast` | Intentional separate identity |
