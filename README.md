# TaskFlow

TaskFlow is a modern project and task management SaaS-style application built as a portfolio/demo project. It covers the full workflow of a team productivity tool — projects, tasks, a Kanban board, a calendar, a team directory, notifications, and account settings — with a clean, responsive UI and full dark mode support.

TaskFlow runs entirely in the browser. There is no backend, database, or real authentication service — all data is mock/seed data persisted to `localStorage`, making it easy to run, explore, and demo without any server setup.

## Features

- **Dashboard** — overview stats, recent projects, recent activity, and upcoming tasks, all computed from live data
- **Projects** — create, edit, delete, search, and filter projects; a details page with progress, team, and related tasks
- **Tasks** — full CRUD, search, filters, sorting, subtasks, and a list view
- **Kanban Board** — drag-and-drop task management across To Do / In Progress / Done columns
- **Calendar** — month, week, and agenda views of tasks by due date, with overdue indicators
- **Team** — member directory with search, role/workload filters, per-member stats, and a mock "invite member" flow
- **Notifications** — read/unread state, filters, search, and links to related tasks/projects
- **Profile & Settings** — editable profile, activity stats, appearance (Light/Dark/System) theme, task-view preference, and a mock password-change flow
- **Mock authentication** — login, registration, and protected routes
- **Local persistence** — all changes survive a page refresh via `localStorage`
- **Responsive design** — usable on mobile, tablet, and desktop
- **Accessible UI** — a small reusable component library (buttons, inputs, modals, dropdowns, etc.) built with accessible labels and visible focus states

## Tech Stack

- [Next.js 16](https://nextjs.org/) (App Router)
- [React 19](https://react.dev/)
- [TypeScript](https://www.typescriptlang.org/)
- [Tailwind CSS v4](https://tailwindcss.com/)
- [lucide-react](https://lucide.dev/) for icons
- [@dnd-kit/core](https://dndkit.com/) for Kanban drag-and-drop
- React Context + `localStorage` for state and persistence (no external state library, no backend)

## Getting Started

Install dependencies:

```bash
npm install
```

Run the development server:

```bash
npm run dev
```

Then open [http://localhost:3000](http://localhost:3000) in your browser. The exact port may differ if 3000 is already in use — check your terminal output for the URL Next.js prints.

## Production Build

```bash
npm run build
npm run start
```

## Mock Authentication

TaskFlow's authentication is a **local, mock implementation** intended purely for demonstration purposes. Registering an account stores the user (including a plaintext password) in `localStorage` on your own machine — nothing is sent to a server. This is **not** production-grade authentication and should not be treated as secure. There is no real password encryption, no email verification, and no account recovery beyond what's simulated in the UI.

## Data Persistence

TaskFlow has no backend or database. All projects, tasks, team members, notifications, and preferences are seeded on first run and then persisted to your browser's `localStorage`. Clearing your browser storage (or using a different browser/device) resets the app back to its seed data.

## Project Structure

```
src/
  app/          Next.js App Router routes (dashboard, projects, tasks, calendar, team, notifications, profile, settings, auth pages)
  components/   Reusable UI building blocks, organized by feature (ui, layout, projects, tasks, calendar, team, notifications, profile, settings)
  context/      React Context providers (auth, theme, data, preferences, toast)
  hooks/        Thin hooks re-exporting the context providers above
  lib/          Utility functions (storage, dates, formatting, per-feature helpers)
  data/         Seed/mock data for projects, tasks, users, labels, notifications, activity
  types/        Shared TypeScript types for the whole app
public/         Static assets
```

## Environment Variables

None are required. TaskFlow has no external API calls, so there is no `.env` file to configure.

## Portfolio Notes

TaskFlow is a **frontend/demo application**. It's built to showcase a complete, polished SaaS-style UI and frontend architecture — not to be deployed as a real multi-user product. If you'd like to extend it into a real backend-powered app, the `DataContext`/`AuthContext` layers in `src/context/` are the natural places to swap in real API calls in place of the current `localStorage`-backed logic.
