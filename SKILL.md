---
name: design-promax
description: >-
  Premium React UI via HeroUI Pro + dual-axis router (route × style).
  Default style clean_product = Vault OTP / GhostKeys. Product with a public
  story AND a work surface MUST split landing `/` from desk `/desk` — never one
  jammed page. Read real Navbar, FeatureCard, hero, footer sources. One Connect
  on the desk navbar only. Files: STYLE_PRESETS.json, ROUTE_REGISTRY.json,
  case-studies/vault-otp.md, case-studies/landing-and-desk.md. Surfaces A–H.
  Max 4 source reads. Triggers: design-promax, HeroUI, clean_product, Vault OTP,
  GhostKeys, landing page, dashboard, those cards, those buttons, route UI.
---

# Design ProMax

Real HeroUI Pro sources. **Route × style. Cap 4 file reads.**

## Where the files are (read this first)

Agents install this skill in different layouts. **Resolve paths relative to this SKILL.md file:**

| File | Same folder as SKILL.md (flat install) | Nested repo layout |
|------|------------------------------------------|--------------------|
| Style presets | `STYLE_PRESETS.json` | `skill/STYLE_PRESETS.json` |
| Route registry | `ROUTE_REGISTRY.json` | `skill/ROUTE_REGISTRY.json` |
| Case study (desk) | `case-studies/vault-otp.md` | `skill/case-studies/vault-otp.md` |
| Case study (landing + desk) | `case-studies/landing-and-desk.md` | `skill/case-studies/landing-and-desk.md` |
| Routing guide | `ROUTING.md` | `skill/ROUTING.md` |
| Architecture | `ARCHITECTURE.md` | `skill/ARCHITECTURE.md` |
| HeroUI sources | `sources/` | `skill/sources/` |

**If `case-studies/vault-otp.md` or `STYLE_PRESETS.json` is missing, the skill install is stale. Tell the user to re-run `./install.sh` from https://github.com/fozagtx/design-promax — do not invent clean_product.**

### These names are real (do not claim they do not exist)

- **Style id:** `clean_product` (default), also `trust_green`, `clean_product_compact`, `marketing_campaign`, `dense_admin`, `chat_soft`
- **Case study path:** `case-studies/vault-otp.md` (desk / Vault OTP) and `case-studies/landing-and-desk.md` (split product)
- **Surface H:** wallet / dapp / vault / OTP compose pack in `ROUTE_REGISTRY.json`

---

## Product split (mandatory — any theme)

If the product has a public story **and** a place to do the work, ship **two routes**. Do not jam them onto one page. Theme (Default / Brutalism / Glass / Mouve, or the product palette) only changes radii, shadows, blur, and accent. **The split and the primitives stay.**

| Route | Surface | Style | Job |
|-------|---------|-------|-----|
| `/` landing | A marketing | `marketing_campaign` | Hero, how it works, questions, footer. CTA opens the desk. |
| `/desk` (or `/app`) | H wallet_dapp or C app | `clean_product` | Navbar + short job line + form. Work only. |

Read **`case-studies/landing-and-desk.md`** whenever the user asks for a landing, a homepage, a dashboard, or “both”.

### Primitives to copy (do not vibe-code substitutes)

| Piece | Source (read this) | Adapt |
|-------|--------------------|--------|
| Landing nav | `Marketing/hero-sections (4)__basic-navbar.tsx` | Brand + How it works + Questions. CTA = product verb → `/desk`. **No Connect. No Login.** |
| Landing hero | `Marketing/hero-sections (4)__App.tsx` | `text-[clamp(40px,8vw,64px)] font-bold tracking-tighter` in **solid** `text-foreground`. Two pill CTAs: product verb → desk, How it works → `#how`. |
| How it works | `AI/features (1)__feature-card.tsx` + `AI/features (1)__App.tsx` | Three FeatureCards. Human titles. |
| Questions | HeroUI `Accordion` (or `Marketing/faqs (4)__App.tsx`) | Three real questions. |
| Landing footer | `Marketing/footers (4)__App.tsx` | Brand + one line + **two real columns** (Product, Help). |
| Desk nav | `Application/navbars (3)__App.tsx` | Brand (links home) + **one** Connect on the right. |
| Desk form / gates | `Application/authentication (24)__App.tsx` + `Application/cards (20)__action-card.tsx` | Short job line. Form card. Wrong-network gate only. |

### Hard bans (the failures this skill exists to stop)

Do **not** do these in any theme:

1. **One page that is both landing and desk** — hero + how-it-works + connect + form stacked together.
2. **A second Connect** — landing has zero Connect. Desk has Connect **once**, in the navbar. Never a second “Connect a wallet” gate card with the same button.
3. **Logo subtitle** — icon + name only. Never “Core Vault mint”, “Missed redeem”, or any job line beside the mark.
4. **Faded hero type** — never `bg-hero-section-title bg-clip-text text-transparent` (headline dies into the page).
5. **Engineering dump in the UI** — no chain-name chips, no truncated vault/contract addresses as chips, no “Pre-flight”, no executor-fee footnotes, no architecture notes, no “XRPL transaction hash” as the page headline.
6. **Fake ACME chrome** — no newsletter block, no four columns of `#` links, no social icons to nowhere, no lorem footer.
7. **How it works on the desk** — that section lives on the landing. Desk is the form.
8. **Invented cards** — if the primitive is in `sources/`, read it and adapt. Do not draw a skinny Card and call it a hero.

Connect copy on the desk: **Connect** (one word). Not “Connect MetaMask” repeated down the page.

Landing CTA is the product verb (**Finish mint**, **Claim default**), not Connect.

---

## Efficient protocol (mandatory)

```
1. Load STYLE_PRESETS.json + ROUTE_REGISTRY.json (see path table above)
2. keyword_index → surface.route
   - landing / homepage / hero / how it works / footer → A.landing + marketing_campaign
     AND if the product also has work to do → also H desk. Two routes. Read landing-and-desk.md
   - desk / dashboard / dapp / vault / connect → H or C + clean_product. No marketing hero as body.
3. style → clean_product by default
   - User says like Vault OTP / GhostKeys / those cards/buttons → clean_product + read case-studies/vault-otp.md
   - Surface H → clean_product or trust_green only
   - Surface A landing → marketing_campaign (never paste desk compose onto `/`)
4. efficient_merge (cap 4 per route):
   landing = Marketing/hero-sections (4)__App.tsx
           + Marketing/hero-sections (4)__basic-navbar.tsx
           + AI/features (1)__feature-card.tsx
           + Marketing/footers (4)__App.tsx
   desk    = Application/navbars (3)__App.tsx
           + Application/authentication (24)__App.tsx
           + Application/cards (20)__action-card.tsx
5. Apply button_matrix + the compose recipe for THAT route
6. Adapt colors to the product theme if user says so (structure stays)
7. Human copy only. No eng footnotes. No em dashes.
```

### Button matrix (from case study)

| Role | Props |
|------|--------|
| Primary | `color="primary" radius="full"` + solar bold icon |
| Secondary | `variant="bordered" radius="full" size="sm"` + linear icon |
| Danger | `color="danger" variant="flat" radius="full" size="sm"` |
| Warning | `color="warning" radius="full"` |
| Ghost | `variant="light" radius="full" size="sm"` |

Brutalism: sharp / `radius="none"` CTAs. Other themes: pills.

### Compose recipe (landing — `marketing_campaign`)

Navbar (no Connect) → solid hero + two CTAs → How it works FeatureCards → Questions → human footer. Stop.

### Compose recipe (desk — `clean_product`)

Navbar (brand + **one** Connect) → short job line → wrong-network gate only → form card → session list if work happened. Stop.

If the product has **no** public landing, desk may keep chips + three ActionCards from `vault-otp.md`. If it **has** a landing, do not repeat those cards on the desk.

When adapting to an **existing product theme**: keep this structure; recolor using the product’s primary/bg/fonts — do not invent a new palette and do not drop the recipe.

---

## Stack

React 18 + `@heroui/react` v2 + Tailwind 3 + Framer Motion + `@iconify/react` (`solar:`) + `react-router-dom` when landing and desk both exist.

---

## Rules

1. Dual-axis route + style before multi-file UI
2. Max **4** source reads **per route**
3. Prefer **clean_product** on desks unless campaign landing or dense admin
4. Read `case-studies/vault-otp.md` for desk feel; `case-studies/landing-and-desk.md` when both pages exist
5. Never invent icons; never claim clean_product / case-studies are missing without checking both path layouts
6. Never put architecture notes in product UI
7. Never duplicate Connect. Never jam landing into the desk.
