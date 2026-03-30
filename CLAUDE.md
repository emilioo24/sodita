# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
pnpm dev        # Start dev server at localhost:4321
pnpm build      # Build production site to ./dist/
pnpm preview    # Preview production build locally
pnpm astro check  # TypeScript type checking
```

Requires Node ≥22.12.0 and pnpm.

## Architecture

This is an **Astro 6.1.1** static site. TypeScript strict mode is enabled via `tsconfig.json` (extends `astro/tsconfigs/strict`).

**Routing:** File-based via `src/pages/`. Each `.astro` file in that directory becomes a route.

**Component model:** Astro components (`.astro`) use a frontmatter script block (between `---` fences) for server-side logic, followed by HTML template. Styles are scoped by default.

**Data flow:**
- `src/pages/index.astro` — home route, imports `Layout` and `Welcome`
- `src/layouts/Layout.astro` — base HTML shell with `<slot />` for page content
- `src/components/` — reusable UI components
- `src/assets/` — images imported directly into components (Astro optimizes them)
- `public/` — static files served as-is (no processing)
