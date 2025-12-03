# Nohvara Portfolio - AI Coding Agent Instructions

## Project Overview

**Nohvara Continuum** is a personal portfolio site for Morris Javan Andanje. The site is a single-page HTML application with embedded CSS and minimal JavaScript. The repository does not assume a specific professional label for the owner; AI agents should mirror the public-facing text in `index.html` when describing the site.

### Architecture

- **Single file deployment**: All content in `index.html` (HTML + CSS + inline JS)
- **No build tools**: Plain HTML/CSS/JS - opens directly in browsers
- **Responsive design**: Mobile-first approach using CSS Grid and Flexbox
- **Design system**: Custom CSS variables in `:root` for unified theming (colors, spacing, typography)

## Key Files & Components

### `index.html` - Complete Site
- **Header**: Brand identity (Nohvara Continuum + Morris Javan Andanje) with navigation links
- **Hero Section**: Main value proposition ("clean your story, choose your lane")
- **Model Section** (id: `model`): 4-step service ladder (Clarity → Story → System → Expression)
- **Proof Section** (id: `cases`): 4 real-world case studies as mini-cards
- **CTA Sections**: Multiple call-to-action buttons linking to calendar booking and email list signup
- **Footer**: Copyright, LinkedIn, and email contact
- **Dynamic year**: Uses `document.getElementById('year')` to auto-update footer year

### Assets
- `profile.jpg`: Portrait image (referenced in hero section)

## Design Patterns & Conventions

### CSS Architecture
- **CSS Variables**: All colors and semantic sizing use `:root` variables (e.g., `--accent: #f5c26b`)
- **Color Palette**: 
  - Dark background (`#050608`)
  - Card background (`#101118`)
  - Gold accent (`#f5c26b`) for highlights and hover states
  - Soft text colors for hierarchy
- **Spacing Scale**: Loosely follows `0.2rem`, `0.45rem`, `0.6rem`, `0.8rem`, `1rem`, `1.6rem`, `1.8rem`, `2.4rem`
- **Typography**: System font stack, minimal weights, heavy reliance on color and size for hierarchy
- **Interactive Elements**: Smooth 0.18s transitions on buttons/links, subtle hover effects (border-color, box-shadow, translateY)

### Component Patterns
- **Buttons**: Two variants - `btn-primary` (gold accent background) and `btn-ghost` (transparent with border)
- **Pills**: Small semantic tags with border (`pill` class) for skill/feature lists
- **Cards**: Gradient backgrounds with borders for case studies (`mini-card`)
- **Sections**: Bordered top, consistent padding/margins for visual rhythm
- **Grid Layouts**: 
  - Hero: 2-column (2fr / 1.3fr) on desktop, stacked mobile
  - Model section: 2-column grid (1.4fr / 1.2fr)
  - Responsive breakpoint: `@media (max-width: 720px)` collapses to single columns

### Accessibility Notes
- All images have alt text
- External links use `target="_blank"` with `rel="noopener noreferrer"`
- Color contrast follows dark theme conventions
- Font sizes use `rem` for scaling

## Development Workflow

### Local Testing
- Open `index.html` directly in a browser (file:// protocol works)
- Chrome debugger: Use `.vscode/launch.json` configuration to launch with `http://localhost:8080`
- Requires simple HTTP server (e.g., `python -m http.server 8080`) if testing live features

### Content Updates
- Edit text directly in `index.html` between relevant semantic tags
- Update styling in the `<style>` block
- Keep CSS variable values in `:root` for theming consistency
- Maintain HTML structure (especially section IDs: `model`, `cases`) for navigation links

### External Integrations

#### Google Calendar Booking Link
- **Location**: Primary CTA button (`.btn-primary`) with text "Book a clarity call"
- **URL**: `https://calendar.app.google/RNHBoKBDEshHmGQ96`
- **Appears in**: Hero section + Final CTA section (two instances)
- **Purpose**: Direct scheduling without intermediate forms
- **Management**: If calendar link changes, update BOTH instances to maintain consistency

#### Google Sheets Email List Signup
- **Location**: Secondary CTA button (`.btn-ghost`) with text "Join the Quiet List"
- **URL**: `https://script.google.com/macros/s/AKfycbx-yEBTiQvGoW8eHZb7igIcA8QbO9fz2BHF5XW4ODxVAVp5SBizgsTzoK5DwjUg6KeO9Q/exec`
- **Appears in**: Hero section + Final CTA section (two instances)
- **Purpose**: Collects emails for "Quiet List" monthly newsletter
- **Management**: Google Apps Script endpoint; if the macro is updated/redeployed, get new URL and update both instances

#### Link Management Best Practices
- Always verify both instances are updated when changing integration URLs
- Test links immediately after changes with `target="_blank"` to ensure correct external opening
- Keep old URLs documented in git commit messages for rollback reference
- Consider adding a comment in HTML above each link section noting the integration purpose

## Common Tasks

### Updating Content
- Hero tagline/subtitle: Locate in `.hero-main` section
- Service descriptions: Edit within `.grid-2` under "Model" section
- Case studies: Add/modify within `.card-list` (`.mini-card` elements)
- Footer year: Automatically updates via JavaScript

### Styling Changes
- Color adjustments: Modify `:root` variables (one place updates entire theme)
- Responsive breakpoints: Add rules in `@media (max-width: 720px)` block
- Component-specific styles: Keep grouped under clear class selectors (e.g., `.btn-primary`, `.mini-card`)

### Adding New Sections
- Copy existing section pattern (border-top, section-title, h2, content)
- Ensure section has an `id` if it needs anchor navigation
- Follow spacing scale for consistency
- Test mobile responsiveness at 720px width and below

## Important Conventions

- **No external CSS files**: All styling is inline in `<style>` block
- **No JavaScript frameworks**: Vanilla JS only (currently just auto-updating copyright year)
- **Image paths**: Use relative paths (e.g., `profile.jpg` - in same directory)
- **No build step required**: Changes take effect immediately on refresh
- **Mobile-first considerations**: Always verify `@media` rules for screens ≤720px
- **Color consistency**: Always reference CSS variables, don't hardcode hex values in new code

## Git Workflow

- Main branch is `main`
- Minimal commit history (currently 2 commits)
- Push changes directly to main for this simple site

---

**Last Updated**: December 2025 | **Contact**: morrisjavan77@gmail.com
