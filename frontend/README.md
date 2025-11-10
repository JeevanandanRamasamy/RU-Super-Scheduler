# Frontend — React + Vite

This folder contains a React (Vite) single-page application used to interact with the RU Super Scheduler backend APIs. It is built with Vite for fast development and HMR.

Project layout (selected)

- `src/` — application source
	- `components/` — reusable UI components
	- `pages/` — route-level pages
	- `context/` — React context providers
	- `hooks/` — custom hooks
- `public/` — static assets
- `index.html`, `vite.config.js` — Vite config and entry

Prerequisites

- Node.js 16+ (recommended LTS)
- npm or yarn

Install dependencies

From the `frontend/` folder:

```bash
# using npm
npm install

# or using yarn
yarn
```

Development server

Start the dev server (runs on port 5173 by default):

```bash
npm run dev
# or
yarn dev
```

Build for production

```bash
npm run build
# or
yarn build
```

Preview production build

```bash
npm run preview
# or
yarn preview
```

Environment and API host

The frontend expects to call the backend API; by default the Vite app uses an environment variable or a proxy defined in `vite.config.js` or `.env` files. Add an `.env.local` (or `.env`) in `frontend/` with values such as:

```env
VITE_API_BASE_URL=http://127.0.0.1:5000
```

Testing and linting

- Linting: `npm run lint` (if ESLint is configured)
- Unit / integration tests (if present) will be described in the `package.json` scripts

Developer tips

- When changing API endpoints, update the frontend `src` code that calls the backend (search for fetch/axios calls).
- If you experience CORS issues, either run the frontend and backend on the same host/port via a proxy or configure CORS on the backend.

Next improvements (suggested)

- Add Storybook for components
- Add E2E tests (Cypress / Playwright) to cover workflows
- Add a Dockerfile for production builds
