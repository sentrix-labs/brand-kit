# Sentrix Brand — Usage Guide

How to pick the right logo asset for any surface. See `BRAND_GUIDE.md` for the underlying design system (palette, typography, clear-space).

## At a glance — pick by surface

| Surface | Asset |
|---|---|
| Web nav, footer, chrome (mark + wordmark lockup) | `svg/sentrix-mark-tight.svg` (or `sentrix-logo-transparent.svg`) |
| Hero coin / wallet balance / asset stamp | `avatars/solid-bronze-gold/avatar-solid-bronze-gold-512.png` |
| Twitter / Discord / Telegram avatar (overlay) | `avatars/single-ring-transparent/*-1024.png` |
| Twitter / Discord avatar (solid bg) | `avatars/single-ring-black/*-1024.png` (dark) or `single-ring-ivory` (light) |
| Browser favicon | `favicon/favicon-{16,32}.png`, `favicon.ico` (pre-rasterized — don't generate from SVG) |
| iOS home screen | `app-icon/ios-appstore-1024.png` |
| Android home screen | `app-icon/android-playstore-512.png` + adaptive `android-adaptive-{foreground,background}-432.png` |
| Exchange listings (CoinGecko, CMC, Trust Wallet) | `exchange/coingecko-200.png`, `exchange/coinmarketcap-200.png`, `exchange/trustwallet-256.png` |

## Wordmark pairing — canonical lockup

The brand-kit ships the canonical lockup as `social/og-image-1200x630.png`: diamond mark + `SENTRIX` in **bold sans-serif gold**. When the mark sits next to a Sentrix wordmark in product chrome, match that lockup style:

- Casing: `SENTRIX` (all caps)
- Font family: bold sans-serif (Geist Sans, Inter, or system sans, weight 700–800)
- Letter-spacing: minimal (≤ 0.05em)
- Color: brand gold (`#DBC17F` / `var(--gold)`)
- Container: `flex items-center gap-3` for visual center alignment

```tsx
<a href="/" className="flex items-center gap-3 text-[var(--gold)]">
  <SentrixLogo size={32} />
  <span className="font-sans text-[22px] font-extrabold tracking-[.02em] uppercase">
    SENTRIX
  </span>
</a>
```

## Logo asset map (Sentrix Chain)

### SVG masters (`svg/`)

| File | What's in it | Use |
|---|---|---|
| `sentrix-mark-tight.svg` | Tight crop of diamond outline + filled inner diamond + 4 pearl dots | Default mark for product chrome |
| `sentrix-logo-transparent.svg` | Same composition with viewBox padding (1024×1024) | Hero / display contexts where padding is needed |
| `sentrix-logo-full.svg` | Diamond + dots inside a SOLID BLACK CIRCLE | Stamp-on-light-bg hero, or where a framed look is wanted |
| `sentrix-logo-mono-black.svg` | All-black mark, transparent bg | Light-bg surfaces (print, light theme) |
| `sentrix-logo-mono-white.svg` | All-white mark, transparent bg | Dark photography/video overlays |
| `sentrix-avatar-zoomed.svg` | Larger diamond + dots inside full black circle | Avatar contexts where a strong frame is wanted |

### PNG avatars (`avatars/`)

Each variant is rendered at 32 / 64 / 128 / 180 / 192 / 256 / 400 / 512 / 1024 / 2048 px.

| Variant | Composition | Use |
|---|---|---|
| `single-ring-transparent/` | Bronze ring + diamond + pearl dots, transparent bg | Avatars (overlay), social profile pictures on busy backgrounds |
| `single-ring-black/` | Same on solid black bg | Twitter/Discord avatars (dark) |
| `single-ring-ivory/` | Same on solid ivory bg | Print, light-theme avatars |
| `double-ring-black/` | Gold outer + bronze inner double-ring + diamond + dots, black bg | Premium "coin" feel for exchange listings |
| `double-ring-ivory/` | Same on ivory | Print, premium light contexts |
| `solid-bronze-gold/` | Solid bronze disc + gold diamond + pearl dots | Coin/asset stamp — wallet balance, faucet hero, asset cards |
| `solid-black/` | Solid black disc + diamond + dots | Avatars on light backgrounds |
| `solid-ivory/` | Solid ivory disc + diamond + dots | Avatars on dark backgrounds |

### Other folders

| Folder | What's in it |
|---|---|
| `favicon/` | favicon.ico, favicon-{16,32}.png, apple-touch-icon, android-chrome-{192,512}, mstile-150, safari-pinned-tab.svg, html-head-snippet.html, site.webmanifest |
| `app-icon/` | iOS App Store 1024, Android Play Store 512, Android adaptive bg+fg 432 |
| `mono/` | Tight diamond+dots in pure black or white at 256/512/1024 |
| `png-full/` | `sentrix-{16…4096}.png` — diamond+dots inside black circle, multiple sizes |
| `png-transparent/` | `sentrix-{16…4096}.png` — diamond+dots transparent bg, multiple sizes |
| `social/` | x-banners, x-avatars, GitHub avatars, og-image (canonical lockup) |
| `exchange/` | Pre-cropped marks for CoinGecko, CoinMarketCap, Trust Wallet, token lists |

## Sub-brands

The brand-kit also ships marks for **SentrisCloud** (parent company) and **Sentrix Labs** (protocol foundation). These follow the same rules but use their own marks (see `svg/sentriscloud-mark.svg`, `svg/sentrix-labs-mark.svg`). Don't pair the Sentrix Chain mark with a SentrisCloud or Labs wordmark.

## Don't

- Don't recolor outside the palette (`#8A5A11` bronze, `#DBC17F` gold, `#000000` black, `#FFFFFF` white)
- Don't add drop-shadow, glow, or gradient overlays
- Don't stretch — preserve square aspect
- Don't generate favicons from SVG at runtime — use the pre-rasterized `favicon/` set
