# Sentrix Brand — Usage

Practical reference for picking the right asset per surface. See `BRAND_GUIDE.md` for the underlying design system; this doc is the cheat-sheet.

## Logo hierarchy

The Sentrix mark has four contexts. Pick by surface, not by preference — using the wrong variant in the wrong place is the most common brand inconsistency.

| Context | What | Variant | When |
|---|---|---|---|
| **1. Header / nav** | Compact mark + sans-serif wordmark | `svg/sentrix-mark-header.svg` | Top navigation, breadcrumb chrome, anywhere the mark sits next to a wordmark in a horizontal layout. The Solana / Vercel / Stripe pattern. |
| **2. Ceremonial / hero** | Full ring + diamond + 4 pearl dots | `avatars/single-ring-transparent/*.png` | Hero stamps, landing splash, splash screens, social cards. The "this is the brand" moment. |
| **3. Asset / value stamp** | Solid bronze coin face | `avatars/solid-bronze-gold/*.png` | Wallet balance pucks, faucet hero, asset cards. Reads as a "coin" — heavier visual weight than the ring. |
| **4. Favicon / app icon** | Pre-rasterized mark | `favicon/`, `app-icon/` | Browser tabs, home screen, app launcher. Don't generate from SVG — the rasterizer blows out 11px-radius pearl dots. |

The header variant is the most common; default to it unless you have a reason to escalate to ceremonial.

## 1. Header logo (web nav, app shells)

**Use:** `svg/sentrix-mark-header.svg`

This is the dual-diamond stripped of decorative ring + pearl dots. Outer outline + inner filled diamond, both bronze. Stroke is widened to 6% of the viewBox so the outline reads cleanly down to 24px display.

**Why not the full mark or ceremonial PNG?**
- `sentrix-mark-tight.svg` and the full-circle variants define pearl dots at radius 11 on a 1024 viewBox. At nav sizes (24-36px) the dots scale to ~1-2px and disappear; the ring competes with the wordmark for visual weight; both fight for attention with no payoff.
- `single-ring-transparent` PNGs are designed for ceremonial display — the ring + dots want space around them to breathe.

**Sizing — match wordmark cap-height:**
- Desktop nav: mark 24-28px, wordmark 16-18px sans-serif at `font-semibold`
- Mobile nav: mark 22-26px, wordmark 14-16px sans-serif at `font-semibold`
- Footer: mark 20-24px, wordmark 14-16px (same family, smaller)
- Gap mark↔wordmark: 8-10px (`gap-2` or `gap-2.5` in Tailwind)
- Letter-spacing: `tracking-tight` (`-0.01em`) — never wide-tracked uppercase. Wide tracking is for hero ceremonial moments, not nav chrome.
- Wordmark casing: mixed-case "Sentrix", not all-caps "SENTRIX". All-caps reads as a section eyebrow, not a brand mark, in a nav context.

```tsx
// Reference: apps/chain-landing/src/components/sections/navbar.tsx
<a href="#" className="flex items-center gap-2.5 text-[var(--gold)]">
  <SentrixLogo size={26} variant="header" />
  <span className="text-[18px] font-semibold tracking-[-0.01em] text-[var(--gold)]">
    Sentrix
  </span>
</a>
```

## 2. Ceremonial / hero coin

**Use:** `avatars/single-ring-transparent/avatar-single-ring-transparent-{256,512,1024}.png`

Bronze ring + bronze diamond + 4 gold pearl dots, transparent background. This is the iconic Sentrix "seal" — it wants air around it and a moment of attention.

**When:** landing hero adjacent to a serif Playfair display title; faucet hero stamp; docs splash; social cards. The full ring + dot composition needs a hero-sized canvas (200px+) for the dots to register as deliberate brand detail rather than noise.

**Don't:** put the ceremonial variant in nav chrome. It clutters at small sizes and undercuts the editorial tone of the wordmark.

## 3. Asset / value stamp

**Use:** `avatars/solid-bronze-gold/avatar-solid-bronze-gold-{256,512,1024}.png`

Solid bronze disc with gold diamond. Heavier visual weight than the ring variant — meant to read as a "coin" stamp in product UI (wallet balances, faucet hero coin, asset cards), not as a brand logo-mark.

The ring vs solid split:
- **Ring** (variant 2) = brand identity. Recognition.
- **Solid** (variant 3) = asset/value. Presence.

Don't mix — using the solid variant as a header logo makes the brand chrome feel heavy; using the ring variant as a wallet balance stamp makes the value feel thin.

## 4. Favicon / app icon

`favicon/` and `app-icon/` are pre-baked at standard sizes. Don't generate from SVG at runtime — the rasterizer in design tools blows out the 11px-radius pearl dots and you get the "polos" diamond problem.

## Don't

- Don't recolor outside palette (`#8A5A11` bronze, `#DBC17F` gold, `#000000` black)
- Don't add drop-shadow, glow, or gradient overlays to the mark
- Don't stretch (preserve square aspect)
- Don't place the ring variant on a busy/photo background — it needs flat dark canvas
- Don't use `svg/sentrix-mark-tight.svg` at < 96px display size — pearl dots disappear
- Don't pair the header mark with a serif wide-tracked uppercase wordmark — that combo is editorial hero treatment, not nav chrome
- Don't pair the ceremonial mark with a sans-serif compact wordmark — it dilutes both

## Reference implementations

Surfaces to match when building new product chrome:

| Surface | Variant | Wordmark | Notes |
|---|---|---|---|
| sentrixchain.com nav | header @ 26px | "Sentrix" sans 18px font-semibold tracking-tight | Solana-style compact |
| sentrixchain.com hero | (no mark, hero is wordmark only) | "SENTRIX" Playfair 96px font-light tracking-[.05em] uppercase | Editorial display |
| faucet.sentrixchain.com hero | ceremonial @ 96px | "Sentrix Faucet" Playfair 44px tracking-tight | Hero context, ring + dots OK |
| solux.sentriscloud.com balance | solid @ inline | inline alongside SRX numeric | Asset stamp |
| explorer asset cards | header @ 24px | inline alongside ticker | Compact data row |
