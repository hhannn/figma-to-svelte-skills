---
name: figma-to-svelte-sections
description: Implement Figma page sections in a SvelteKit site with responsive structure, existing design tokens, assets, and appropriate visual verification. Use when building a supplied Figma section as Svelte code.
---

# Figma to Svelte sections

Inspect the exact Figma node and its available mobile, intermediate, and desktop frames. Record the content order, section dimensions, grid geometry, typography, spacing, colors, image crop, and interaction states. Treat generated design code as a reference, not a Svelte implementation.

Read the target project's conventions before editing: existing section boundaries, Tailwind tokens and utilities, shared components, local assets, motion setup, and any repository instructions. Reuse these where they fit. Keep a page component focused on arranging sections, and put a section in the route's own component directory unless it is shared across routes.

Build the semantic content and mobile layout first. Map larger frames with responsive grid spans, order, gaps, and alignment based on the actual Figma frames. Use named text and color tokens when the project has them; use exact values when the design requires them. Check text wrapping and image crop in the rendered page, not just the markup.

Leading whitespace in Figma paragraphs may represent a first-line spacer. Implement the offset with the project's spacer component or CSS text indent; do not copy artificial spaces into content.

If Figma shows a shader, treat it as a visual placeholder. Use the underlying base image in the section. The shader will be wired later; do not implement its Figma effect as part of the section unless the user explicitly asks.

Add requested interaction and motion after the static layout is correct. Follow the project's lifecycle and cleanup pattern for animations and scrolling.

Compare the rendered result at the design frame widths, including mobile and desktop. Check reading order, typography, geometry, image crop, interaction, and horizontal overflow. Run the project's relevant type and build checks. Keep edits within the requested scope.
