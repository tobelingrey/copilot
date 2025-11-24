# Kyle's Shopify Theme - Learning Project

A custom Shopify theme built from scratch to learn Shopify development, GitHub best practices, and working with AI assistants.

## Store Information
- **Store URL**: kyle-superhi-project-1.myshopify.com
- **Developer Account**: tobelingrey@gmail.com
- **Theme ID**: 174936228033

## 🎯 Important Guidelines - READ FIRST

**Before building any component, review:**
- [`GUIDELINES.md`](./GUIDELINES.md) - Complete coding standards and best practices
- [`TODO.md`](./TODO.md) - Current tasks and priorities

**Key Principles:**
1. **Semantic HTML**: Always use proper heading hierarchy (H1 → H2 → H3)
2. **CSS Variables**: Never hardcode colors/spacing - use theme settings
3. **BEM Naming**: Use `.block__element--modifier` pattern
4. **Mobile First**: Build for mobile, enhance for desktop
5. **Accessibility**: Alt text, aria-labels, semantic elements

## Design System

### Typography
- **Heading Font**: Controlled via theme settings (`--font-heading`)
- **Body Font**: Controlled via theme settings (`--font-body`)
- **Sizes**: H1-H4 configurable in theme customizer
- **Mobile-first**: Smaller sizes on mobile, scale up on desktop

### Colors
All colors are customizable in the theme editor:
- `--color-accent`: Primary brand color (buttons, links)
- `--color-accent-hover`: Hover state for accent
- `--color-success`: Positive actions
- `--color-error`: Error states
- `--color-foreground`: Primary text
- `--color-background`: Page background
- `--color-border`: Borders and dividers

### Spacing (8px Grid System)
- `--spacing-xs`: 8px
- `--spacing-sm`: 16px
- `--spacing-md`: 24px
- `--spacing-lg`: 32px
- `--spacing-xl`: 48px
- `--spacing-2xl`: 64px

### Border Radius
- `--radius-input`: Form inputs
- `--radius-button`: Buttons

## Getting Started

### Prerequisites
- Shopify CLI
- Git
- A Shopify Partner/Developer account

### Installation
1. Clone this repository
2. Install Shopify CLI (if not already installed)
3. Authenticate with Shopify
4. Start the development server

## Development Workflow

### Branching Strategy
- `main` - Production-ready code
- `develop` - Integration branch for features
- `feature/*` - Individual feature branches
- `fix/*` - Bug fix branches

### Commit Message Convention
- `feat:` - New features
- `fix:` - Bug fixes
- `docs:` - Documentation changes
- `style:` - Code style changes (formatting, etc.)
- `refactor:` - Code refactoring
- `test:` - Adding or updating tests
- `chore:` - Maintenance tasks

## Project Structure
```
├── assets/          # CSS, JS, images, SVG files
├── blocks/          # Reusable theme blocks
├── config/          # Theme settings (settings_schema.json)
├── layout/          # Theme layouts (theme.liquid)
├── locales/         # Translation files
├── sections/        # Page sections (header, footer, custom)
├── snippets/        # Reusable Liquid snippets (css-variables, etc)
├── templates/       # JSON templates for pages
├── GUIDELINES.md    # 📖 Coding standards - READ THIS
├── TODO.md          # Current task list
└── README.md        # This file
```

## Development Commands

```bash
# Start development server
shopify theme dev --store kyle-superhi-project-1.myshopify.com

# Push theme to Shopify
shopify theme push

# Pull theme from Shopify
shopify theme pull

# Check theme for issues
shopify theme check
```

## Session Notes & Important Learnings

### Navigation System (Nov 21, 2025)
- Built responsive header with dropdown menu
- Implemented 300ms delay for better UX (prevents accidental close)
- Added logo support with SVG placeholder
- Mobile hamburger menu with smooth transitions

### Design System Setup (Nov 23, 2025)
- **Typography**: H1-H6 hierarchy with mobile-first responsive sizing
- **Color System**: Accent, success, error colors all customizable
- **Spacing**: 8px grid system for consistent spacing
- **CSS Variables**: All design tokens in `snippets/css-variables.liquid`
- **Critical CSS**: Global typography styles in `assets/critical.css`

### Key Decisions Made
1. **Mobile-first approach**: Font sizes scale from 70-85% on mobile, full size on desktop
2. **BEM naming**: Using `.block__element--modifier` for clarity
3. **CSS Variables over hardcoding**: Everything pulls from theme settings
4. **Semantic HTML**: Strict H1 → H2 → H3 hierarchy enforcement
5. **8px spacing grid**: All spacing uses multiples of 8px for consistency

## Learning Resources
- [Shopify Theme Documentation](https://shopify.dev/docs/themes)
- [Liquid Template Language](https://shopify.dev/docs/api/liquid)
- [Shopify CLI Documentation](https://shopify.dev/docs/themes/tools/cli)
- [BEM Naming Convention](https://getbem.com/naming/)

## Quick Tips for AI Sessions

**When starting a new session, ask me to:**
1. "Review the GUIDELINES.md file"
2. "Check TODO.md for current priorities"
3. "Reference the design system in README"

**Common reminders:**
- Always use CSS variables (never hardcode colors/spacing)
- Follow heading hierarchy (H1 → H2 → H3)
- Use BEM naming (`.block__element--modifier`)
- Mobile-first responsive design
- Add LiquidDoc comments to all snippets/sections
This is a learning project to understand:
- Shopify theme development and Liquid templating
- GitHub workflows and best practices
- Working with AI coding assistants
