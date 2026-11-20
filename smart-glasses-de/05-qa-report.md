# QA Review Report — smart-glasses-de Prototype
**File reviewed:** `04-prototype/index.html`
**Date:** November 2026

---

## Summary
- 🔴 Must fix: 2
- 🟡 Should fix: 5
- 🟢 Minor / optional: 3

---

## 🔴 Must Fix

### 1. CTA section primary buttons link to `href="#"` — no destination
**Location:** `index.html` lines ~741–742, inside `<section id="cta">`.
```html
<a href="#" class="btn-primary">Gespräch vereinbaren</a>
<a href="#" class="btn-secondary">Demo anfordern</a>
```
Both are dead links. The nav and hero buttons correctly point to `#cta`, but the CTA section's own conversion buttons lead nowhere. At minimum these should point to a contact form anchor, a Calendly URL, or a `mailto:` address.

### 2. Visible placeholder disclosure text in the social proof section
**Location:** `index.html` line ~665, `<p class="section-sub">` inside `#social-proof`.
```html
<p class="section-sub">Reale Käuferpersönlichkeiten aus Fertigung und Logistik — Zitate werden durch verifizierte Kundenaussagen ersetzt.</p>
```
This sentence renders as normal body copy visible to any visitor. It openly states the quotes are unverified placeholders. Remove this sentence from visible body copy; keep the footer disclaimer and the per-card "Platzhalter" badges.

---

## 🟡 Should Fix

### 3. Benefit card 1 missing DSFA abbreviation expansion
Copywriting (`03-copywriting.md`) specifies: "Fertige DSFA-Vorlagen (Datenschutz-Folgenabschätzung) für..."
The parenthetical expansion is missing in the HTML.

### 4. Benefit card 2 drops a differentiating clause
HTML ends at: "...ein zertifizierter, vorgebauter Connector."
Copywriting includes: "...ein zertifizierter, vorgebauter Connector, der im Rahmen bewährter SAP-Partnerschaften geliefert wird."
The dropped clause reinforces the partner network claim, which the strategy identifies as a key competitive moat.

### 5. All five trust-bar icons use an identical star SVG path
Every trust signal (CE certification, DSGVO, SAP Connector, Germany Support, 90-day guarantee) uses the exact same star-shaped path. Each should use a distinct and semantically relevant icon.

### 6. No `<nav>` semantic element in the header
Navigation content is wrapped in a plain `<div>` with no `<nav>` element. Screen readers use `<nav>` landmarks for navigation. Add `<nav aria-label="Hauptnavigation">`.

### 7. Features section breakpoint (700px) inconsistent with main responsive breakpoint (600px)
The two-column features layout collapses at `max-width: 700px`, but all other responsive overrides trigger at `max-width: 600px`. On viewports between 601px and 700px this causes visual inconsistency.

---

## 🟢 Minor / Optional

### 8. Decorative SVG icons lack `aria-hidden="true"`
Benefit card icons and trust bar icons are purely decorative. Without `aria-hidden="true"`, screen readers will attempt to read them as unnamed graphical elements.

### 9. No skip-navigation link
No "Zum Hauptinhalt springen" link before the sticky header. Add a visually hidden skip link pointing to `<main>`.

### 10. Placeholder testimonial badges — must be tracked for production
The orange "Platzhalter" badges are intentional and correct for prototype use. Before any public deployment, all three testimonials must be replaced with verified customer quotes and badges removed.

---

## Content Consistency Check

| Item | Status |
|---|---|
| Hero headline | ✅ Pass |
| Hero subheadline | ✅ Pass |
| Slogan | ✅ Pass |
| Benefit card 1 body (with DSFA expansion) | ⚠ Minor gap |
| Benefit card 2 body (SAP partnership clause) | ⚠ Minor gap |
| Benefit cards 3 & 4 | ✅ Pass |
| All 3 testimonial quotes | ✅ Pass |
| CTA headline and body | ✅ Pass |
| Feature list (9 items) | ✅ Pass |
| Language (all German) | ✅ Pass |
| No Lorem ipsum / [TODO] | ✅ Pass |
| Strategy pillars (DSGVO + SAP + German AI + rugged HW) | ✅ Pass |

---

## Overall Verdict
The prototype is structurally sound, fully in German, and faithfully reflects the strategy positioning. There are **2 red issues** that must be resolved before sharing with any external stakeholder. The remaining issues are quality improvements that do not block internal review.

**Most critical issue: The two primary CTA buttons in `<section id="cta">` both have `href="#"` and lead nowhere.**
