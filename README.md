## 1. Project name

**10x-cards**

![Astro](https://img.shields.io/badge/Astro-5-ff5d01?logo=astro&logoColor=white)
![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind-4-38B2AC?logo=tailwindcss&logoColor=white)
![Node](https://img.shields.io/badge/Node.js-22.14.0-339933?logo=node.js&logoColor=white)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

## Table of contents

- **[2. Project description](#2-project-description)**
- **[3. Tech stack](#3-tech-stack)**
- **[4. Getting started locally](#4-getting-started-locally)**
- **[5. Available scripts](#5-available-scripts)**
- **[6. Project scope](#6-project-scope)**
- **[7. Project status](#7-project-status)**
- **[8. License](#8-license)**

## 2. Project description

**10x-cards** is a web application that helps university students create and study educational flashcards efficiently.  
The core feature is an **AI-powered generator** that turns user-provided text (e.g., lecture notes, articles) into high‑quality candidate flashcards, which users can review, edit, and selectively save. The app focuses on reducing the friction of manual flashcard creation while leveraging a **spaced repetition algorithm** to power effective study sessions.

For full product details, see the product requirements in `.ai/prd.md`.

## 3. Tech stack

- **Frontend**
  - **Astro 5** (`astro` ^5.13.7) – modern framework for building fast, content-focused web apps
  - **React 19** (`react` ^19.1.1, `react-dom` ^19.1.1) – interactive UI components
  - **TypeScript 5** – type-safe JavaScript
  - **Tailwind CSS 4** (`tailwindcss` ^4.1.13, `@tailwindcss/vite` ^4.1.13) – utility-first styling
  - **Shadcn/ui**-style primitives (`@radix-ui/react-slot`, `class-variance-authority`, `clsx`, `tailwind-merge`, `lucide-react`, `tw-animate-css`) – building accessible, composable UI

- **Backend & Data**
  - **Supabase** – authentication and database layer (see `.ai/tech-stack.md`)

- **AI integration**
  - **OpenRouter.ai** – used for AI-powered flashcard generation

- **Tooling & CI/CD**
  - **Node.js 22.14.0** (see `.nvmrc`)
  - **ESLint 9 + TypeScript ESLint** – linting (`eslint`, `@typescript-eslint/*`, `eslint-plugin-react*`, `eslint-plugin-astro`, `eslint-plugin-import`, `eslint-plugin-jsx-a11y`, `eslint-plugin-prettier`)
  - **Prettier + prettier-plugin-astro** – formatting
  - **Husky + lint-staged** – pre-commit checks
  - **GitHub Actions** – CI
  - **DigitalOcean** – hosting (planned)

Additional technical notes are available in `.ai/tech-stack.md`.

## 4. Getting started locally

- **Prerequisites**
  - **Node.js 22.14.0** (recommended; see `.nvmrc`)
  - **npm** (bundled with Node)

- **1. Clone the repository**

```bash
git clone https://github.com/<your-github-username>/10x-cards.git
cd 10x-cards
```

- **2. Install dependencies**

```bash
npm install
```

- **3. Configure environment variables**

This project will need configuration for:

- **Supabase** (URL, anon/service keys)
- **OpenRouter.ai** (API key)

Create a `.env` file in the project root and add the required variables for your Supabase project and OpenRouter account. The exact variable names and usage depend on the implementation in `src/db` and `src/pages/api` (to be finalized as the backend is implemented).

- **4. Run the development server**

```bash
npm run dev
```

The app should now be available at `http://localhost:4321` (Astro’s default dev port, unless configured otherwise).

- **5. Build for production**

```bash
npm run build
```

- **6. Preview the production build**

```bash
npm run preview
```

## 5. Available scripts

All scripts are defined in `package.json`:

- **`npm run dev`**: Start the Astro development server.
- **`npm run build`**: Build the project for production.
- **`npm run preview`**: Preview the production build locally.
- **`npm run astro`**: Run the Astro CLI directly (e.g., `npm run astro -- --help`).
- **`npm run lint`**: Run ESLint on the project.
- **`npm run lint:fix`**: Run ESLint with automatic fixes.
- **`npm run format`**: Run Prettier to format supported files.

## 6. Project scope

The MVP scope is defined in `.ai/prd.md`. At a high level:

- **In scope for MVP**
  - **AI-powered flashcard generation from plain text**
    - Uses OpenRouter.ai to generate up to **10 flashcards** from up to **10,000 characters** of input.
    - Prominent text input area with clear character/flashcard limits.
  - **Flashcard review workflow**
    - Review list of AI-generated candidate cards (front/back).
    - In-line edits to each candidate.
    - Accept/reject actions; only accepted cards are saved.
  - **Manual flashcard creation**
    - “Create manually” UI, likely via modal.
    - Text-only front (≤200 chars) and back (≤500 chars) fields.
  - **Flashcard management**
    - Central list of all saved flashcards with pagination.
    - Text-based search (case-insensitive, real-time filtering).
    - Edit and delete operations with confirmation on delete.
    - Empty-state messaging and clear call-to-action for new users.
  - **Spaced repetition study session**
    - Integration with an existing open‑source algorithm (e.g., SM‑2, FSRS).
    - Study sessions that show due cards, reveal answers, and let users self‑grade (e.g., “Hard”, “Good”, “Easy”).
  - **User accounts**
    - Email/password registration, login, and logout.
    - Secure credential storage and session handling.

- **Out of scope for MVP**
  - Custom/proprietary spaced repetition algorithms.
  - Importing content from formats like PDF, DOCX, Markdown.
  - Decks/folders/categories for organizing cards.
  - Rich media on cards (images, audio, rich text).
  - Sharing or collaborating on flashcard sets.
  - LMS integrations and native mobile apps.
  - Advanced subject-specific AI tuning and detailed onboarding flows.

- **Unresolved / to be decided**
  - Exact open-source spaced repetition algorithm to use.
  - Detailed UX for the study session, including grading controls and summary screen.

For a full list of user stories and acceptance criteria, see the **User Stories** section in `.ai/prd.md`.

## 7. Project status

- **Status**: Early-stage MVP in active development.
- **Implemented** (from this repository snapshot):
  - Astro/React/TypeScript/Tailwind project scaffold.
  - Base UI utilities and configuration for modern tooling (ESLint, Prettier, Husky, lint-staged).
- **Planned / not yet implemented** (per PRD):
  - Full authentication flow (registration, login, logout) backed by Supabase.
  - AI flashcard generation via OpenRouter.ai, including character and card limits.
  - Review UI for AI-generated candidates with inline editing and accept/reject actions.
  - Manual flashcard creation modal and flashcard CRUD management views.
  - Search, pagination, and empty-state UX for the flashcard list.
  - Spaced repetition algorithm integration and study session interface with grading and session summary.

Success for the AI features will be measured by:

- **AI Quality**: Target of 75% of AI-generated flashcards being accepted (immediately or after editing).
- **AI Adoption**: Target of 75% of saved flashcards originating from the AI generator.

## 8. License

This project is licensed under the **MIT License**.

See the `LICENSE` file for full license text (if present in this repository).
