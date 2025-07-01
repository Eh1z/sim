# Codebase Structure & Navigation Guide

## Root Directory

- **`app/`**  
  The main Next.js application folder.  
  - Contains route groups like `(auth)` and `(landing)` for authentication and landing pages.
  - Subfolders like `api/`, `chat/`, `workspace/`, and others organize API routes, chat features, workspace management, and more.
  - Shared UI and logic files: `layout.tsx`, `globals.css`, `global-error.tsx`, etc.

- **`blocks/`**  
  Modular, reusable logic blocks and integrations.  
  - `blocks/blocks/`: Individual integration files (e.g., for Slack, Google, OpenAI, etc.), each encapsulating logic for a specific service or feature.
  - `types.ts`, `utils.ts`, `registry.ts`, `index.ts`: Type definitions, utility functions, and block registration.

- **`components/`**  
  Shared React components for UI and emails.
  - `ui/`: Atomic UI components (buttons, dialogs, forms, etc.).
  - `icons/`: Icon components and icon sets.
  - `emails/`: Email template components (invitation, reset password, etc.).
  - `icons.tsx`: Large icon library.

- **`contexts/`**  
  React context providers for global state management (e.g., `socket-context.tsx` for WebSocket connections).

- **`db/`**  
  Database schema and migration management.
  - `schema.ts`: Drizzle ORM schema definitions.
  - `migrations/`: SQL migration files for schema evolution.
  - `index.ts`: DB initialization and exports.

- **`docs/`**  
  Documentation site (likely a Next.js app) and related assets.
  - `app/`, `components/`, `content/`, `lib/`, `public/`: Structure mirrors a typical Next.js docs site.
  - `README.md`: Docs-specific readme.
  - `package.json`, `tsconfig.json`, etc.: Docs app configuration.

- **`executor/`**  
  Core workflow and automation engine.
  - `index.ts`, `resolver.ts`, `loops.ts`, etc.: Main logic for executing, resolving, and managing workflows.
  - `handlers/`: Submodules for handling different workflow steps (agent, API, condition, etc.).
  - `__test-utils__/`: Test utilities for the executor.
  - `types.ts`: Type definitions for workflow execution.

- **`hooks/`**  
  Custom React hooks for shared logic (e.g., permissions, debouncing, collaborative workflows).

- **`lib/`**  
  General-purpose libraries and utilities.
  - Subfolders for specific domains: `auth`, `documents`, `email`, `file-parsers`, `logs`, `oauth`, `permissions`, `schedules`, `subscription`, `uploads`, `urls`, `variables`, `waitlist`, `webhooks`, `workflows`.
  - Utility files: `utils.ts`, `env.ts`, `telemetry.ts`, etc.

- **`providers/`**  
  LLM and AI provider integrations.
  - Subfolders for each provider (OpenAI, Google, Anthropic, etc.).
  - `models.ts`: Model definitions and metadata.
  - `index.ts`, `types.ts`, `utils.ts`: Provider registry, types, and utilities.

- **`public/`**  
  Static assets served by Next.js.
  - `favicon/`, `social/`, `twitter/`, `static/`: Images, icons, and other public files.
  - `logo-sim.svg`, `sim.png`, etc.: Branding assets.

- **`scripts/`**  
  Standalone scripts for migrations, data seeding, and other maintenance tasks.

- **`serializer/`**  
  Serialization logic for workflows, data, or state.
  - `index.ts`, `types.ts`: Core serialization logic and types.
  - `__test-utils__/`: Test helpers.

- **`socket-server/`**  
  Real-time server logic (likely for collaborative features).
  - `handlers/`, `middleware/`, `rooms/`, `routes/`, `validation/`, `config/`, `database/`: Modular server logic for handling sockets, rooms, validation, etc.
  - `index.ts`: Server entry point.

- **`stores/`**  
  State management stores (possibly Zustand or similar).
  - Subfolders for each domain: `workflows`, `sidebar`, `panel`, `settings`, `knowledge`, `notifications`, `ollama`, `copilot`, `custom-tools`, `execution`, `folders`.
  - `index.ts`: Store registry or root store.
  - `constants.ts`: Shared constants.

- **`tests/`**  
  Top-level test files (e.g., for socket server).

- **`tools/`**  
  Integrations and utility tools for external services.
  - Subfolders for each tool/integration (e.g., Google, Slack, Notion, etc.).
  - `index.ts`, `registry.ts`, `types.ts`: Tool registry, types, and main entry point.
  - `utils.ts`: Shared tool utilities.

---

## Key File Types

- **`.ts` / `.tsx`**: TypeScript and React component files.
- **`.sql`**: Database migration scripts.
- **`.json`**: Configuration files.
- **`.md` / `.mdx`**: Markdown documentation and content.
- **`.sh`**: Shell scripts for automation.

---

## Navigation Tips

- **Feature Development**:  
  - UI: Start in `components/` and `app/`.
  - Backend logic: Explore `blocks/`, `executor/`, and `lib/`.
  - Integrations: Check `tools/` and `providers/`.

- **Database**:  
  - Schema: `db/schema.ts`
  - Migrations: `db/migrations/`

- **Workflows & Automation**:  
  - Core logic: `executor/`
  - Serialization: `serializer/`
  - State: `stores/`

- **Real-time/Collaboration**:  
  - Socket logic: `socket-server/`
  - Contexts: `contexts/`

- **Documentation**:  
  - Docs app: `docs/`

---

## Additional Notes

- **Testing**:  
  - Test files are co-located with logic (`*.test.ts(x)`) and in dedicated test folders.
- **Configuration**:  
  - Root and per-app config files (`tsconfig.json`, `next.config.ts`, etc.).
- **Public Assets**:  
  - All static files are in `public/` and its subfolders.

---

This guide should help you quickly locate and understand the purpose of each part of the codebase. If you need a deep dive into any specific folder or file, let me know! 