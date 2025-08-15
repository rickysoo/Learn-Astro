# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an educational Astro website that demonstrates the modern web framework's capabilities. The site teaches 9 core Astro concepts through interactive cards and showcases exceptional performance with 0KB JavaScript bundle and 100 Lighthouse scores.

## Essential Commands

```bash
# Development
npm install              # Install dependencies
npm run dev             # Start dev server at localhost:4321
npm run build           # Build production site to ./dist/
npm run preview         # Preview production build at localhost:4322
npm run astro ...       # Run Astro CLI commands

# Astro-specific commands
npm run astro add       # Add integrations
npm run astro check     # Type check .astro files
```

## Architecture & Structure

### Component System
- **BaseLayout.astro**: Root layout with dark mode support, meta tags, and global styles
- **Page Components**: Navigation, Hero, ConceptsSection, DemoSection, Footer
- **Educational Components**: ConceptCard.astro for modular content presentation
- **Styling**: Tailwind CSS v4 with custom animations and accessibility features

### Key Patterns
- **Static-First**: All components render to static HTML by default
- **Component Composition**: Pages composed of reusable .astro components
- **Props Interface**: TypeScript interfaces for component props (e.g., `export interface Props`)
- **Frontmatter**: All logic in `---` blocks at component top
- **Scoped Styles**: Component-level `<style>` blocks with custom animations

### File Organization
```
src/
├── components/         # Reusable UI components
├── layouts/           # Page layout templates  
├── pages/             # File-based routing (index.astro)
├── styles/            # Global CSS with Tailwind imports
```

### Build System
- **Astro 5.13+** with Vite integration
- **Tailwind CSS v4** via @tailwindcss/vite plugin  
- **TypeScript** with strict config extending astro/tsconfigs/strict
- **Zero JavaScript** output - pure static site generation

### Dark Mode Implementation
- System preference detection with localStorage persistence
- Inline script in BaseLayout prevents FOUC (Flash of Unstyled Content)
- Tailwind dark: variant with CSS custom properties
- Default to dark mode unless explicitly set to light

### Performance Optimizations
- **0KB JavaScript bundle** - no client-side hydration
- **Static HTML generation** - all content pre-rendered
- **CSS optimization** - 27KB minified Tailwind output
- **Custom animations** with reduced motion support
- **Accessibility features** - WCAG compliant focus states

## Development Guidelines

### Component Creation
- Use .astro files for static components
- Define TypeScript interfaces for props
- Import global.css only in BaseLayout
- Use Tailwind classes with custom CSS for animations

### Styling Approach  
- **Tailwind-first** with utility classes
- **Custom CSS** in global.css for reusable animations
- **Component scoping** for component-specific styles
- **Dark mode support** required for all new components

### Content Strategy
- Educational focus with clear concept explanations
- Performance metrics and comparisons highlighted
- SEO-optimized with semantic HTML structure
- Accessibility considerations (reduced motion, high contrast)

### Testing & Validation
- Run `npm run build` to verify static generation
- Check `dist/` output for 0KB JavaScript bundles
- Validate HTML structure and meta tags
- Test dark mode toggle functionality

## Deployment Notes

- **Static hosting ready** - generates pure HTML/CSS/assets
- **CDN optimized** - all files can be cached globally  
- **No server required** - works on GitHub Pages, Netlify, Vercel
- **Performance-first** - achieves 100 Lighthouse scores