# Stripe Homepage

**URL:** https://stripe.com  
**Last studied:** April 2026

## Why It Works

Stripe's homepage is arguably the most influential SaaS landing page ever made. It communicates technical sophistication while feeling approachable.

### The Core Insight

**Stripe sells to developers AND executives.** The design bridges both audiences:
- Developers see code, API references, technical credibility
- Executives see enterprise logos, stats, professional polish

Most B2B sites fail by choosing one audience. Stripe serves both.

## Key Design Elements

### 1. The Gradient Background

The signature flowing color gradients are not decoration — they're brand identity.

**Why it works:**
- Creates visual motion without actual animation
- Suggests transformation, flow, dynamism
- Impossible to screenshot and feel the same (visit the site)
- Changes subtly based on time of day

**Technical approach:**
- CSS gradients + subtle WebGL/Canvas animations
- Mesh gradients that shift and blend
- Performance-optimized (no jank on scroll)

### 2. Real-time Stats Counter

"Global GDP running on Stripe: $X"

**Why it works:**
- Creates urgency and FOMO
- Demonstrates scale instantly
- Updates in real-time — the page feels *alive*
- Positions Stripe as infrastructure, not just a payment processor

### 3. Code + Product Split

The hero shows both:
- Left side: Value proposition in plain English
- Right side: Actual code snippets or product UI

**Why it works:**
- Developers can evaluate technical implementation immediately
- Non-technical visitors see that "it's code, must be legit"
- Reduces "is this for me?" friction for both audiences

### 4. Time-of-Day Theming

The background shifts based on actual time:
- Pre-dawn, Sunrise, Daytime, Dusk, Sunset, Night

**Why it works:**
- Creates a sense of a living, global product
- Subconsciously reinforces "we're always on"
- Memorable detail that people talk about

## Typography

- **Font:** Custom Stripe font (similar to Inter/Söhne)
- **Headlines:** Large, confident, tight tracking
- **Body:** Generous line height, easy to scan
- **Code:** Monospace with syntax highlighting

## Layout Patterns

### The "Bento Grid"

Product features displayed in a grid of different-sized cards:
- Large card for primary product (Payments)
- Medium cards for secondary products (Billing, Connect)
- Small cards for tertiary products

**Why it works:**
- Visual hierarchy without being explicit about priority
- Each card is self-contained but feels part of a system
- Scannable — users can jump to what interests them

### Progressive Disclosure

The homepage is long but never overwhelming:
1. Hero with core value prop
2. Product overview (bento grid)
3. Enterprise social proof
4. Developer section
5. Stats/trust signals
6. CTA

Each section is complete — you could stop reading at any point.

## The Details That Matter

### Hover States
Every interactive element has a considered hover state. Cards lift slightly, colors shift, cursors change.

### Whitespace
Generous margins. Nothing feels cramped. The content breathes.

### Motion
Subtle. Nothing bounces or slides aggressively. Movement serves communication, not decoration.

## What Would Break It

- **Adding more colors:** The gradient palette is tight. More colors = visual noise.
- **Removing the code:** Would feel like any generic SaaS site.
- **Making it shorter:** The length communicates "we have a lot to offer."
- **Stock photography:** Stripe uses illustrations and UI, never stock photos.

## When to Reference This

- B2B SaaS landing pages targeting technical + business audiences
- Platform/infrastructure products
- When you need to communicate sophistication AND simplicity
- Developer-focused marketing

## Code Snippets

### Gradient Background (Simplified CSS)

```css
.hero-gradient {
  background: linear-gradient(
    135deg,
    #667eea 0%,
    #764ba2 25%,
    #6B8DD6 50%,
    #8E37D7 75%,
    #667eea 100%
  );
  background-size: 400% 400%;
  animation: gradient-shift 15s ease infinite;
}

@keyframes gradient-shift {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}
```

### Real-time Counter Animation

```javascript
// Simplified version of Stripe's counter effect
function animateCounter(element, target, duration = 2000) {
  const start = performance.now();
  const initial = parseFloat(element.textContent) || 0;
  
  function update(currentTime) {
    const elapsed = currentTime - start;
    const progress = Math.min(elapsed / duration, 1);
    
    // Easing function for smooth deceleration
    const eased = 1 - Math.pow(1 - progress, 3);
    
    const current = initial + (target - initial) * eased;
    element.textContent = formatCurrency(current);
    
    if (progress < 1) {
      requestAnimationFrame(update);
    }
  }
  
  requestAnimationFrame(update);
}
```

---

*This is a living document. Update as Stripe evolves.*
