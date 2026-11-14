# Vezolla E-Commerce Platform

[![CI](https://github.com/halilemret/emr-ecommerce-vezolla/actions/workflows/ci.yml/badge.svg)](https://github.com/halilemret/emr-ecommerce-vezolla/actions/workflows/ci.yml)
[![Next.js](https://img.shields.io/badge/Next.js-16.4-black?logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-blue?logo=react)](https://react.dev/)
[![Prisma](https://img.shields.io/badge/Prisma-7-2D3748?logo=prisma)](https://www.prisma.io/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?logo=typescript)](https://www.typescriptlang.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?logo=postgresql)](https://www.postgresql.org/)
[![Vitest](https://img.shields.io/badge/Vitest-5.0-6E9F18?logo=vitest)](https://vitest.dev/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A modern, high-performance, modular full-stack e-commerce platform built with **Next.js 16 (App Router)**, **React 19**, **Prisma 7 (Multi-Schema PostgreSQL)**, **Tailwind CSS**, and an **Expo (React Native)** mobile companion app. Designed with an editorial catalog aesthetic for storefront shoppers and an operational workbench for store operators.

---

## 🌟 Key Highlights

- **Next.js 16 & React 19**: Leverages Server Components, Server Actions, streaming SSR, and Turbopack for sub-second page loads.
- **Multi-Schema Database Architecture**: Clean domain separation across 8 specialized Prisma schemas (Catalog, Sales, Inventory, Identity, Content, System, SEO, XML).
- **"Complete the Look" (Kombini Tamamla) Bundle Builder**: Dynamic product bundling with variant-scoped promotion rules, preventing coupon leakage to unrelated cart items.
- **VezollaClub Loyalty & Tiered Pricing**: Automated point accumulation, redemption against orders, and club-exclusive member pricing.
- **Enterprise Promotions Engine**: Support for percentage discounts, fixed reductions, free shipping thresholds, Buy X Get Y (BXGY), and user-specific coupon codes.
- **High-Throughput XML Dropshipping Sync**: Fast streaming XML parser (`fast-xml-parser` & `saxes`) capable of bulk importing thousands of variants, custom attributes, and automated scheduled syncs without database locks.
- **One-Page Checkout & Payments**: Seamless checkout flow with Iyzico payment gateway, installment breakdown tables, automated legal contracts (Pre-Information & Distance Sales Contracts), and address auto-completion.
- **Automated Invoicing & Shipping**: Built-in E-Invoice (E-Fatura) generator and carrier integrations (Yurtiçi, Aras, MNG, PTT) with barcode label rendering (`bwip-js`).
- **GEO & AI Search Readiness**: Out-of-the-box `llms.txt`, Generative Engine Optimization (GEO) tracking for AI search bots (GPTBot, ClaudeBot, PerplexityBot), and dynamic robots/sitemap generators.
- **Zero-Friction Local Development**: Docker Compose support alongside an embedded PostgreSQL script for zero-install database seeding.
- **175+ Automated Tests**: Comprehensive unit and integration test coverage powered by Vitest with GitHub Actions CI pipeline.

---

## 🏗️ Architecture & Multi-Schema Database

The database layer uses Prisma 7 multi-schema PostgreSQL, grouping models into domain-driven boundaries:

```
prisma/schema/
├── base.prisma             # Global datasource & client generator configuration
├── catalog.prisma          # Products, Variants, Categories, Options, Attributes, Media
├── sales.prisma            # Carts, Orders, Payments, Promotions, Fulfillments, Refunds, Loyalty
├── inventory.prisma        # Warehouses, Stock levels, Allocations, Backorders
├── identity.prisma         # Customers, Staff accounts, RBAC Roles & Permissions, Audit logs
├── content.prisma          # Pages, Navigation menus, Banners, Blog posts
├── system.prisma           # Store settings, Payment rules, Invoicing, Notification templates
├── seo.prisma              # Search engine logs, AI bot telemetry, Meta tags
└── xml.prisma              # Dropshipping feeds, Field mapping profiles, Import jobs
```

---

## 🛍️ Storefront Features

- **Editorial Catalog Aesthetic**: High-contrast, clean typography (`Instrument Serif` + `Plus Jakarta Sans`), accessible colors adhering to WCAG AA contrast standards.
- **Instant Search**: Debounced autocomplete modal featuring popular search tags, SKU lookup, and live product previews.
- **Product Experience**:
  - Multi-image gallery with interactive zoom and responsive mobile carousels.
  - Interactive Size Guide with real-time biometric recommendations (height/weight).
  - Fabric, care instructions, and specification accordions.
  - Filtered customer reviews with verified purchase badges and star distributions.
- **Conversion Optimizations**:
  - Live recent sales toasts (social proof).
  - Free shipping progress threshold bar in the side cart drawer.
  - Abandoned cart exit-intent modals with one-click promotional discounts.
  - Multi-currency switcher with live exchange rates (TRY, USD, EUR, GBP).
- **Customer Self-Service**:
  - Secure passwordless and password-based authentication with Argon2 hashing.
  - Order tracking timeline, digital invoice downloads, and structured return request management with hygiene-product return controls.

---

## ⚙️ Admin Operations Workbench

Access the control panel at `/admin` with role-based access control (RBAC):

- **Product & Inventory Manager**: Rich TipTap product editor, SKU barcode generation, image reordering, stock thresholds, and multi-warehouse allocation.
- **Order Processing & Fulfillment**: Live order updates, shipping label PDF generation, automated customer SMS/email notifications, and cancellation/refund workflows.
- **Dropshipping XML Wizard**: Feed previewer, custom node mapping, pricing markups, stock filters, and background cron synchronization.
- **Campaigns & Discounts**: Custom coupon creator with restrictions (minimum order value, customer email binding, category/product locks, usage limits).
- **Theme & Brand Customizer**: Dynamic storefront theme selector, brand colors, typography, top announcement tickers, and trust badge controls without code changes.

---

## 🚀 Getting Started

### Prerequisites

- **Node.js**: v20 or higher
- **npm** or **pnpm**
- **Docker** (optional, for running PostgreSQL via Docker Compose)

### Quick Start

1. **Clone the repository**:
   ```bash
   git clone https://github.com/halilemret/emr-ecommerce-vezolla.git
   cd emr-ecommerce-vezolla
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Configure Environment Variables**:
   Copy the example environment configuration:
   ```bash
   cp .env.example .env
   ```

4. **Start PostgreSQL Database**:
   - **Option A (Docker Compose - Recommended)**:
     ```bash
     docker compose up -d
     ```
   - **Option B (Embedded script)**:
     ```bash
     npm run db
     ```

5. **Initialize Database Schema & Demo Seed**:
   ```bash
   npm run db:push
   npm run db:seed
   ```

6. **Start the Development Server**:
   ```bash
   npm run dev
   ```
   Open [http://localhost:3000](http://localhost:3000) for the storefront, or [http://localhost:3000/admin](http://localhost:3000/admin) for the admin workbench.

---

## 🔑 Default Credentials (After Seeding)

After running `npm run db:seed` or `npm run db:zero-install`, the following default administrative user is created:

| Role | Email | Password | Access URL |
| :--- | :--- | :--- | :--- |
| **Super Admin / Store Owner** | `admin@vezolla.com` *(or `admin@ornek-magaza.local`)* | `Admin123!` | [http://localhost:3000/admin](http://localhost:3000/admin) |

---

## 📜 Available Scripts

| Script | Description |
| :--- | :--- |
| `npm run dev` | Starts the Next.js development server with Turbopack |
| `npm run build` | Generates Prisma client and builds production artifacts |
| `npm run start` | Boots the Next.js production server |
| `npm run db` | Launches the embedded local PostgreSQL database |
| `npm run db:push` | Synchronizes Prisma schemas directly with the active database |
| `npm run db:seed` | Populates database with sample products, categories, and settings |
| `npm run db:zero-install` | Wipes database completely and executes a clean production seed |
| `npm run db:studio` | Opens Prisma Studio visual database editor |
| `npm run worker` | Runs background task worker for cron jobs and scheduled tasks |
| `npm run typecheck` | Validates TypeScript types across the entire codebase |
| `npm test` | Runs the full Vitest suite (175+ tests) |
| `npm run mobile` | Starts the Expo development server for the mobile app |

---

## 🧪 Testing & Quality Assurance

The codebase includes comprehensive unit and integration tests covering pricing calculations, VAT extraction, promotional rule validations, warehouse reservations, and contract generation:

```bash
# Run all automated tests
npm test

# Run tests in watch mode
npx vitest

# Run TypeScript typecheck
npm run typecheck
```

---

## 🗺️ Roadmap & Planned Features

- [ ] **International Payments**: Stripe and PayPal payment gateways alongside Iyzico.
- [ ] **Multi-Language (i18n)**: Built-in internationalization for English, German, and Arabic.
- [ ] **Advanced Search Adapters**: Optional Typesense and Meilisearch integrations for million-item catalogs.
- [ ] **Webhook Subscriptions**: Outbound webhooks for order creation, inventory changes, and fulfillment updates.
- [ ] **Multi-Vendor Marketplace Support**: Vendor portal for merchant onboarding and commission payouts.

---

## 🤝 Contributing & Community

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

- Please read our [Contributing Guidelines](CONTRIBUTING.md) for details on code style, branching, and PR submissions.
- Please review our [Code of Conduct](CODE_OF_CONDUCT.md).
- To report security vulnerabilities, consult our [Security Policy](SECURITY.md).

---

## 📱 Mobile Companion App

A cross-platform React Native app built with **Expo SDK** is located in the `mobile/` directory, designed for store managers to scan barcodes, verify inventory, and view daily sales metrics:

```bash
cd mobile
npm install
npx expo start
```

---

## 📄 License

This project is open-source and distributed under the [MIT License](LICENSE).
