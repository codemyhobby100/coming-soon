# XCROWMART Design System & Brand Guidelines
> This file is the single source of truth for all UI/UX decisions 
> on the XCROWMART project. Read and follow this before writing 
> any component, page, or style.

---

## Brand Identity

**Product:** XCROWMART  
**Type:** Peer-to-peer Web3 digital marketplace  
**Tagline:** The Web3 Marketplace. Powered by Escrow.  
**Audience:** Crypto traders, Web3 merchants, DeFi users, 
digital asset buyers and sellers globally  
**Tone:** Confident, trustworthy, modern, Web3-native. 
Clear and direct — no fluff, no jargon overload.

---

## Color System

These are the ONLY colors allowed in this project.
No Tailwind default color classes (blue-500, purple-400 etc.)
No multi-color gradients. No rainbow effects.

| Name          | Value     | Usage                          |
|---------------|-----------|--------------------------------|
| bg-base       | #00091a   | Every section background       |
| bg-elevated   | #00112a   | Cards, panels, elevated surfaces|
| bg-card       | #000d24   | Dashboard interiors, deep cards |
| bg-footer     | #000d1f   | Footer only                    |
| accent        | #2dc7ff   | Primary accent — all highlights|
| accent-dark   | #00a1ff   | Gradient end, secondary accent |
| accent-light  | #60d8ff   | Lighter tint, gradient via     |
| text-primary  | white/85  | rgba(255,255,255,0.85)         |
| text-muted    | white/40  | rgba(255,255,255,0.40)         |
| text-subtle   | white/20  | rgba(255,255,255,0.20)         |
| border        | white/6   | rgba(255,255,255,0.06)         |
| border-accent | #2dc7ff/20| rgba(45,199,255,0.20)          |
| glow          | #2dc7ff/5 | rgba(45,199,255,0.05) blur     |

### CSS Variables (defined in globals.css)
```css
:root {
  --xcrow-bg: #00091a;
  --xcrow-elevated: #00112a;
  --xcrow-card: #000d24;
  --xcrow-footer: #000d1f;
  --xcrow-blue: #2dc7ff;
  --xcrow-blue-dark: #00a1ff;
  --xcrow-blue-light: #60d8ff;
}
```

### Gradient Recipes

Gradient text:
bg-gradient-to-r from-[#2dc7ff] via-[#60d8ff] to-[#00a1ff]
bg-clip-text text-transparent
Gradient button bg:
bg-gradient-to-r from-[#2dc7ff] to-[#00a1ff]
Gradient border glow (via box-shadow):
shadow-[0_0_24px_rgba(45,199,255,0.3)]
Ambient orb:
bg-[#2dc7ff]/[0.05] blur-[120px] rounded-full


### FORBIDDEN
Never use these anywhere in the project:
- purple, pink, orange, green, red, indigo, violet, 
  rose, amber, emerald, yellow, cyan (Tailwind defaults)
- bg-black, bg-zinc-900, bg-gray-900, bg-[#030303]
- Multi-color or rainbow gradients
- dark: variant classes that introduce different dark colors

---

## Become a Merchant Page
- Location: /become-merchant
- Components: features/become-merchant/
- Uses vertical timeline for MerchantSteps
- FAQ uses single-open accordion pattern
- MerchantCTA uses ElegantShapes + dot grid
- Featured testimonial card sits above 3-col grid

## Typography

| Role          | Font          | Weight | Size (desktop) | Size (mobile) |
|---------------|---------------|--------|----------------|---------------|
| H1            | Space Grotesk | 800    | 64-72px        | 36px          |
| H2            | Space Grotesk | 700    | 48-56px        | 28px          |
| H3 / titles   | Space Grotesk | 600    | 20-24px        | 18px          |
| Body          | Montserrat    | 400    | 15-16px        | 14px          |
| Labels/eyebrow| Space Grotesk | 500    | 11px           | 10px          |
| Buttons       | Space Grotesk | 700    | 14px           | 13px          |
| Tags/pills    | Montserrat    | 500    | 11px           | 10px          |

Line heights:
- Headings: 1.05–1.15
- Body: 1.7–1.8
- Labels: 1.0 (no line height needed)

Letter spacing:
- Labels/eyebrows: tracking-[0.2em]
- Buttons: tracking-[0.05em]
- Body: normal

---

## Spacing System

Section padding:
- Desktop: py-24 md:py-32
- Mobile:  py-16 px-4

Container:
- max-w-7xl mx-auto px-4 sm:px-6 lg:px-8

Gap scale used:
- Card grids: gap-4 (desktop) gap-3 (mobile)
- Content within cards: gap-3 to gap-6
- Section internal: gap-8 to gap-16
- Between label → H2 → subtext: gap-4

---

## Component Patterns

### Section Wrapper Pattern
Every section uses this structure:
```tsx
<section className="relative bg-[#00091a] py-24 md:py-32 
  overflow-hidden">
  
  {/* Ambient orb */}
  <div className="absolute top-1/2 left-1/4 -translate-y-1/2 
    w-[500px] h-[500px] rounded-full bg-[#2dc7ff]/[0.04] 
    blur-[120px] pointer-events-none" />

  {/* Top blend */}
  <div className="absolute top-0 left-0 right-0 h-32 
    bg-gradient-to-b from-[#00091a] to-transparent 
    pointer-events-none z-10" />

  {/* Content */}
  <div className="relative z-10 max-w-7xl mx-auto 
    px-4 sm:px-6 lg:px-8">
    {/* section content */}
  </div>

  {/* Bottom blend */}
  <div className="absolute bottom-0 left-0 right-0 h-32 
    bg-gradient-to-t from-[#00091a] to-transparent 
    pointer-events-none z-10" />

</section>
```

### Eyebrow Label Pattern
```tsx
<span className="inline-flex items-center gap-2 
  text-[11px] font-[Space_Grotesk] font-medium 
  uppercase tracking-[0.2em] text-[#2dc7ff] mb-4">
  <span className="w-6 h-px bg-[#2dc7ff]" />
  LABEL TEXT HERE
  <span className="w-6 h-px bg-[#2dc7ff]" />
</span>
```

### Section Headline Pattern
```tsx
<h2 className="font-[Space_Grotesk] font-bold 
  text-[48px] leading-[1.1]">
  <span className="text-white/90">Plain white line</span>
  <br />
  <span className="bg-clip-text text-transparent 
    bg-gradient-to-r from-[#2dc7ff] via-[#60d8ff] 
    to-[#00a1ff]">
    Gradient blue line
  </span>
</h2>
```

### Card Pattern (Glassmorphism)
```tsx
<div className="bg-white/[0.02] border border-white/[0.06] 
  rounded-2xl p-6 relative overflow-hidden
  hover:border-[#2dc7ff]/[0.25]
  hover:shadow-[0_0_40px_rgba(45,199,255,0.07)]
  transition-all duration-300">

  {/* Top highlight line */}
  <div className="absolute top-0 left-8 right-8 h-px 
    bg-gradient-to-r from-transparent 
    via-[#2dc7ff]/[0.25] to-transparent" />

  {/* Card content */}
</div>
```

### Elevated Card Pattern (for dashboard/panel cards)
```tsx
<div className="bg-[#00112a] border border-white/[0.06] 
  rounded-2xl overflow-hidden">
  {/* content */}
</div>
```

### Icon Box Pattern
```tsx
{/* Large (12x12) */}
<div className="w-12 h-12 rounded-2xl flex items-center 
  justify-center bg-gradient-to-br from-[#2dc7ff]/[0.15] 
  to-transparent border border-[#2dc7ff]/[0.15]">
  <Icon className="w-6 h-6 text-[#2dc7ff]" />
</div>

{/* Small (10x10) */}
<div className="w-10 h-10 rounded-xl flex items-center 
  justify-center bg-[#2dc7ff]/[0.08] 
  border border-[#2dc7ff]/[0.12]">
  <Icon className="w-5 h-5 text-[#2dc7ff]" />
</div>
```

### Primary Button Pattern
```tsx
<button className="group inline-flex items-center gap-2 
  px-8 py-4 rounded-xl font-bold text-[14px]
  font-[Space_Grotesk] tracking-wide
  bg-gradient-to-r from-[#2dc7ff] to-[#00a1ff]
  text-[#00091a]
  shadow-[0_0_20px_rgba(45,199,255,0.25)]
  hover:shadow-[0_0_40px_rgba(45,199,255,0.45)]
  hover:scale-[1.02] active:scale-[0.98]
  transition-all duration-200
  ease-[cubic-bezier(0.34,1.56,0.64,1)]
  min-h-[52px]">
  Button Text
  <ArrowRight className="w-4 h-4 group-hover:translate-x-1 
    transition-transform duration-200" />
</button>
```

### Ghost Button Pattern
```tsx
<button className="inline-flex items-center gap-2 
  px-8 py-4 rounded-xl text-[14px] font-medium
  font-[Space_Grotesk] tracking-wide
  text-[#2dc7ff]
  border border-[#2dc7ff]/[0.25]
  bg-[#2dc7ff]/[0.04]
  hover:bg-[#2dc7ff]/[0.08]
  hover:border-[#2dc7ff]/[0.5]
  transition-all duration-200
  min-h-[52px]">
  Button Text
</button>
```

### Badge/Pill Pattern
```tsx
{/* Eyebrow badge */}
<div className="inline-flex items-center gap-2 px-4 py-1.5 
  rounded-full bg-[#2dc7ff]/[0.06] 
  border border-[#2dc7ff]/[0.2]
  shadow-[0_0_20px_rgba(45,199,255,0.06)]">
  <span className="w-1.5 h-1.5 rounded-full 
    bg-[#2dc7ff] animate-pulse" />
  <span className="text-[11px] text-[#2dc7ff] uppercase 
    tracking-[0.2em] font-medium font-[Space_Grotesk]">
    BADGE TEXT
  </span>
</div>

{/* Info pill */}
<div className="inline-flex items-center gap-2 px-3 py-1.5 
  rounded-xl bg-white/[0.03] border border-white/[0.06] 
  backdrop-blur-sm">
  <Icon className="w-3.5 h-3.5 text-[#2dc7ff]" />
  <span className="text-[12px] text-white/45 
    font-[Montserrat]">
    Pill text
  </span>
</div>
```

---

## Background System

### Ambient Orbs
Place 1–2 per section, never more:
```tsx
{/* Primary orb */}
<div className="absolute top-1/4 left-1/4 
  w-[500px] h-[500px] rounded-full 
  bg-[#2dc7ff]/[0.04] blur-[120px] 
  pointer-events-none" />

{/* Secondary orb */}
<div className="absolute bottom-1/4 right-1/4 
  w-[400px] h-[400px] rounded-full 
  bg-[#00a1ff]/[0.03] blur-[100px] 
  pointer-events-none" />
```

Mobile: reduce to 50% size and halve opacity.

### ElegantShapes
Import from @/components/ui/shape-landing-hero
Use ONLY these gradient values on shapes:
- "from-[#2dc7ff]/[0.12]"
- "from-[#00a1ff]/[0.10]"
- "from-[#60d8ff]/[0.08]"
- "from-[#2dc7ff]/[0.06]"

Max 4 shapes per section on desktop.
Max 2 shapes on mobile (hide others with hidden sm:block).

### Dot Grid Pattern
```tsx
<div className="absolute inset-0 pointer-events-none"
  style={{
    backgroundImage: `radial-gradient(circle, 
      rgba(45,199,255,0.12) 1px, transparent 1px)`,
    backgroundSize: '28px 28px',
    opacity: 0.03
  }} 
/>
```

### Section Transitions
Every section (except first and footer) needs:
- Top blend: bg-gradient-to-b from-[#00091a] to-transparent
- Bottom blend: bg-gradient-to-t from-[#00091a] to-transparent
- Height: h-32 absolute inset-x-0 pointer-events-none

---

## Animation System

### Core Variants
```tsx
export const sectionVariants = {
  hidden: { opacity: 0, y: 40 },
  visible: { 
    opacity: 1, y: 0,
    transition: { 
      duration: 0.8, 
      ease: [0.25, 0.46, 0.45, 0.94] 
    }
  }
}

export const containerVariants = {
  hidden: {},
  visible: { 
    transition: { 
      staggerChildren: 0.1, 
      delayChildren: 0.15 
    }
  }
}

export const cardVariants = {
  hidden: { opacity: 0, y: 24 },
  visible: { 
    opacity: 1, y: 0,
    transition: { 
      duration: 0.6, 
      ease: [0.25, 0.46, 0.45, 0.94] 
    }
  }
}

export const fadeUpVariants = {
  hidden: { opacity: 0, y: 30 },
  visible: (i: number) => ({
    opacity: 1, y: 0,
    transition: {
      duration: 1,
      delay: 0.5 + i * 0.2,
      ease: [0.25, 0.4, 0.25, 1],
    },
  }),
}
```

### Usage Rules
- All sections: whileInView + viewport={{ once: true }}
- Cards: whileHover={{ y: -3 }} transition duration 0.2
- Primary buttons: whileHover={{ scale: 1.02 }} 
  whileTap={{ scale: 0.97 }}
- Always respect prefers-reduced-motion:
```tsx
const shouldReduce = useReducedMotion()
// If true: set all durations to 0
```

### Float Animation (for decorative elements)
```tsx
animate={{ y: [0, 12, 0] }}
transition={{ 
  duration: 6, 
  repeat: Infinity, 
  ease: "easeInOut" 
}}
```

---

## Responsive Breakpoints

| Breakpoint | Width    | Tailwind prefix |
|------------|----------|-----------------|
| Mobile     | < 640px  | default         |
| Tablet     | 640–1024 | sm: md:         |
| Desktop    | > 1024px | lg:             |

### Mobile Rules (always apply)
- overflow-x: hidden on all sections
- Section padding: py-16 px-4
- H1: text-[36px], H2: text-[28px]
- All grids → grid-cols-1 unless specified
- All CTA buttons → w-full flex-col
- Ambient orbs → 50% smaller, opacity halved
- ElegantShapes → max 2 visible (hidden sm:block on rest)
- Decorative bg numbers → hidden
- All interactive elements → min 44x44px touch target
- Remove hover effects: wrap in @media (hover: hover)

### Performance on Mobile
```css
@media (max-width: 640px) {
  body { overflow-x: hidden; }
  * { will-change: auto !important; }
}

@media (hover: hover) {
  /* All hover styles go here */
}
```

---

## Page-Level Background
All pages share the same seamless background:
- Base: bg-[#00091a] on <body> and every <section>
- Footer only: bg-[#000d1f]
- No page should have any white, gray or 
  alternative dark background

---

## Accessibility Standards
Every interactive component must have:
```tsx
className="focus-visible:outline-none 
  focus-visible:ring-2 
  focus-visible:ring-[#2dc7ff]/50
  focus-visible:ring-offset-2
  focus-visible:ring-offset-[#00091a]"
```

ARIA labels on all icon-only buttons.
Semantic HTML: section, nav, main, footer, article, h1–h3.
Color contrast: all text meets WCAG AA minimum.

---

## Skeleton Loading Pattern
```tsx
<div className="animate-pulse rounded-2xl bg-white/[0.03]"
  style={{
    background: `linear-gradient(
      90deg,
      transparent 0%,
      rgba(45,199,255,0.04) 50%,
      transparent 100%
    )`,
    backgroundSize: '200% 100%',
    animation: 'shimmer 1.5s infinite'
  }}
/>
```

---

## File Structure

---

## What This Project Is

XCROWMART is a peer-to-peer digital marketplace where 
merchants and traders buy and sell crypto tools, assets, 
and resources — protected by a built-in escrow system 
that ensures every transaction is safe, instant, and 
transparent.

### Core Features
1. Escrow-protected trades — funds held until confirmed
2. Instant withdrawals — no holds or waiting periods
3. Built-in merchant chat — encrypted, real-time
4. Multi-currency deposits — crypto, stablecoin or fiat
5. Multivendor marketplace — thousands of verified listings
6. Merchant program — anyone can apply and start selling

### Key Pages
- Landing page (/) — convert visitors to sign ups
- Marketplace (/marketplace) — browse and buy listings
- Become a Merchant (/become-merchant) — merchant acquisition
- Auth (/auth/login, /auth/signup) — authentication