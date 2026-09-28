---
name: figma-tailwind-mapping
description: Apply SvelteKit projects's Figma-to-Tailwind layout, typography, color, component, and image conventions.
---

# Figma Tailwind mapping

Use alongside `figma-to-svelte-sections` when implementing a Figma section in the SvelteKit projects. Check the current code before using these conventions, since project values may change.

## Project structure

- `src/routes/layout.css`: Tailwind 4 theme, colors, fonts, and reusable utilities.
- `src/routes/<route>/_sections/`: route-owned sections. `src/lib/components/` and `src/lib/sections/`: reusable pieces.
- `static/images/`: local images referenced as `/images/...`.
- `src/routes/+layout.svelte`: global scrolling and image canvas setup. Sections should not create another global scroll instance.

## Mapping

- Figma's 360px mobile frame is the base layout, commonly four columns. Use `md:` for 768px and eight columns, and `lg:` for 1024px and twelve columns. Verify actual section frames before assigning spans or order. Tailwind prefixes are minimum widths.
- `wrap` defines the content width, grid gap, and column metrics used by the site's `Spacer`. `section` provides responsive vertical padding. Use these when they match the design.
- Common Figma spacing maps to Tailwind's 4px scale: 8→`2`, 16→`4`, 24→`6`, 48→`12`, 64→`16`, 96→`24`, 128→`32`. Use a specific value when the frame calls for one.
- Prefer semantic colors such as `bg-background`, `text-foreground`, `text-muted-foreground`, and `text-accent`. Use a palette color such as `text-orange-500` only when that specific color is intended.
- Match Figma's named text styles to the existing utilities: `text-body-base`, `text-body-xl`, `text-heading-base`, `text-heading-lg`, `text-heading-xl`, and `text-button`. These carry responsive typography; verify actual line wrapping.
- Reuse the site's Button and Spacer components where appropriate. Represent Figma's leading paragraph whitespace with Spacer or first-line indentation rather than literal spaces.
- Use the exact base image and inspect its ratio, crop, and position. Figma shader fills are placeholders to be wired later. Keep the section's ordinary image element compatible with the site's global image canvas.

Add project-wide `@utility` rules in `layout.css` only for genuinely repeated design rules. Keep one-off layout choices in component classes. For animation, use the existing GSAP setup and clean up scoped effects on component teardown.

Verify at the supplied Figma widths, especially 360px, 768px, and 1536px when those frames exist. Run `npm run check` and `npm run build` after implementation.
