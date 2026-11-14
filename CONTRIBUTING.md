# Contributing to Vezolla E-Commerce

Thank you for your interest in contributing to the **Vezolla E-Commerce Platform**! We welcome contributions from developers of all skill levels. Whether you are fixing a bug, improving documentation, or proposing a new feature, your help is appreciated.

---

## Code of Conduct

By participating in this project, you agree to abide by our [Code of Conduct](CODE_OF_CONDUCT.md). Please treat all contributors with respect and professionalism.

---

## Development Workflow

### 1. Fork & Clone
1. Fork the repository on GitHub.
2. Clone your fork locally:
   ```bash
   git clone https://github.com/<your-username>/emr-ecommerce-vezolla.git
   cd emr-ecommerce-vezolla
   ```

### 2. Environment Setup
1. Copy the example environment file:
   ```bash
   cp .env.example .env
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the PostgreSQL database:
   - **Option A (Docker)**: `docker compose up -d`
   - **Option B (Embedded script)**: `npm run db`
4. Apply the database schema and seed demo data:
   ```bash
   npm run db:push
   npm run db:seed
   ```
5. Start the development server:
   ```bash
   npm run dev
   ```

### 3. Branching Guidelines
- Create a feature branch off `main`:
  ```bash
  git checkout -b feat/your-feature-name
  # or for bug fixes:
  git checkout -b fix/issue-description
  ```
- Keep changes focused and atomic. Avoid mixing unrelated refactors into a single PR.

---

## Coding Standards

- **TypeScript**: Strict typechecking is enforced. Avoid `any` types; define explicit interfaces or schemas with Zod where appropriate.
- **Server vs. Client Components**:
  - Keep components server-rendered by default.
  - Mark interactive components explicitly with `"use client"`.
  - Mutate server-side state using Server Actions under `src/modules/*/actions.ts` or route handlers.
- **Styling**:
  - Use Tailwind CSS utility classes and design tokens defined in `src/app/globals.css`.
  - Maintain WCAG AA contrast standards (minimum 4.5:1 for body text).
- **Icons**:
  - Use `@phosphor-icons/react` or `lucide-react`. Ensure icons convey functional meaning.

---

## Testing & Quality Gates

Before opening a pull request, verify that all quality gates pass:

1. **Type Check**:
   ```bash
   npm run typecheck
   ```
2. **Automated Test Suite**:
   ```bash
   npm test
   ```
3. **Linter**:
   ```bash
   npm run lint
   ```

If you add new business logic, service functions, or API endpoints, please include corresponding Vitest tests in `*.test.ts`.

---

## Submitting a Pull Request

1. Push your branch to your GitHub fork:
   ```bash
   git push origin feat/your-feature-name
   ```
2. Open a Pull Request against the `main` branch of the upstream repository.
3. Fill out the [Pull Request Template](.github/PULL_REQUEST_TEMPLATE.md) with details about what your changes accomplish.
4. Ensure all CI checks pass. A maintainer will review your submission promptly.
