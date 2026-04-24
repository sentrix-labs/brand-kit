# Sentrix Chain — Brand Guide

Official brand guidelines for **Sentrix Chain**, the Indonesian Layer 1 blockchain.

**Generated:** April 2026
**Owner:** Sentrix Labs
**Version:** 1.0

---

## Brand Identity

### Official Names

| Context | Name | When to use |
|---------|------|-------------|
| **Formal / External** | **Sentrix Chain** | Whitepapers, exchange listings, press releases, legal documents, pitch decks, first mention in media |
| **Casual / Community** | **Sentrix** | Twitter, Discord, community chat, internal documentation |
| **First mention (ambiguous context)** | **Sentrix Chain — Indonesian L1 Blockchain** | SEO meta tags, media coverage, investor decks |

**Critical rule:** Never use "Sentrix Chain" and "Sentrix" inconsistently within the same formal document. Pick one based on context and stick with it.

### Tagline
```
The Indonesian L1 Blockchain
```

### Brand Hierarchy
```
Sentrix Labs                    ← Parent company
│
└── Sentrix Chain               ← L1 blockchain (this brand kit)
    ├── Sentrix Scan            ← Block explorer
    ├── Sentrix SDK             ← Developer toolkit
    └── [future products...]
```

`FastPoint` and `GSC Patrol` are separate Sentrix Labs SaaS products — they do **not** fall under the Sentrix Chain brand umbrella.

---

## Color Palette

| Name | Hex | RGB | CMYK (approx) | Usage |
|------|-----|-----|---------------|-------|
| Sentrix Black | `#000000` | 0, 0, 0 | 0, 0, 0, 100 | Primary background, circle container |
| Sentrix Bronze | `#8A5A11` | 138, 90, 17 | 0, 35, 88, 46 | Primary mark color (outline + inner diamond) |
| Sentrix Gold | `#DBC17F` | 219, 193, 127 | 0, 12, 42, 14 | Accent nodes, wordmark on dark backgrounds |
| Deep Canvas | `#0A0A0C` | 10, 10, 12 | 17, 17, 0, 95 | Banner / hero section background |

### CSS Tokens

```css
:root {
  --sentrix-black:  #000000;
  --sentrix-bronze: #8A5A11;
  --sentrix-gold:   #DBC17F;
  --sentrix-canvas: #0A0A0C;
}
```

### Tailwind Config

```js
theme: {
  extend: {
    colors: {
      sentrix: {
        black:  '#000000',
        bronze: '#8A5A11',
        gold:   '#DBC17F',
        canvas: '#0A0A0C',
      }
    }
  }
}
```

---

## Logo System

### Primary Mark
The Sentrix Chain logo consists of:
1. An outer diamond outline (bronze)
2. A smaller filled diamond inside (bronze)
3. Four gold nodes at the cardinal vertices
4. A black circle container (in the "full" variant)

The diamond + nodes symbolize a network of validators anchored by a central consensus mechanism.

### Variants

| File | When to use |
|------|-------------|
| `sentrix-logo-full.svg` | Default logo with black circle background. Use on any background. |
| `sentrix-logo-transparent.svg` | No circle. Use when you need the mark on a solid brand-colored surface. |
| `sentrix-logo-mono-black.svg` | All-black. For print, light backgrounds, embossing, single-color output. |
| `sentrix-logo-mono-white.svg` | All-white. For dark brand-colored backgrounds, invoices, watermarks. |
| `sentrix-mark-tight.svg` | Tight-cropped diamond (no padding). For banner compositions where logo sits next to a wordmark. |

---

## Folder Structure

```
brand-kit/
├── README.md                  ← Quick overview & CDN links
├── LICENSE                    ← Proprietary brand license
├── BRAND_GUIDE.md             ← This file
│
├── svg/                       ← Master vector files
│   ├── sentrix-logo-full.svg
│   ├── sentrix-logo-transparent.svg
│   ├── sentrix-logo-mono-black.svg
│   ├── sentrix-logo-mono-white.svg
│   └── sentrix-mark-tight.svg
│
├── png-full/                  ← Full logo (with circle) — 16, 32, 64, 128, 256, 512, 1024, 2048, 4096
├── png-transparent/           ← Transparent logo (no circle) — same sizes
├── mono/                      ← Black & white variants — 256, 512, 1024
│
├── favicon/                   ← Complete web favicon set
│   ├── favicon.ico            ← Multi-resolution 16/32/48/64
│   ├── favicon-16x16.png
│   ├── favicon-32x32.png
│   ├── apple-touch-icon.png   ← 180×180 (iOS)
│   ├── android-chrome-192x192.png
│   ├── android-chrome-512x512.png
│   ├── mstile-150x150.png     ← Windows tile
│   ├── safari-pinned-tab.svg  ← Monochrome mask
│   ├── site.webmanifest       ← PWA manifest
│   └── html-head-snippet.html ← Ready-to-paste <head> tags
│
├── exchange/                  ← Token listing & DEX tokenlist assets
│   ├── coingecko-200.png
│   ├── coinmarketcap-200.png
│   ├── coinmarketcap-32.png
│   ├── trustwallet-256.png
│   ├── tokenlist-32.png       ← Uniswap / PancakeSwap tokenlist
│   ├── tokenlist-128.png
│   ├── tokenlist-256.png
│   └── listing-full-512.png
│
├── social/                    ← Social media kit
│   ├── twitter-avatar-400.png
│   ├── twitter-banner-1500x500.png
│   ├── twitter-banner-iconly-1500x500.png
│   ├── twitter-card-1200x675.png
│   ├── discord-avatar-512.png
│   ├── discord-avatar-1024.png
│   ├── telegram-512.png
│   ├── github-500.png
│   ├── github-social-1280x640.png
│   ├── linkedin-400.png
│   ├── linkedin-banner-1584x396.png
│   ├── youtube-avatar-800.png
│   ├── youtube-banner-2560x1440.png
│   ├── og-image-1200x630.png     ← Link preview (WhatsApp, FB, LinkedIn)
│   └── og-image-iconly-1200x630.png
│
└── app-icon/                  ← Mobile app store
    ├── ios-appstore-1024.png
    ├── android-playstore-512.png
    ├── android-adaptive-foreground-432.png
    └── android-adaptive-background-432.png
```

---

## Usage Guidelines

### Do ✓

- Use **SVG** whenever possible — it's vector and scales infinitely
- Use the **transparent variant** when placing the logo on a non-black background
- Maintain minimum clear space equal to **20% of the mark diameter** around the logo
- Use on pure black (`#000000`) or deep canvas (`#0A0A0C`) backgrounds for best contrast
- Use the mono-white variant on dark brand-colored backgrounds
- Use the mono-black variant on light / paper / print applications
- Reference the full official name **"Sentrix Chain"** on first mention in formal documents

### Don't ✗

- Don't rotate, mirror, or skew the diamond
- Don't change the bronze/gold ratio (both colors must be present in the color variant)
- Don't add drop shadows, glows, gradients, or effects to the logo
- Don't place the logo on busy photographic backgrounds without a solid container
- Don't use low-res PNGs when SVG is available
- Don't recolor to arbitrary hex values outside the defined palette
- Don't stretch or distort — always scale proportionally
- Don't use "Sentrix Chain" and "Sentrix" interchangeably within the same formal document
- Don't invent a wordmark font; use the system sans-serif used in the kit (DejaVu Sans Bold) or replace with your brand's font only when integrated into a broader marketing material

---

## Minimum Sizes

| Use | Minimum |
|-----|---------|
| Digital display | 24×24 px |
| Favicon | 16×16 px (use `favicon-16x16.png`) |
| Print | 10mm × 10mm |
| Embossing / etching | 15mm × 15mm |

Below 24 px, prefer the mono variant or `safari-pinned-tab.svg` silhouette for clarity.

### Clear Space

Maintain clear space around the logo equal to **20% of the circle diameter** (or mark height if using the transparent variant). No other visual elements, text, or imagery should intrude into this space.

---

## Web Integration

### HTML `<head>` snippet

The ready-to-paste snippet is in [`favicon/html-head-snippet.html`](favicon/html-head-snippet.html). Copy its contents into the `<head>` of your landing page. Remember to adjust the `https://sentrixchain.com` URLs to match your deployment environment (staging, etc.).

### PWA Manifest

The `favicon/site.webmanifest` file is configured for Sentrix Chain's PWA identity. It includes:
- App name: **Sentrix Chain**
- Theme color: `#000000`
- Background color: `#000000`
- Standalone display mode
- Adaptive Android icons (maskable)

---

## Exchange Listing Checklist

When submitting Sentrix Chain tokens to exchanges and aggregators, use:

| Platform | Asset | Notes |
|----------|-------|-------|
| CoinGecko | `exchange/coingecko-200.png` | 200×200 PNG, transparent preferred |
| CoinMarketCap (main) | `exchange/coinmarketcap-200.png` | 200×200 |
| CoinMarketCap (small) | `exchange/coinmarketcap-32.png` | 32×32 for rankings |
| Trust Wallet | `exchange/trustwallet-256.png` | 256×256 transparent |
| Uniswap tokenlist | `exchange/tokenlist-32.png` | + 128 + 256 |
| PancakeSwap tokenlist | `exchange/tokenlist-32.png` | Same standard |
| chainlist.org | `png-full/sentrix-128.png` + SVG | Plus RPC endpoint & chain ID |

### Required Metadata for Listings

| Field | Value |
|-------|-------|
| Project Name | Sentrix Chain |
| Chain ID | 7119 |
| Native Unit | sentri (1 SRX = 100,000,000 sentri) |
| Consensus | DPoS + BFT |
| Website | https://sentrixchain.com |
| Block Explorer | https://scan.sentrixchain.com |
| Documentation | https://docs.sentrixchain.com |
| GitHub | https://github.com/sentrix-labs |

### Token Differentiation

Sentrix Chain has **three distinct tokens**. For exchange listings, each should have its own icon to avoid user confusion:

| Token | Role | Icon status |
|-------|------|-------------|
| **SRX** | Consensus / staking (native) | ✅ Uses the primary Sentrix Chain logo |
| **SNTX** | Gas token (with burn mechanics) | ⚠️ Separate variant needed (TODO) |
| **SRTX** | CDP-backed stablecoin (SRC-20) | ⚠️ Separate variant needed (TODO) |

**TODO:** Design SNTX and SRTX token-specific variants before submitting to exchanges. Using the same logo for all three tokens will cause confusion for both users and exchange reviewers.

---

## On-Chain Namespace (Phase 2 Roadmap)

Sentrix Chain will launch a native name service in Phase 2:

- **Service name:** Sentrix Name Service (SNS)
- **Namespace:** `.sentrix` (e.g., `satya.sentrix`, `usdt.sentrix`)
- **Purpose:** Human-readable identifiers for wallet addresses, smart contracts, validators, and profiles
- **Status:** Roadmap item, not yet deployed

This is **distinct** from the web DNS domain `sentrixchain.com`. The `.sentrix` namespace works on-chain inside wallets and dApps; it does **not** resolve in conventional web browsers.

---

## Trademark

**"Sentrix"** and **"Sentrix Chain"** are trademarks of **Sentrix Labs**.

---

## Contact

For brand-related inquiries, permissions beyond the scope of the LICENSE, or partnership discussions:

- **Website:** [sentrixchain.com](https://sentrixchain.com)
- **GitHub:** [@sentrix-labs](https://github.com/sentrix-labs)
- **Developer / Maintainer:** [@satyakwok](https://github.com/satyakwok) / [@satyakwok](https://x.com/satyakwok)

---

*Sentrix Chain — Indonesian L1 Blockchain.*
*Brand kit v1.0 · © 2026 Sentrix Labs · All rights reserved.*
