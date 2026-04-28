# Sentrix Brand — Usage

Practical reference for picking the right asset per surface. See `BRAND_GUIDE.md` for the underlying design system; this doc is the cheat-sheet.

## Header logo (web nav, app shells)

**Use:** `avatars/single-ring-transparent/avatar-single-ring-transparent-{128,256,512}.png`

This is the canonical "Sentrix mark" composition: bronze ring + bronze diamond + 4 gold pearl dots at cardinal points, transparent background. It reads as a recognizable coin/seal at any size — including small navbar (50px) and footer (28px) display.

**Why not the SVG?** `svg/sentrix-mark-tight.svg` and `svg/sentrix-logo-transparent.svg` define the pearl dots at radius 11 on a 1024 viewBox. At header sizes (50px), the dots scale to ~2-3px and disappear. The PNG avatars are pre-rendered at each size with proportions that hold up.

**Sizes & responsive srcSet:**
- Navbar primary: 40–56px → ship 128/256/512 srcSet
- Footer / inline: 24–32px → ship 64/128 srcSet
- Hero stamps: 200px+ → use 512 or 1024

```tsx
<img
  src="/brand/coin-ring-512.png"
  srcSet="/brand/coin-ring-128.png 128w, /brand/coin-ring-256.png 256w, /brand/coin-ring-512.png 512w"
  sizes={`${size}px`}
  alt="Sentrix Chain"
  width={size}
  height={size}
/>
```

**Reference implementation:** `sentriscloud-frontend/apps/chain-landing/src/components/ui/logo.tsx`

## Hero coin / asset stamp (Solux balance, Faucet hero)

**Use:** `avatars/solid-bronze-gold/avatar-solid-bronze-gold-{256,512,1024}.png`

Solid bronze disc with gold diamond. Heavier visual weight than the ring variant — meant to read as a "coin" stamp in product UI (wallet balances, faucet hero, asset cards), not as a brand logo-mark.

The two variants split duties:
- **Ring** = brand identity (header/footer). Recognition.
- **Solid** = asset/value stamp (in-product). Presence.

Don't mix — using the solid variant in the navbar makes the brand feel heavy; using the ring variant as a hero stamp makes the value feel thin.

## Wordmark adjacency

When the mark sits next to the "SENTRIX" wordmark (which is the standard header treatment): mark height = wordmark cap-height × 1.2, gap = ¼ × mark height.

## Favicon / app icon

`favicon/` and `app-icon/` are pre-baked. Don't generate from SVG — the rasterizer in design tools blows out the 11px-radius pearl dots.

## Don't

- Don't recolor outside palette (`#8A5A11` bronze, `#DBC17F` gold, `#000000` black)
- Don't add drop-shadow, glow, or gradient overlays to the mark
- Don't stretch (preserve square aspect)
- Don't place the ring variant on a busy/photo background — it needs flat dark canvas
- Don't use `svg/sentrix-mark-tight.svg` at < 96px display size — pearl dots disappear

## Reference implementations

Match these surfaces when building new product chrome:

- **Header logo (gold standard):** sentrixchain.com nav — ring variant @ 50px
- **Hero coin stamp:** faucet.sentrixchain.com — solid variant @ 256px
- **Wallet balance stamp:** solux.sentriscloud.com — solid variant @ inline-height
- **Compact data label:** explorer asset-cards — 24px ring inline with mono ticker
