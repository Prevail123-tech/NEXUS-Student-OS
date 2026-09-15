# NEXUS Student OS

NEXUS is a local-first futuristic student operating system connecting study, scholarships, opportunities, skills, planning, and campus resources in one interactive prototype.

## Run & Operate

- `pnpm --filter @workspace/api-server run dev` — run the API server (port 5000)
- `pnpm --filter @workspace/nexus-student-os run dev` — run the NEXUS web app through its managed workflow
- `pnpm --filter @workspace/nexus-student-os run typecheck` — typecheck the frontend
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — Postgres connection string

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9
- React + Vite + Tailwind CSS, Framer Motion, Lucide React, Recharts
- API: Express 5
- DB: PostgreSQL + Drizzle ORM
- Validation: Zod (`zod/v4`), `drizzle-zod`
- API codegen: Orval (from OpenAPI spec)
- Build: esbuild (CJS bundle)

## Where things live

- `artifacts/nexus-student-os/src/App.tsx` — local-first NEXUS experience, routes, demo data, and interactions
- `artifacts/nexus-student-os/src/index.css` — NEXUS visual system, responsive utilities, and motion preferences
- `artifacts/nexus-student-os/.replit-artifact/artifact.toml` — managed web artifact routing and workflow configuration

## Architecture decisions

- The first prototype is frontend-only and local-first; demo data is embedded so the judging experience works without credentials or live services.
- Student progress, intro state, settings, saved scholarships, XP, planner tasks, and skill milestones persist in localStorage.
- The intro and main shell share a connected-node NEXUS logo and use the same dark atmospheric visual system.

## Product

The prototype includes a guided intro, dashboard missions, demo AI chat, scholarship radar and eligibility checker, opportunity radar, skill roadmaps, smart planner, stylized campus explorer, progress and gamification views, global search, notifications, profile, and settings.

## User preferences

- The product should feel like a premium startup experience rather than a conventional school dashboard.

## Gotchas

- Standalone Vite builds require `PORT` and `BASE_PATH`; the managed artifact workflow supplies them automatically.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
