# Case study: landing + desk (reference split)

**Status:** Canonical when a product has a public story **and** a work surface.  
**Surfaces:** A (`marketing` / landing) **and** H or C (desk / dashboard)  
**Styles:** `marketing_campaign` on `/` · `clean_product` on `/desk`  
**Theme:** Any (Default, Brutalism, Glass, Mouve, or product palette). Theme retokens. It does not collapse the split.

When the user says “landing and dashboard”, “homepage and app”, “hero + how it works + the actual tool”, or hates a jammed one-pager → **replay this**, not Vault OTP stacked on a marketing page.

---

## What made it feel good

| Layer | What we did |
|-------|-------------|
| **Two routes** | `/` tells the story. `/desk` does the job. Distinct chrome. |
| **Landing nav** | HeroUI `Navbar` from `basic-navbar.tsx`. Icon + **name only**. Links: How it works, Questions. CTA is the product verb, not Connect. |
| **Hero** | Clamp 40–64px, bold, tight tracking, **solid** foreground. One lede. Two pills: verb → desk, How it works → `#how`. |
| **How it works** | `FeatureCard` from `AI/features (1)__feature-card.tsx` — icon, title, three short lines each. Grid of three. |
| **Questions** | Accordion. Three human answers. |
| **Footer** | Brand + one line + Product / Help. Real in-page links. |
| **Desk nav** | `Application/navbars (3)__App.tsx`. Brand links home. **One** Connect on the right. |
| **Desk body** | Short job line. Form. Wrong-network switch only. Session cards after work. |

---

## Connect rule (non-negotiable)

| Page | Connect |
|------|---------|
| Landing `/` | **None.** CTA is Finish mint / Claim default / Open the desk. |
| Desk `/desk` | **Once**, in the navbar. Label: **Connect**. |
| Wrong network | Switch network button. Not a second Connect. |
| Disconnected desk | Navbar Connect is enough. No duplicate gate card. |

---

## Copy rule

Human product language. The job line is the headline, not the protocol.

**Use:** Paste the payment you already sent. / Load the request you already made.  
**Do not use in chrome:** Pre-flight, Coston2 chips, truncated vault addresses, Core Vault mint beside the logo, executor fee, XRPL transaction hash as the page title, attestation, calldata.

Keep live values (min fee, vault copy) **inside the form** where they are needed to finish the job.

---

## Hero type (do not fade)

From `Marketing/hero-sections (4)__App.tsx` take size and weight.

**Keep:** `text-[clamp(40px,8vw,64px)] font-bold leading-[1.1] tracking-tighter text-foreground`  
**Drop:** `bg-hero-section-title bg-clip-text text-transparent` and the white-to-gray fade. The headline must stay readable.

---

## Footer (do not ship ACME)

From `Marketing/footers (4)__App.tsx` take the layout (brand block + columns + bottom line).

**Keep:** Brand, one sentence, two columns of **real** links (How it works, Open the desk, Questions).  
**Drop:** Newsletter, fake Services/Legal/social to `#`, lorem, contract addresses.

---

## Desk compose (when a landing exists)

```
1. Navbar (icon + name → `/`, Connect once)
2. Short job title + one lede
3. Wrong-network card only if connected on the wrong chain
4. Form card if unlocked
5. Session / status cards if work happened
6. STOP — no how-it-works row, no marketing footer, no eng chips
```

If there is **no** landing, fall back to `vault-otp.md` (chips + three ActionCards on the desk).

---

## HeroUI sources to open (4 per route)

**Landing**

1. `Marketing/hero-sections (4)__App.tsx`  
2. `Marketing/hero-sections (4)__basic-navbar.tsx`  
3. `AI/features (1)__feature-card.tsx`  
4. `Marketing/footers (4)__App.tsx`  

**Desk**

1. `Application/navbars (3)__App.tsx`  
2. `Application/authentication (24)__App.tsx`  
3. `Application/cards (20)__action-card.tsx`  
4. Optional: `Application/cards (20)__security-settings.tsx`  

---

## Anti-patterns (this split failed before)

- Hero + how it works + Connect + form on one scroll  
- Two Connect MetaMask buttons  
- Job subtitle under the logo  
- Gradient-clipped hero that fades to unreadable  
- Skinny homemade cards instead of FeatureCard / Navbar  
- Coston2 / vault-address / Pre-flight chips as “status”  
- Fake ACME footer and newsletter  
- Repeating how-it-works on the desk after it already lives on the landing  
- Glass blobs / IBM Plex / motion wallpaper when the user asked for the primitives, not a theme costume  
