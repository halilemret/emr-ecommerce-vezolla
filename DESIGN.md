# Visual Direction & Design System

## 1. Identity & Architecture

The storefront and admin panel are styled with a clean, high-contrast, editorial aesthetic designed to showcase products with clarity and distinction:

- **Storefront**: Brand-agnostic, editorial catalog feel with crisp typography, responsive product grids, and accessible components.
- **Admin Panel**: High-density operational commerce workbench tailored for store managers and operators.

## 2. Color Palette

The active palette relies on 2 neutral tones + 1 focused accent. All text pairings strictly satisfy WCAG AA (4.5:1+) contrast standards:

- **Surface**: `#fafaf9` (warm paper-like background) and `#ffffff` (card and table surfaces)
- **Ink / Primary Text**: `#18181b` (deep zinc, high contrast primary text and buttons)
- **Secondary Text**: `#52525b` (muted zinc, high readability secondary text)
- **Borders**: `#e4e4e7` (crisp 1px dividers)
- **Accent**: `#9a3412` (terracotta / brick red, used sparingly for primary discounts, badges, and active states)
- **Status Colors**:
  - Success / In Stock: `#166534` text, `#dcfce7` surface
  - Warning / Low Stock: `#92400e` text, `#fef3c7` surface
  - Error / Cancelled: `#991b1b` text, `#fee2e2` surface

## 3. Typography

- **Headings**: `Instrument Serif` (or theme-customized `Plus Jakarta Sans` / `IBM Plex Sans`). Provides an editorial catalog feel.
- **Body & Admin Panel**: `Plus Jakarta Sans`. Clean rendering and high legibility across dense data tables.
- **Monospace & Numerical Data**: `font-variant-numeric: tabular-nums` and `IBM Plex Mono` for barcodes, SKUs, order IDs, and currency amounts.

## 4. Iconography & Component Rules

- **Icon Set**: `@phosphor-icons/react` for functional, crisp icon representation.
- **Border Radius**: Consistent `rounded-md` (6px) system.
- **Shadows**: Border-first separation (`1px solid #e4e4e7`). Elevation shadows are reserved for modals and dropdown menus (`shadow-lg`).
- **Action Semantics**: Explicit and functional button labels ("View Variants", "Add to Cart", "Complete Order") rather than vague text.
