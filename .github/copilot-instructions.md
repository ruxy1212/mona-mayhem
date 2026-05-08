# Copilot Instructions for Mona Mayhem

## Project Overview

**Mona Mayhem** is a GitHub Copilot workshop template—a retro arcade-themed website built with Astro that compares GitHub contribution graphs of two users. This is a starter template meant to be built incrementally through guided workshop steps.

The app features a server-rendered architecture and includes an incomplete GitHub contribution API endpoint that workshop participants implement.

## Build, Test, and Lint Commands

### Development
```bash
npm run dev           # Start Astro dev server (hot reload, typically http://localhost:3000)
npm run build         # Production build to dist/
npm run preview       # Preview the production build locally
npm run astro [cmd]   # Direct Astro CLI access for advanced tasks
```

No test or lint commands are currently configured. The workshop expects participants to implement these as needed.

## Architecture

### Tech Stack
- **Framework:** Astro v5 (strict TypeScript mode)
- **Runtime:** Node.js with @astrojs/node adapter (server-rendered in standalone mode)
- **Styling:** CSS (retro gaming theme with Press Start 2P font)
- **External API:** GitHub contribution graph data via unofficial endpoint

### Project Structure
```
src/
├── pages/
│   ├── index.astro                  # Home page (workshop starter template)
│   └── api/contributions/[username].ts  # API route for GitHub data (incomplete)
public/                              # Static assets (favicon, etc.)
docs/                                # Theme CSS files
workshop/                            # Workshop guide (00-06 parts)
```

### Key Implementation Pattern

**Dynamic Route Handling:** The app uses Astro's bracket notation for dynamic routes—`[username]` captures URL parameters. The API endpoint at `/api/contributions/[username]` accesses this via `params.username`.

**Server-Rendered Output:** Set `output: 'server'` with Node.js adapter means all pages render on-demand (no static pre-rendering). This supports dynamic API calls per request.

**Incomplete Endpoint:** The contributions API route returns 501 (Not Implemented) with a TODO. Workshop participants implement the GitHub contribution fetching logic here.

## Key Conventions

- **TypeScript Strict Mode:** All source files use `astro/tsconfigs/strict`. Type safety is enforced.
- **Astro File-Based Routing:** `.astro` files in `src/pages/` automatically become routes. No manual routing config needed.
- **API Routes as Functions:** Files in `src/pages/api/` export `APIRoute` functions; `GET`, `POST`, etc. handlers determine HTTP method behavior.
- **Dynamic Parameters in Filenames:** Square brackets like `[username].ts` are route parameters, accessed via `params` in the handler.
- **TODO Comments for Workshop Gaps:** Incomplete features are marked with TODO comments indicating what participants should implement.
- **JSON API Responses:** API routes return `Response` objects with JSON-serialized bodies and appropriate headers.

## Workshop Context

This is a **workshop template**, not a completed application. The workshop has two tracks:
- **VS Code:** Use Chat, Plan Mode, Agent Mode, and editor-native review loops
- **CLI:** Use `copilot` CLI commands, `/plan`, `/delegate`, and `/review`

Participants follow guided steps in `workshop/00-overview.md` through `workshop/06-bonus.md` to build the app incrementally.

## Common Tasks

### Running the dev server
```bash
npm run dev
```
Open http://localhost:3000. Changes to `.astro` files hot-reload.

### Building for production
```bash
npm run build
npm run preview  # Test the build locally before deploying
```

Output is in `dist/` ready for deployment to Node.js hosting.

### Adding new pages
Create a new `.astro` file in `src/pages/`. Nested folders create nested routes automatically.

### Adding API endpoints
Create a new `.ts` file in `src/pages/api/` that exports `GET`, `POST`, etc. functions. Use `APIRoute` type from `astro`.

### Checking build errors
Run `npm run astro build --verbose` or `npm run build` to see detailed TypeScript and Astro errors.

## Environment

- **Node.js:** 18+ (tested with 22+)
- **Git:** Required for workshop context and version control
- **Browser:** For testing the dev server and comparing contribution graphs
