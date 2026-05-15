# CHAIC 2026 — Design System

## Colors

| Token | Hex | Usage |
|---|---|---|
| `--dark` | `#050d1e` | Page background, hero bg |
| `--dark-2` | `#0a1628` | Mobile nav dropdown bg |
| `--gold` | `#f5b800` | Primary accent, CTA buttons, hero title accent |
| `--navy-btn` | `#1a3e7a` | Secondary buttons, badges, ticket borders |

### Extended palette (inline, no token)

| Hex | Usage |
|---|---|
| `#0d1117` | Agenda section background, agenda cards |
| `#131929` | Agenda card background |
| `#0d1b2e` | Dark section background (`section-dark`) |
| `#f7f8fc` | Light section background (`section-light`) |
| `#e8b84b` | Agenda accent gold (slightly warmer than `--gold`) |
| `#b7791f` | VIP/approval badge color |
| `#020810` | Footer background (deepest dark) |
| `#1a1a2e` | Body text on light sections, nav links |
| `#e0a800` | `--gold` hover state |
| `#15326a` | `--navy-btn` hover state |

---

## Typography

### Fonts

| Role | Family | Weights |
|---|---|---|
| Body | Inter | 400, 500, 600, 700, 800, 900 |
| Headings (`h1`–`h6`) | Space Grotesk | 400, 500, 600, 700 |
| Fallback | `system-ui, -apple-system, sans-serif` | — |

Loaded via Google Fonts:
```
Inter: 400, 500, 600, 700, 800, 900
Space Grotesk: 400, 500, 600, 700
```

### Type scale

| Element | Size | Weight | Notes |
|---|---|---|---|
| Hero title | `clamp(3rem, 4.5vw, 5rem)` | 900 | Space Grotesk |
| Countdown number | `4.5rem` (desktop) → `2.6rem` (mobile) | 900 | |
| Section title | `2.25rem` | 800 | |
| About title | `clamp(2rem, 3.5vw, 2.75rem)` | 900 | |
| Agenda title | `clamp(2rem, 3.2vw, 2.6rem)` | 900 | |
| Agenda card title | `1.3rem` | 800 | |
| Ticket price | `2.75rem` | 900 | |
| Sub-headings | `1.15rem` | 700 | |
| Body / section desc | `0.95–1.05rem` | 400 | line-height 1.75–1.85 |
| Small labels / roles | `0.78–0.88rem` | varies | |
| Uppercase tracking labels | `0.65–0.85rem` | 600 | `letter-spacing: 0.06–0.12em` |

---

## Spacing & Layout

| Token | Value |
|---|---|
| `--nav-h` | `72px` |
| Container max-width | `1100px` (sections), `1280–1400px` (hero/agenda) |
| Section padding | `5rem 2rem` (desktop) → `3.5rem 1.25rem` (mobile) |
| Border radius (cards) | `14–16px` |
| Border radius (pills/buttons) | `50px` |

### Breakpoints

| Name | `max-width` |
|---|---|
| Tablet | `1024px` |
| Mobile | `768px` |

---

## Components

### Buttons

#### `.btn-register` — Primary CTA (gold)
- Background: `--gold` (`#f5b800`)
- Color: `--dark`
- Padding: `0.85rem 0.9rem 0.85rem 1.75rem`
- Has pulsing glow animation (`btn-pulse`)
- Paired with `.btn-circle` (dark circle with gold arrow)

#### `.btn-agenda` — Ghost outline
- Border: `2px solid rgba(255,255,255,0.6)`
- Color: white
- Backdrop blur: `4px`
- Paired with `.btn-circle-ghost`

#### `.btn-contact` — Navy pill (navbar)
- Background: `--navy-btn`
- Color: white
- Padding: `0.55rem 0.7rem 0.55rem 1.3rem`
- Paired with `.btn-circle-nav` (white circle, navy arrow)

#### `.btn-ticket` — Navy pill (tickets)
- Background: `--navy-btn`
- Hover: `#15326a`
- Full-width block

#### `.btn-get-tickets` — White pill (agenda sidebar)
- Background: white, Color: dark
- Hover background: `#e8b84b`

#### `.btn-become-sponsor` — Ghost outline (dark bg)
- Border: `2px solid rgba(255,255,255,0.5)`
- Color: white

### Cards

#### Speaker card (`.speaker-card`)
- Background: `rgba(255,255,255,0.05)`
- Border: `1px solid rgba(255,255,255,0.1)`
- Border radius: `14px`
- Centered layout, avatar + name + role

#### Agenda card (`.agenda-card`)
- Background: `#131929`
- Border: `1px solid rgba(255,255,255,0.08)`
- Sticky stacking effect using `--card-index` CSS var
- Time bar height: `56px`, color: `#e8b84b`

#### Sponsor card (`.sponsor-card`)
- Background: `rgba(255,255,255,0.07)` with `backdrop-filter: blur(14px)`
- Size: `300×140px`
- Used in auto-scrolling carousel

#### Ticket card (`.ticket-card`)
- Background: white, border: `2px solid #e0e4ed`
- `.featured` variant: navy border + shadow
- `.ticket-card--vip` variant: gold/amber border + warm gradient bg

### Navbar
- Height: `72px`, background white, sticky top
- Links: `#1a1a2e`, hover: `--navy-btn`
- Contact button absolutely positioned at right edge on desktop
- Collapses to hamburger (3-line → X animation) at ≤768px
- Mobile menu: dark bg `--dark-2`, full-width stacked links

### Hero
- Full-viewport height minus navbar
- Background video (`ai-brain-opt.mp4`) with static image fallback
- Left-to-right gradient overlay with `backdrop-filter: blur(6px)`
- 2-column grid: countdown + event info left, tagline right
- Gold accent text on title

### Sections
- `.section-light`: `#f7f8fc` bg, `#1a1a2e` text (About, Tickets)
- `.section-dark`: `#0d1b2e` bg, white text (Speakers, Sponsors)
- Agenda section: `#0d1117` (standalone, no `.section` class)

### Footer
- Background: `#020810`
- Single row: logo | copyright | nav links
- Stacks vertically on mobile

---

## Iconography

All icons are inline SVG from the Feather icon set style:
- `stroke-width: 1.6–2`
- `stroke-linecap: round`, `stroke-linejoin: round`
- `fill: none` (outline style)
- Sizes: `13–44px` depending on context

---

## Motion

| Effect | Implementation |
|---|---|
| Register button glow | `@keyframes btn-pulse` — box-shadow cycle, 2.6s ease-in-out infinite |
| Sponsor carousel | `@keyframes scroll-sponsors` — translateX 0 → -50%, 22s linear infinite; pauses on hover |
| Nav hamburger → X | CSS transform on `span` children, `transition: all 0.25s` |
| Agenda sticky stack | CSS sticky + `--card-index` custom property per card |
| Reduced motion | `@media (prefers-reduced-motion: reduce)` — hides hero video, shows static image |

---

## Images & Assets

All images in `/images/`. Format: **WebP** (logos, stills), **MP4** (videos).

| Asset | Path | Notes |
|---|---|---|
| CHAIC logo | `images/logos/CHAIC-Logo.webp` | Used in navbar + footer |
| Hero video | `images/videos/ai-brain-opt.mp4` | Poster: `ai-brain-opt.webp` |
| About video | `images/videos/about-opt.mp4` | |
| SPE logo | `images/logos/SPE-White-Letters.webp` | White version for dark bg |
| ABAIM logo | `images/logos/ABAIM-logo-transparent.webp` | Wide aspect ratio |
| AMRC logo | `images/logos/AMRC.webp` | Square-ish |
| RCM-UPR logo | `images/logos/RCM-UPR-Logo.webp` | Square-ish |
