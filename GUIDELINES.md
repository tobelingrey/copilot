# Coding Guidelines & Best Practices

## Critical Principles

### 1. Semantic HTML & Heading Hierarchy
**ALWAYS follow this structure:**
```html
<section class="hero">
  <h1>Main Page Title</h1>      <!-- Only ONE H1 per page -->
  <p>Supporting text</p>
</section>

<section class="features">
  <h2>Features Section</h2>       <!-- H2 for major sections -->
  
  <div class="feature">
    <h3>Feature Title</h3>        <!-- H3 for subsections -->
    <p>Feature description</p>
  </div>
</section>
```

**Rules:**
- ONE H1 per page (usually page title or hero heading)
- H2 for main section headings
- H3 for subsection headings within H2 sections
- H4 for nested content within H3 sections
- Never skip heading levels (no H1 → H3)

### 2. CSS Variables - Always Use Theme Settings
**Use these variables instead of hardcoding:**

```css
/* Typography */
font-family: var(--font-heading);      /* For headings */
font-family: var(--font-body);         /* For body text */
font-size: var(--font-size-h1);        /* Use semantic sizes */

/* Colors */
background: var(--color-accent);       /* Brand color */
color: var(--color-foreground);        /* Text color */
border-color: var(--color-border);     /* Borders */

/* Spacing - Use the 8px grid */
margin: var(--spacing-md);             /* 24px */
padding: var(--spacing-lg);            /* 32px */
gap: var(--spacing-sm);                /* 16px */

/* Transitions */
transition: all var(--transition-base); /* 250ms ease */
```

**Available Spacing:**
- `--spacing-xs`: 8px
- `--spacing-sm`: 16px
- `--spacing-md`: 24px
- `--spacing-lg`: 32px
- `--spacing-xl`: 48px
- `--spacing-2xl`: 64px

### 3. CSS Naming Conventions (BEM-inspired)

```css
/* Block - The main component */
.hero { }

/* Element - Child of the block */
.hero__title { }
.hero__subtitle { }
.hero__image { }

/* Modifier - Variation of block or element */
.hero--dark { }
.hero__title--large { }

/* State classes */
.is-active { }
.is-open { }
.is-loading { }
```

**Examples:**
```html
<section class="product-card">
  <img class="product-card__image" src="...">
  <h3 class="product-card__title">Product Name</h3>
  <p class="product-card__price product-card__price--sale">$19.99</p>
  <button class="product-card__button is-loading">Add to Cart</button>
</section>
```

### 4. Section Structure Template

Every section should follow this pattern:

```liquid
{% doc %}
  Brief description of what this section does.

  @param {type} setting_name - Description
  
  @example
  Add this section in the theme editor
{% enddoc %}

<section class="section-name" {{ section.shopify_attributes }}>
  <div class="section-name__container">
    <h2 class="section-name__heading">{{ section.settings.heading }}</h2>
    <!-- Content here -->
  </div>
</section>

{% stylesheet %}
  .section-name {
    padding: var(--spacing-xl) 0;
  }
  
  .section-name__container {
    max-width: var(--page-width);
    margin: 0 auto;
    padding: 0 var(--page-margin);
  }
{% endstylesheet %}

{% schema %}
{
  "name": "Section Name",
  "settings": [
    {
      "type": "text",
      "id": "heading",
      "label": "Heading",
      "default": "Section Title"
    }
  ],
  "presets": [
    {
      "name": "Section Name"
    }
  ]
}
{% endschema %}
```

### 5. ID vs Class Usage

**IDs:**
- Use for unique, one-per-page elements
- JavaScript targeting
- Accessibility (aria-labelledby, aria-describedby)
```html
<nav id="main-navigation">
<section id="hero-banner">
```

**Classes:**
- Use for styling (always)
- Reusable components
- Multiple instances
```html
<div class="product-card">
<button class="btn btn--primary">
```

### 6. Liquid Best Practices

**Use hyphens in comments:**
```liquid
{%- comment -%} This removes whitespace {%- endcomment -%}
```

**Check before rendering:**
```liquid
{%- if section.settings.show_feature -%}
  <div class="feature">...</div>
{%- endif -%}
```

**Use filters for safety:**
```liquid
{{ product.title | escape }}
{{ image | image_url: width: 800 }}
{{ price | money }}
```

**Use Shopify routes:**
```liquid
{{ routes.cart_url }}              <!-- Not /cart -->
{{ routes.collections_url }}       <!-- Not /collections -->
{{ routes.account_url }}           <!-- Not /account -->
```

### 7. Accessibility Requirements

```html
<!-- Images always have alt text -->
<img src="..." alt="Descriptive text">

<!-- Buttons have aria-labels when icons only -->
<button aria-label="Close menu">
  <svg>...</svg>
</button>

<!-- Links are descriptive -->
<a href="...">Read more about Product Name</a>  <!-- Good -->
<a href="...">Click here</a>                    <!-- Bad -->

<!-- Form inputs have labels -->
<label for="email">Email Address</label>
<input id="email" type="email">
```

### 8. Mobile-First Responsive Design

```css
/* Base styles - Mobile first */
.component {
  font-size: 16px;
  padding: var(--spacing-sm);
}

/* Tablet and up */
@media (min-width: 768px) {
  .component {
    font-size: 18px;
    padding: var(--spacing-md);
  }
}

/* Desktop and up */
@media (min-width: 1024px) {
  .component {
    font-size: 20px;
    padding: var(--spacing-lg);
  }
}
```

### 9. Performance Best Practices

```liquid
<!-- Lazy load images below the fold -->
<img src="..." loading="lazy">

<!-- Preload critical images -->
<img src="..." loading="eager">

<!-- Use responsive images -->
{{ image | image_url: width: 800 | image_tag: 
  widths: '400, 600, 800, 1000',
  sizes: '(min-width: 1024px) 50vw, 100vw'
}}
```

### 10. Color Usage Guidelines

```css
/* Primary actions */
background: var(--color-accent);

/* Hover states */
background: var(--color-accent-hover);

/* Success messages */
color: var(--color-success);

/* Error messages */
color: var(--color-error);

/* Text */
color: var(--color-foreground);

/* Backgrounds */
background: var(--color-background);

/* Borders and dividers */
border-color: var(--color-border);
```

## Quick Reference Checklist

Before committing any section/component:
- [ ] Proper heading hierarchy (H1 → H2 → H3)
- [ ] All colors use CSS variables
- [ ] All spacing uses `--spacing-*` variables
- [ ] BEM naming convention followed
- [ ] Mobile-first responsive design
- [ ] Images have alt text
- [ ] Buttons/links are accessible
- [ ] LiquidDoc comment added
- [ ] Schema includes all settings
- [ ] No hardcoded URLs (use routes object)
- [ ] Tested on mobile viewport

---

**Last Updated:** November 23, 2025
