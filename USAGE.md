# Sentrix Brand — Usage

Practical reference for picking the right asset per surface. See `BRAND_GUIDE.md` for the underlying design system; this doc is the cheat-sheet.

## Logo hierarchy

The Sentrix mark has three visual contexts plus a favicon track. Pick by surface, not by preference — using the wrong variant in the wrong place is the most common brand inconsistency.

| Context | Mark | Wordmark | When |
|---|---|---|---|
| **1. Default / brand** | Ring + diamond + 4 pearl dots (`avatars/single-ring-transparent/*.png`) | `SENTRIX` serif uppercase, minimal letter-spacing (≤ 0.05em), font-light | Top navigation, footer, anywhere the mark sits next to a wordmark. The pearl-dots circle is the signature element — strip it and the diamond reads as a generic rotated square. |
| **2. Hero / display** | Same as default (ring + dots) | Wordmark scales up: serif uppercase, larger letter-spacing OK, font-light or font-normal | Landing hero, splash screens, social cards. Hero context has room for wider tracking. |
| **3. Asset / value stamp** | Solid bronze coin face (`avatars/solid-bronze-gold/*.png`) | (none — used inline alongside numeric value) | Wallet balance pucks, faucet hero coin, asset cards. Reads as a "coin" stamp — heavier visual weight than the ring. |
| **4. Favicon / app icon** | Pre-rasterized mark (`favicon/`, `app-icon/`) | n/a | Browser tabs, home screen, app launcher. Don't generate from SVG — the rasterizer blows out 11px-radius pearl dots. |

The ring + pearl dots is the brand signature. Strip it only when there's a real legibility problem at < 24px — and even then, prefer raising the size to recovering the brand.

## 1. Default / nav / footer

**Mark:** `avatars/single-ring-transparent/avatar-single-ring-transparent-{128,256,512}.png`

Bronze ring + bronze diamond + 4 gold pearl dots, transparent background. The PNGs are pre-rasterized at each size with proportions that hold up — pearl dots stay visible from 32px up.

**Wordmark:** `SENTRIX` all caps, serif (Playfair or the brand serif), letter-spacing ≤ 0.05em (NOT the wide editorial 0.25em — that reads as a section eyebrow, not a brand mark, in a nav context), font-weight 300-400 (light to normal), color brand gold.

**Sizing — mark slightly larger than wordmark cap-height for visual balance:**
- Desktop nav: mark 36-40px, wordmark 20-24px serif at `font-light`
- Mobile nav: mark 32-36px, wordmark 18-22px
- Footer: mark 26-30px, wordmark 14-18px (same family, smaller)
- Gap mark↔wordmark: 10-14px (`gap-2.5` or `gap-3` in Tailwind)
- Container: `flex items-center` — visual centers align cleanly because the mark is round-ish (ring) and the text is centered within its line-box

```tsx
// Reference: apps/chain-landing/src/components/sections/navbar.tsx
<a href="#" className="flex items-center gap-3 text-[var(--gold)]">
  <SentrixLogo size={38} />
  <span className="font-serif text-[22px] font-light tracking-[.04em] uppercase text-[var(--gold)] leading-none">
    SENTRIX
  </span>
</a>
```

## 2. Hero / display

Same mark, scaled to 96-200px+. Wordmark in the surrounding hero composition can use wider letter-spacing (up to 0.15em) because the larger font size gives the wide tracking room to breathe without losing legibility.

The constraint is the OPPOSITE of nav: the ring + pearl dots want air around them. A hero context delivers that air.

## 3. Asset / value stamp

**Use:** `avatars/solid-bronze-gold/avatar-solid-bronze-gold-{256,512,1024}.png`

Solid bronze disc with gold diamond. No ring, no pearl dots. Heavier visual weight than the brand variant — meant to read as a "coin" stamp in product UI (wallet balances, faucet hero coin, asset cards), not as a brand logo-mark.

Ring vs solid split:
- **Ring** (variants 1 + 2) = brand identity. Recognition.
- **Solid** (variant 3) = asset/value. Presence.

Don't mix — the solid variant in nav chrome reads as heavy and confused with content; the ring variant on a wallet balance feels thin and decorative.

## 4. Favicon / app icon

`favicon/` and `app-icon/` are pre-baked at standard sizes. Don't generate from SVG at runtime — the rasterizer in design tools blows out the 11px-radius pearl dots and you get the "polos" (bare) diamond problem.

## Compact-only fallback (rarely used)

`svg/sentrix-mark-header.svg` is a stripped dual-diamond — no ring, no pearl dots — for ultra-compact contexts (≤ 20px display) where the pearl dots really can't fit. It exists as a fallback option, not a default. If you find yourself reaching for it, first try raising the surrounding size — the pearl-dots PNG is the brand mark, the stripped diamond is a substitute.

## Don't

- Don't recolor outside palette (`#8A5A11` bronze, `#DBC17F` gold, `#000000` black)
- Don't add drop-shadow, glow, or gradient overlays to the mark
- Don't stretch (preserve square aspect)
- Don't place the ring variant on a busy/photo background — it needs flat dark canvas
- Don't use `svg/sentrix-mark-tight.svg` at < 96px display size — pearl dots disappear (use the PNG variants instead)
- Don't pair the brand mark with the wordmark wide-tracked (`tracking-[.25em]`+) in a horizontal nav — the wide tracking belongs in hero, not chrome
- Don't pair the brand mark with mixed-case "Sentrix" wordmark — the mark is iconic, the wordmark should match its formality with `SENTRIX` all-caps

## Reference implementations

Surfaces to match when building new product chrome:

| Surface | Mark | Wordmark | Notes |
|---|---|---|---|
| sentrixchain.com nav | ring @ 38px | `SENTRIX` Playfair 22px font-light tracking-[.04em] | Default brand chrome |
| sentrixchain.com hero | (no inline mark — wordmark only) | `SENTRIX` Playfair 96px font-light tracking-[.05em] uppercase | Editorial display |
| sentrixchain.com footer | ring @ 28px | `SENTRIX` Playfair 16px font-light tracking-[.04em] | Smaller proportional version of nav |
| scan.sentrixchain.com nav | ring @ 32px | `SENTRIX` Playfair 18px font-light + sans `Scan` subtitle | Sub-brand pattern |
| faucet.sentrixchain.com hero | solid @ 96px | `Sentrix Faucet` Playfair 44px tracking-tight | Hero context, solid coin stamp |
| solux.sentriscloud.com balance | solid @ inline | inline alongside SRX numeric | Asset stamp |
| explorer asset cards | ring @ 24px | inline alongside ticker | Compact data row |
