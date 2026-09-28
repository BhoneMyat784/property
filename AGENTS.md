# Repository Guidance

This file defines the stable engineering boundaries and decisions for the Property Portal workspace. Product behavior belongs in `SPEC.md`; update it when features or user workflows change. Keep this file focused on technical choices and repository boundaries that are expected to change infrequently.

## Workspace layout

The workspace has three sibling projects, each maintained as an independent Git repository:

```text
property/
├── api/       # API service
├── app/       # web application
└── mobile/    # Expo mobile application
```

Each project owns its package manifest, lockfile, dependencies, environment configuration, build, and release lifecycle. Do not add a shared source-code package across these repositories by importing files directly. The API contract is the integration boundary. If shared types become necessary, generate them from the API contract or publish a versioned package.

## Technology decisions

- Use TypeScript with strict type checking.
- `api`: Express and TypeScript.
- `app`: React web application, built with Vite; use shadcn/ui configured with preset `b7ClNFsdU`.
- `mobile`: React Native with Expo.
- Persistence: SQLite with Prisma 7 for the initial database.
- HTTP interface: versioned REST JSON API under `/api/v1`.
- Validate external request data at API boundaries with the API's chosen schema validation library.

## Integration and data boundaries

- The API owns business rules, authentication/authorization, and persistent domain state.
- Web and mobile clients consume the API and do not duplicate server-side business rules.
- Public API responses must not expose private account or contact data.
- Store timestamps in UTC and format them for the user in the client.
- Represent money without floating-point storage.
- Keep the schema portable where practical so SQLite-specific choices do not unnecessarily block a later PostgreSQL migration.
- Keep media storage behind an interface so local development storage can be replaced by object storage.

## Change guidance

- Update `SPEC.md` when a product feature or workflow changes.
- Update this file only when a stable stack, architecture, or repository boundary changes.
- Keep each project's README focused on that project's audience, setup, and available capabilities.
- Do not recreate the removed HTML review page unless the user asks for it.
- Development demo accounts and sample credentials must remain development-only.
