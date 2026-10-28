# React + TypeScript + Vite

A scalable React application built with **TypeScript**, **Vite**, and **Node 24**. The project uses a feature-based architecture inspired by [Bulletproof React](https://github.com/alan2207/bulletproof-react), with tools for code quality, dependency validation, component development, and end-to-end testing.

## Tech Stack

- **Node 24** — Runtime used for development and project tooling.
- **pnpm** — Package manager for installing dependencies and running scripts.
- **React + TypeScript** — Component-based UI development with static type checking.
- **Vite** — Fast development server and production bundler.
- **ESLint + Prettier** — Code quality and consistent formatting.
- **Dependency Cruiser** — Validates module dependencies and architectural boundaries.
- **Playwright** — End-to-end (E2E) testing in a real browser.
- **Storybook** — Develops, documents, and tests UI components in isolation, including their different states and variations.
- **Husky** — Git hooks integration.

## Architecture

The project follows a **feature-based architecture inspired by Bulletproof React** to keep the codebase modular, maintainable, and scalable.

Code is organized around application features rather than grouping everything by technical type. This helps keep related components, hooks, services, and other feature-specific code together.

The architecture aims to establish clear boundaries between:

- **App** — Application-level setup and composition.
- **Features** — Self-contained business features and their related functionality.
- **Shared** — Reusable components, hooks, utilities, and other code that is not specific to a single feature.

Dependency Cruiser helps enforce these boundaries by detecting unwanted dependencies between modules.

## Getting Started

### Prerequisites

Install the following tools:

- [Node 24](https://nodejs.org/)
- [pnpm](https://pnpm.io/installation)

Check your installed versions:

```bash
node --version
pnpm --version
```

### Installation

Clone the repository, navigate to the project directory, and install the dependencies:

```bash
pnpm install
```

### Start the Development Server

```bash
pnpm dev
```

Vite starts the development server and provides a local URL in the terminal.

### Production Build

```bash
pnpm build
```

This runs the TypeScript project build (`tsc -b`) followed by the Vite production build. The generated production assets are placed in `dist/`.

Preview the production build locally:

```bash
pnpm preview
```

## Development Tools

### Code Quality and Validation

Run the available checks individually:

| Command             | Description                                                                    |
| ------------------- | ------------------------------------------------------------------------------ |
| `pnpm typecheck`    | Checks TypeScript types without emitting output.                               |
| `pnpm lint`         | Runs ESLint against the `src` directory.                                       |
| `pnpm lint:fix`     | Automatically fixes supported ESLint issues.                                   |
| `pnpm format`       | Formats source files in `src` with Prettier.                                   |
| `pnpm format:check` | Checks formatting without modifying files.                                     |
| `pnpm depcruise`    | Analyzes dependencies within `src` against the configured architectural rules. |

Run all configured quality checks in sequence:

```bash
pnpm check
```

This runs type checking, linting, formatting validation, and Dependency Cruiser.

### Bundle Analysis

Build the application using the configured analysis mode:

```bash
pnpm build:analyze
```

This runs TypeScript project compilation followed by Vite in `analyze` mode, as configured in the Vite configuration.

### End-to-End Testing with Playwright

Playwright is used to test application behavior through browser interactions, helping verify complete user flows rather than testing individual functions in isolation.

Run the E2E test suite:

```bash
pnpm test:e2e
```

Launch the interactive Playwright UI:

```bash
pnpm test:e2e:ui
```

Generate tests by interacting with the application in a browser:

```bash
pnpm test:e2e:codegen
```

The code-generation script currently targets `http://localhost:3000`. Make sure the application is running at that URL before starting code generation. If Vite uses a different port, update the script or configure the target URL accordingly.

### Component Development with Storybook

Storybook provides an isolated environment for developing, documenting, and reviewing UI components independently of the full application.

It is particularly useful for components that have multiple states or variations, such as loading, disabled, error, empty, and success states.

Start the Storybook development server:

```bash
pnpm storybook
```

Storybook runs on port `6006` by default.

Build a static Storybook site:

```bash
pnpm build-storybook
```

The generated Storybook output can be used to publish or host the component documentation separately from the application.

## Available Scripts

| Script                  | Purpose                                                 |
| ----------------------- | ------------------------------------------------------- |
| `pnpm dev`              | Starts the Vite development server.                     |
| `pnpm build`            | TypeScript build followed by a production Vite build.   |
| `pnpm build:analyze`    | Builds the application in the configured analysis mode. |
| `pnpm preview`          | Previews the production build locally.                  |
| `pnpm typecheck`        | Runs TypeScript checks without emitting files.          |
| `pnpm lint`             | Checks source code with ESLint.                         |
| `pnpm lint:fix`         | Fixes supported lint issues automatically.              |
| `pnpm format`           | Formats source files with Prettier.                     |
| `pnpm format:check`     | Checks source formatting.                               |
| `pnpm depcruise`        | Checks dependency rules and module relationships.       |
| `pnpm check`            | Runs all configured quality checks.                     |
| `pnpm test:e2e`         | Runs Playwright E2E tests.                              |
| `pnpm test:e2e:ui`      | Opens the Playwright UI.                                |
| `pnpm test:e2e:codegen` | Opens Playwright Codegen for the configured URL.        |
| `pnpm storybook`        | Starts Storybook on port `6006`.                        |
| `pnpm build-storybook`  | Builds the static Storybook site.                       |
