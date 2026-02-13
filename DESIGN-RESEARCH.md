# Premium Landing Page Design Research Guide

> Compiled from analysis of Linear, Vercel, Stripe, Raycast, Arc, Dribbble trends, and 21st.dev component patterns.
> Last updated: 2026-02-14

---

## Table of Contents

1. [Color Systems](#1-color-systems)
2. [Typography](#2-typography)
3. [Spacing & Layout](#3-spacing--layout)
4. [Navigation](#4-navigation)
5. [Hero Sections](#5-hero-sections)
6. [CTA Buttons](#6-cta-buttons)
7. [Feature Sections](#7-feature-sections)
8. [Card Designs](#8-card-designs)
9. [Pricing Tables](#9-pricing-tables)
10. [Social Proof & Trust](#10-social-proof--trust)
11. [Forms](#11-forms)
12. [Animations & Micro-interactions](#12-animations--micro-interactions)
13. [Footer](#13-footer)
14. [Mobile Responsive](#14-mobile-responsive)
15. [Implementation Recommendations](#15-implementation-recommendations)

---

## 1. Color Systems

### Dark Mode (Recommended for Premium SaaS — Linear, Arc, Raycast pattern)

| Token | Hex | Usage |
|-------|-----|-------|
| `--bg-primary` | `#0A0A0B` | Page background |
| `--bg-secondary` | `#111113` | Card/section backgrounds |
| `--bg-tertiary` | `#1A1A1E` | Elevated surfaces, inputs |
| `--bg-hover` | `#232328` | Hover states |
| `--border-subtle` | `#222225` | Subtle dividers |
| `--border-default` | `#2E2E32` | Card borders |
| `--text-primary` | `#EDEDEF` | Headings |
| `--text-secondary` | `#A0A0A6` | Body text, descriptions |
| `--text-tertiary` | `#6E6E76` | Muted labels, captions |
| `--accent-primary` | `#6C5CE7` | Primary brand / CTA (purple) |
| `--accent-hover` | `#7C6FF7` | Hover state |
| `--accent-glow` | `rgba(108, 92, 231, 0.15)` | Glow/shadow effects |

### Light Mode (Vercel / Stripe pattern)

| Token | Hex | Usage |
|-------|-----|-------|
| `--bg-primary` | `#FFFFFF` | Page background |
| `--bg-secondary` | `#FAFAFA` | Alternating sections |
| `--bg-tertiary` | `#F5F5F5` | Cards, inputs |
| `--border-subtle` | `#EAEAEA` | Dividers |
| `--text-primary` | `#171717` | Headings |
| `--text-secondary` | `#666666` | Body text |
| `--accent-primary` | `#635BFF` | Stripe-style purple |

### Gradient Techniques

```css
/* Stripe-style hero gradient — vibrant, warm, diagonal sweep */
.hero-gradient-stripe {
  background: linear-gradient(135deg, #a960ee 0%, #ff6b95 25%, #ff8c42 50%, #ffcf56 75%, #6bdfb8 100%);
}

/* Linear-style subtle dark gradient */
.hero-gradient-linear {
  background: radial-gradient(ellipse 80% 50% at 50% -20%, rgba(108, 92, 231, 0.3), transparent);
}

/* Vercel-style soft light gradient */
.hero-gradient-vercel {
  background: radial-gradient(ellipse at 60% 80%, rgba(255, 150, 100, 0.25), transparent 50%),
              radial-gradient(ellipse at 40% 80%, rgba(100, 255, 200, 0.2), transparent 50%);
}

/* Purple glow behind CTAs or hero text */
.accent-glow {
  background: radial-gradient(circle at 50% 50%, rgba(108, 92, 231, 0.25) 0%, transparent 60%);
}

/* Mesh gradient (modern trend from Dribbble/21st.dev) */
.mesh-gradient {
  background:
    radial-gradient(at 20% 80%, rgba(108, 92, 231, 0.4) 0%, transparent 50%),
    radial-gradient(at 80% 20%, rgba(99, 91, 255, 0.3) 0%, transparent 50%),
    radial-gradient(at 50% 50%, rgba(120, 80, 255, 0.15) 0%, transparent 70%);
}

/* Animated gradient border (21st.dev trend) */
.gradient-border {
  background: linear-gradient(var(--bg-secondary), var(--bg-secondary)) padding-box,
              linear-gradient(135deg, #6C5CE7, #a78bfa, #6C5CE7) border-box;
  border: 1px solid transparent;
  border-radius: 12px;
}
```

---

## 2. Typography

### Font Stack

```css
/* Primary: Inter (used by Linear, Vercel, most modern SaaS) */
font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;

/* Alternative premium: Cal Sans for display headings */
/* Alternative: Geist (Vercel's custom font) */
```

### Type Scale

| Element | Size | Weight | Line Height | Letter Spacing | Color |
|---------|------|--------|-------------|----------------|-------|
| Hero H1 | `64px` / `4rem` | `700` | `1.1` | `-0.03em` | `--text-primary` |
| Section H2 | `48px` / `3rem` | `700` | `1.15` | `-0.025em` | `--text-primary` |
| Card H3 | `24px` / `1.5rem` | `600` | `1.3` | `-0.015em` | `--text-primary` |
| Subheading | `20px` / `1.25rem` | `500` | `1.4` | `-0.01em` | `--text-secondary` |
| Body Large | `18px` / `1.125rem` | `400` | `1.6` | `0` | `--text-secondary` |
| Body | `16px` / `1rem` | `400` | `1.6` | `0` | `--text-secondary` |
| Caption/Label | `14px` / `0.875rem` | `500` | `1.5` | `0.01em` | `--text-tertiary` |
| Overline/Badge | `12px` / `0.75rem` | `600` | `1.4` | `0.05em` | `--accent-primary` |

### Key Patterns

- **Negative letter-spacing on headings** (`-0.03em` to `-0.02em`) — tighter tracking = premium feel
- **Large hero text** — 56–72px on desktop, never smaller than 36px on mobile
- **Two-tone headings** — key word in accent color or gradient text:

```css
.gradient-text {
  background: linear-gradient(135deg, #EDEDEF 0%, #6E6E76 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

/* Or accent word */
.accent-word {
  color: #6C5CE7;
}
```

---

## 3. Spacing & Layout

### Spacing Scale (8px base)

| Token | Value | Usage |
|-------|-------|-------|
| `--space-1` | `4px` | Tight inline spacing |
| `--space-2` | `8px` | Icon gaps, small padding |
| `--space-3` | `12px` | Compact padding |
| `--space-4` | `16px` | Default padding |
| `--space-5` | `24px` | Card padding |
| `--space-6` | `32px` | Section inner padding |
| `--space-7` | `48px` | Between components |
| `--space-8` | `64px` | Between sections (mobile) |
| `--space-9` | `96px` | Between sections (desktop) |
| `--space-10` | `128px` | Hero vertical padding |
| `--space-11` | `160px` | Large section gaps |

### Container

```css
.container {
  max-width: 1200px;     /* Content width */
  margin: 0 auto;
  padding: 0 24px;       /* Mobile gutter */
}

@media (min-width: 768px) {
  .container { padding: 0 40px; }
}

@media (min-width: 1024px) {
  .container { padding: 0 64px; }
}

/* Full-bleed variant for backgrounds */
.section-full {
  width: 100%;
  padding: 96px 0;       /* Vertical rhythm */
}
```

### Grid Patterns

```css
/* 3-column feature grid (Linear, Vercel) */
.features-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

/* 2-column with image (Stripe pattern) */
.split-section {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 64px;
  align-items: center;
}

/* Bento grid (trending from Dribbble/21st.dev) */
.bento-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: auto;
  gap: 16px;
}
.bento-large { grid-column: span 2; grid-row: span 2; }
.bento-wide { grid-column: span 2; }
```

---

## 4. Navigation

### Pattern: Floating/Sticky Transparent Nav (Linear, Vercel, Stripe)

```css
.nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 50;
  height: 64px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 24px;
  background: rgba(10, 10, 11, 0.8);     /* Dark semi-transparent */
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
  transition: background 0.3s ease;
}

/* Light variant (Vercel) */
.nav-light {
  background: rgba(255, 255, 255, 0.8);
  border-bottom: 1px solid rgba(0, 0, 0, 0.06);
}
```

### Nav Link Styles

```css
.nav-link {
  font-size: 14px;
  font-weight: 500;
  color: var(--text-secondary);
  text-decoration: none;
  padding: 8px 12px;
  border-radius: 6px;
  transition: color 0.15s ease, background 0.15s ease;
}

.nav-link:hover {
  color: var(--text-primary);
  background: rgba(255, 255, 255, 0.06);
}
```

### Nav CTA Button

```css
.nav-cta {
  font-size: 14px;
  font-weight: 500;
  padding: 8px 16px;
  border-radius: 8px;
  background: var(--accent-primary);
  color: #FFFFFF;
  border: none;
  cursor: pointer;
  transition: opacity 0.15s ease, transform 0.1s ease;
}

.nav-cta:hover {
  opacity: 0.9;
  transform: translateY(-1px);
}
```

### Layout Pattern

```
[Logo]                    [Features] [Pricing] [FAQ]     [CTA Button]
```

- Logo left-aligned, links center or right, CTA far right
- 3–5 nav links max (Linear uses 6, but most premium sites keep it minimal)
- Mobile: hamburger menu with slide-in panel

---

## 5. Hero Sections

### Pattern A: Left-Aligned Bold Statement (Linear)

```
[Overline badge: "Now accepting new clients"]

# Business Plans That
# Close Deals.

Subtitle text in muted color, 2-3 lines max.
18-20px, max-width: 600px.

[Primary CTA]  [Secondary CTA]
```

### Pattern B: Center-Aligned with Visual Below (Vercel)

```
         [Small animated element or grid]

       Build and deploy on the AI Cloud.

  Subtitle text centered, comfortable reading width.

       [Primary CTA]  [Secondary CTA]

    [Product screenshot / gradient visual below]
```

### Pattern C: Split with Animated Visual (Stripe)

```
[Stat badge: "1.57% of Global GDP"]        [Gradient visual / 
                                              abstract art on 
Financial infrastructure                      right side, 
to grow your revenue.                         bleeding to edge]

[CTA]  [Secondary CTA]

[Logo bar: xero, amazon, nvidia...]
```

### Hero CSS

```css
.hero {
  min-height: 90vh;          /* Nearly full viewport */
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;        /* or flex-start for left-aligned */
  text-align: center;         /* or left */
  padding: 160px 24px 96px;
  position: relative;
  overflow: hidden;
}

.hero h1 {
  font-size: clamp(36px, 5vw, 72px);
  font-weight: 700;
  line-height: 1.05;
  letter-spacing: -0.03em;
  max-width: 900px;
  margin-bottom: 24px;
}

.hero .subtitle {
  font-size: clamp(16px, 1.5vw, 20px);
  color: var(--text-secondary);
  max-width: 600px;
  line-height: 1.6;
  margin-bottom: 40px;
}

/* Status badge above hero text */
.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 6px 16px;
  border-radius: 999px;
  border: 1px solid var(--border-default);
  background: var(--bg-secondary);
  font-size: 14px;
  font-weight: 500;
  color: var(--text-secondary);
  margin-bottom: 32px;
}

.hero-badge .dot {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #22C55E;
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.5; }
}
```

---

## 6. CTA Buttons

### Primary CTA (Action button — high contrast)

```css
.btn-primary {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 14px 28px;
  font-size: 16px;
  font-weight: 600;
  color: #FFFFFF;
  background: var(--accent-primary);    /* #6C5CE7 */
  border: none;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.2s ease;
  box-shadow: 0 0 0 0 rgba(108, 92, 231, 0);
}

.btn-primary:hover {
  background: var(--accent-hover);
  transform: translateY(-2px);
  box-shadow: 0 8px 25px -5px rgba(108, 92, 231, 0.4);
}

.btn-primary:active {
  transform: translateY(0);
}
```

### Secondary CTA (Ghost / outline)

```css
.btn-secondary {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  padding: 14px 28px;
  font-size: 16px;
  font-weight: 500;
  color: var(--text-primary);
  background: transparent;
  border: 1px solid var(--border-default);
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.btn-secondary:hover {
  background: var(--bg-hover);
  border-color: var(--text-tertiary);
}
```

### CTA Pair Layout

```css
.cta-group {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  justify-content: center;    /* or flex-start */
}
```

### Stripe-style Arrow CTA

```css
.btn-arrow::after {
  content: '→';
  margin-left: 4px;
  transition: transform 0.2s ease;
}

.btn-arrow:hover::after {
  transform: translateX(4px);
}
```

---

## 7. Feature Sections

### Pattern: 3-Column Icon Cards (Linear, Raycast)

```css
.features-section {
  padding: 96px 0;
}

.features-section h2 {
  text-align: center;
  margin-bottom: 16px;
}

.features-section .section-subtitle {
  text-align: center;
  color: var(--text-secondary);
  max-width: 600px;
  margin: 0 auto 64px;
}

.feature-card {
  padding: 32px;
  border-radius: 16px;
  border: 1px solid var(--border-subtle);
  background: var(--bg-secondary);
  transition: border-color 0.2s ease, transform 0.2s ease;
}

.feature-card:hover {
  border-color: var(--border-default);
  transform: translateY(-4px);
}

.feature-icon {
  width: 48px;
  height: 48px;
  border-radius: 12px;
  background: rgba(108, 92, 231, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
  color: var(--accent-primary);
}

.feature-card h3 {
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 8px;
}

.feature-card p {
  font-size: 15px;
  color: var(--text-secondary);
  line-height: 1.6;
}
```

### Pattern: Alternating Split Sections (Stripe)

Left text + right visual, then swap. Each section has:
- Overline label (12px, uppercase, accent color)
- H2 heading (36–48px)
- Body paragraph (16–18px, muted)
- Small CTA link with arrow

### Pattern: Bento Grid (Trending 2025–2026, from 21st.dev)

Interactive cards of varying sizes showing features. Mix of:
- Large demo cards (span 2 cols)
- Stat cards
- Illustration cards
- Code snippet cards

---

## 8. Card Designs

### Standard Feature Card

```css
.card {
  padding: 24px;
  border-radius: 16px;
  border: 1px solid var(--border-subtle);
  background: var(--bg-secondary);
  transition: all 0.2s ease;
}

.card:hover {
  border-color: rgba(108, 92, 231, 0.3);
  box-shadow: 0 0 30px rgba(108, 92, 231, 0.08);
}
```

### Glass Card (21st.dev trend)

```css
.glass-card {
  padding: 24px;
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.06);
}
```

### Pricing Card (Highlighted)

```css
.pricing-card-featured {
  padding: 32px;
  border-radius: 20px;
  border: 1px solid var(--accent-primary);
  background: var(--bg-secondary);
  position: relative;
  box-shadow: 0 0 40px rgba(108, 92, 231, 0.15);
  transform: scale(1.02);
}

.pricing-card-featured::before {
  content: 'Most Popular';
  position: absolute;
  top: -12px;
  left: 50%;
  transform: translateX(-50%);
  background: var(--accent-primary);
  color: white;
  font-size: 12px;
  font-weight: 600;
  padding: 4px 16px;
  border-radius: 999px;
  letter-spacing: 0.02em;
}
```

### Testimonial Card

```css
.testimonial-card {
  padding: 24px;
  border-radius: 16px;
  border: 1px solid var(--border-subtle);
  background: var(--bg-secondary);
}

.testimonial-quote {
  font-size: 15px;
  line-height: 1.7;
  color: var(--text-secondary);
  font-style: italic;
  margin-bottom: 16px;
}

.testimonial-author {
  display: flex;
  align-items: center;
  gap: 12px;
}

.testimonial-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  object-fit: cover;
}

.testimonial-name {
  font-size: 14px;
  font-weight: 600;
  color: var(--text-primary);
}

.testimonial-role {
  font-size: 13px;
  color: var(--text-tertiary);
}
```

---

## 9. Pricing Tables

### Pattern: 3-Tier Horizontal Cards

Derived from Stripe, Linear, and Dribbble pricing page trends.

```
┌──────────────┐  ┌──────────────────┐  ┌──────────────┐
│   Starter    │  │   Professional   │  │  Enterprise  │
│              │  │   ★ POPULAR ★    │  │              │
│   $299       │  │     $599         │  │   Custom     │
│   one-time   │  │    one-time      │  │  Contact us  │
│              │  │                  │  │              │
│ ✓ Feature    │  │ ✓ Everything in  │  │ ✓ Everything │
│ ✓ Feature    │  │   Starter, plus: │  │   in Pro +   │
│ ✓ Feature    │  │ ✓ Feature        │  │ ✓ Dedicated  │
│              │  │ ✓ Feature        │  │ ✓ Priority   │
│ [Get Started]│  │ [Get Started]    │  │ [Contact Us] │
└──────────────┘  └──────────────────┘  └──────────────┘
```

### Pricing Card CSS

```css
.pricing-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
  max-width: 1100px;
  margin: 0 auto;
  align-items: start;
}

.pricing-card {
  padding: 32px;
  border-radius: 20px;
  border: 1px solid var(--border-subtle);
  background: var(--bg-secondary);
}

.pricing-tier {
  font-size: 14px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--text-tertiary);
  margin-bottom: 8px;
}

.pricing-price {
  font-size: 48px;
  font-weight: 700;
  letter-spacing: -0.03em;
  color: var(--text-primary);
  margin-bottom: 4px;
}

.pricing-period {
  font-size: 14px;
  color: var(--text-tertiary);
  margin-bottom: 24px;
}

.pricing-description {
  font-size: 15px;
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 24px;
  padding-bottom: 24px;
  border-bottom: 1px solid var(--border-subtle);
}

.pricing-features {
  list-style: none;
  padding: 0;
  margin: 0 0 32px 0;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.pricing-feature {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  font-size: 14px;
  color: var(--text-secondary);
  line-height: 1.5;
}

.pricing-feature .check {
  color: #22C55E;
  font-weight: 700;
  flex-shrink: 0;
  margin-top: 2px;
}
```

### Innovations Observed

1. **Toggle annual/monthly** — pill toggle above pricing grid, annual shows savings badge
2. **Feature comparison table** — expandable accordion below cards (Stripe pattern)
3. **Highlighted "best value"** card with accent border + glow shadow
4. **Money-back guarantee badge** below pricing — builds trust
5. **Sticky price header** on scroll for comparison tables

---

## 10. Social Proof & Trust

### Logo Bar (Stripe pattern — immediately below hero)

```css
.logo-bar {
  padding: 48px 0;
  border-top: 1px solid var(--border-subtle);
  border-bottom: 1px solid var(--border-subtle);
}

.logo-bar-label {
  text-align: center;
  font-size: 13px;
  font-weight: 500;
  color: var(--text-tertiary);
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: 24px;
}

.logo-grid {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 48px;
  flex-wrap: wrap;
  opacity: 0.5;
  filter: grayscale(100%);
  transition: opacity 0.2s;
}

.logo-grid:hover {
  opacity: 0.7;
}

.logo-grid img {
  height: 28px;
  width: auto;
}
```

### Stats Row (Stripe — large numbers with labels)

```css
.stats-row {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 32px;
  padding: 64px 0;
  text-align: center;
}

.stat-number {
  font-size: 48px;
  font-weight: 700;
  letter-spacing: -0.02em;
  color: var(--text-primary);
}

.stat-label {
  font-size: 14px;
  color: var(--text-tertiary);
  margin-top: 4px;
}
```

### Testimonial Grid (Raycast pattern — quote + avatar + name)

```css
.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

/* Or masonry-style with varying heights */
.testimonials-masonry {
  columns: 3;
  column-gap: 20px;
}

.testimonials-masonry .testimonial-card {
  break-inside: avoid;
  margin-bottom: 20px;
}
```

### Trust Badges

```css
.trust-badges {
  display: flex;
  justify-content: center;
  gap: 32px;
  padding: 32px 0;
  color: var(--text-tertiary);
  font-size: 13px;
}

.trust-badge {
  display: flex;
  align-items: center;
  gap: 8px;
}

/* Examples: "✓ Money-back guarantee", "🔒 Secure payment", "⚡ 48h delivery" */
```

---

## 11. Forms

### Intake / Contact Form (Dark theme)

```css
.form-group {
  margin-bottom: 20px;
}

.form-label {
  display: block;
  font-size: 14px;
  font-weight: 500;
  color: var(--text-secondary);
  margin-bottom: 6px;
}

.form-input {
  width: 100%;
  padding: 12px 16px;
  font-size: 15px;
  color: var(--text-primary);
  background: var(--bg-tertiary);
  border: 1px solid var(--border-default);
  border-radius: 10px;
  outline: none;
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
}

.form-input:focus {
  border-color: var(--accent-primary);
  box-shadow: 0 0 0 3px rgba(108, 92, 231, 0.15);
}

.form-input::placeholder {
  color: var(--text-tertiary);
}

.form-textarea {
  min-height: 120px;
  resize: vertical;
}

/* Select / dropdown */
.form-select {
  appearance: none;
  background-image: url("data:image/svg+xml,...chevron-svg...");
  background-repeat: no-repeat;
  background-position: right 12px center;
  padding-right: 40px;
}
```

### Multi-step Form Pattern (trending on Dribbble)

- Progress bar / step indicators at top
- One question per screen on mobile
- Animated transitions between steps
- Summary card on final step before payment

---

## 12. Animations & Micro-interactions

### Scroll-triggered Fade In (most common pattern)

```css
/* Base state — hidden */
.animate-on-scroll {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}

/* Visible state — triggered by IntersectionObserver */
.animate-on-scroll.visible {
  opacity: 1;
  transform: translateY(0);
}

/* Staggered children */
.animate-on-scroll.visible .stagger-child:nth-child(1) { transition-delay: 0s; }
.animate-on-scroll.visible .stagger-child:nth-child(2) { transition-delay: 0.1s; }
.animate-on-scroll.visible .stagger-child:nth-child(3) { transition-delay: 0.2s; }
```

### Button Hover Effects

```css
/* Lift + glow */
.btn-hover-lift:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px -5px rgba(108, 92, 231, 0.4);
}

/* Shimmer effect on CTA */
@keyframes shimmer {
  0% { background-position: -200% center; }
  100% { background-position: 200% center; }
}

.btn-shimmer {
  background: linear-gradient(90deg,
    var(--accent-primary) 0%,
    #a78bfa 50%,
    var(--accent-primary) 100%);
  background-size: 200% auto;
  animation: shimmer 3s linear infinite;
}
```

### Subtle Background Animations

```css
/* Floating gradient orbs (Linear-style) */
@keyframes float {
  0%, 100% { transform: translate(0, 0) scale(1); }
  33% { transform: translate(30px, -30px) scale(1.05); }
  66% { transform: translate(-20px, 20px) scale(0.95); }
}

.gradient-orb {
  position: absolute;
  width: 400px;
  height: 400px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(108, 92, 231, 0.2) 0%, transparent 70%);
  filter: blur(60px);
  animation: float 20s ease-in-out infinite;
  pointer-events: none;
}
```

### Counter/Number Animation

Animate stats counting up when they scroll into view (e.g., "500+" clients → count from 0 to 500).

### Smooth Scroll

```css
html {
  scroll-behavior: smooth;
}
```

---

## 13. Footer

### Pattern: Minimal Dark Footer (Linear, Vercel)

```css
.footer {
  padding: 64px 0 32px;
  border-top: 1px solid var(--border-subtle);
  background: var(--bg-primary);
}

.footer-grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr;
  gap: 48px;
  margin-bottom: 48px;
}

.footer-brand p {
  font-size: 14px;
  color: var(--text-tertiary);
  max-width: 300px;
  line-height: 1.6;
}

.footer-column h4 {
  font-size: 13px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--text-tertiary);
  margin-bottom: 16px;
}

.footer-link {
  display: block;
  font-size: 14px;
  color: var(--text-secondary);
  text-decoration: none;
  padding: 4px 0;
  transition: color 0.15s ease;
}

.footer-link:hover {
  color: var(--text-primary);
}

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 32px;
  border-top: 1px solid var(--border-subtle);
  font-size: 13px;
  color: var(--text-tertiary);
}
```

### Footer Layout

```
[Logo]                    Product     Company     Legal
Brief description         Features    About       Privacy
of the service.           Pricing     Blog        Terms
                          FAQ         Contact     Refunds

──────────────────────────────────────────────────────────
© 2026 PlanForge                     [Twitter] [LinkedIn]
```

---

## 14. Mobile Responsive

### Breakpoints

```css
/* Mobile first */
/* sm: 640px — Large phones */
/* md: 768px — Tablets */
/* lg: 1024px — Laptops */
/* xl: 1280px — Desktops */
/* 2xl: 1536px — Large monitors */
```

### Key Mobile Adjustments

```css
/* Typography scales down */
@media (max-width: 768px) {
  .hero h1 { font-size: 36px; }
  .section h2 { font-size: 32px; }

  /* Stack grids */
  .features-grid,
  .pricing-grid,
  .stats-row { grid-template-columns: 1fr; }

  .split-section { grid-template-columns: 1fr; gap: 32px; }

  /* Reduce section padding */
  .section { padding: 64px 0; }

  /* Full-width CTAs */
  .cta-group { flex-direction: column; }
  .cta-group .btn { width: 100%; text-align: center; }

  /* Footer stacks */
  .footer-grid { grid-template-columns: 1fr; gap: 32px; }

  /* Nav becomes hamburger */
  .nav-links { display: none; }
  .nav-hamburger { display: flex; }
}

/* Tablet: 2 columns where 3 existed */
@media (min-width: 640px) and (max-width: 1023px) {
  .features-grid { grid-template-columns: repeat(2, 1fr); }
  .pricing-grid { grid-template-columns: repeat(2, 1fr); }
  .testimonials-grid { grid-template-columns: repeat(2, 1fr); }
}
```

### Mobile Navigation Pattern

```css
.mobile-menu {
  position: fixed;
  inset: 0;
  z-index: 100;
  background: var(--bg-primary);
  padding: 80px 24px 32px;
  display: flex;
  flex-direction: column;
  gap: 8px;
  transform: translateX(100%);
  transition: transform 0.3s ease;
}

.mobile-menu.open {
  transform: translateX(0);
}

.mobile-menu-link {
  font-size: 18px;
  font-weight: 500;
  padding: 12px 0;
  border-bottom: 1px solid var(--border-subtle);
}
```

---

## 15. Implementation Recommendations

### Tech Stack

- **Framework**: Next.js 14+ (App Router) or Astro for static
- **Styling**: Tailwind CSS v4 + CSS custom properties for theming
- **Animations**: Framer Motion for React, or CSS-only for lightweight
- **Fonts**: Inter via `next/font` or Fontsource (self-hosted, no FOUT)
- **Icons**: Lucide React (consistent, lightweight)
- **Components**: Radix UI primitives + custom styling

### Tailwind Custom Config Mapping

```js
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        bg: {
          primary: '#0A0A0B',
          secondary: '#111113',
          tertiary: '#1A1A1E',
          hover: '#232328',
        },
        border: {
          subtle: '#222225',
          default: '#2E2E32',
        },
        text: {
          primary: '#EDEDEF',
          secondary: '#A0A0A6',
          tertiary: '#6E6E76',
        },
        accent: {
          primary: '#6C5CE7',
          hover: '#7C6FF7',
        },
      },
      fontFamily: {
        sans: ['Inter', 'system-ui', 'sans-serif'],
      },
      borderRadius: {
        DEFAULT: '12px',
        lg: '16px',
        xl: '20px',
      },
      fontSize: {
        'hero': ['clamp(36px, 5vw, 72px)', { lineHeight: '1.05', letterSpacing: '-0.03em', fontWeight: '700' }],
        'section': ['clamp(32px, 3.5vw, 48px)', { lineHeight: '1.15', letterSpacing: '-0.025em', fontWeight: '700' }],
      },
    },
  },
}
```

### Page Section Order (Recommended)

1. **Nav** — Fixed, transparent, backdrop blur
2. **Hero** — Badge + H1 + subtitle + 2 CTAs
3. **Logo Bar** — "Trusted by" logos (grayscale)
4. **How It Works** — 3-step process (numbered)
5. **Features** — 3-col grid or bento
6. **Sample Work / Social Proof** — Testimonials or case study preview
7. **Pricing** — 3-tier cards
8. **FAQ** — Accordion
9. **Final CTA** — Repeat hero CTA in a banner section
10. **Footer** — Links + legal

### Performance Targets

- **LCP** < 2.5s
- **CLS** < 0.1
- **FID** < 100ms
- Use `loading="lazy"` on below-fold images
- Preload hero fonts
- Minimize JS — most of these patterns are CSS-only

---

## Quick Reference: CSS Variables (Copy-Paste)

```css
:root {
  /* Backgrounds */
  --bg-primary: #0A0A0B;
  --bg-secondary: #111113;
  --bg-tertiary: #1A1A1E;
  --bg-hover: #232328;

  /* Borders */
  --border-subtle: #222225;
  --border-default: #2E2E32;

  /* Text */
  --text-primary: #EDEDEF;
  --text-secondary: #A0A0A6;
  --text-tertiary: #6E6E76;

  /* Accent */
  --accent-primary: #6C5CE7;
  --accent-hover: #7C6FF7;
  --accent-glow: rgba(108, 92, 231, 0.15);

  /* Success/Status */
  --success: #22C55E;
  --warning: #F59E0B;
  --error: #EF4444;

  /* Spacing */
  --space-xs: 4px;
  --space-sm: 8px;
  --space-md: 16px;
  --space-lg: 24px;
  --space-xl: 32px;
  --space-2xl: 48px;
  --space-3xl: 64px;
  --space-4xl: 96px;
  --space-5xl: 128px;

  /* Border Radius */
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --radius-xl: 20px;
  --radius-full: 999px;

  /* Shadows */
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.3);
  --shadow-md: 0 4px 12px rgba(0, 0, 0, 0.3);
  --shadow-lg: 0 8px 25px rgba(0, 0, 0, 0.3);
  --shadow-glow: 0 0 30px rgba(108, 92, 231, 0.15);

  /* Transitions */
  --transition-fast: 0.15s ease;
  --transition-normal: 0.2s ease;
  --transition-slow: 0.3s ease;
}
```
