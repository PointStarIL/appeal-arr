# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hebrew-language Appeals Committee Management System (מערכת ועדת ערר) for managing legal appeal cases, particularly licensing and betterment tax appeals. The application uses modern React/TypeScript with a simple Express.js backend and SQLite database.

## Development Commands

### Essential Commands
- `npm run dev` - Start development server (Vite on port 8080)
- `npm run server` - Start Express API server (port 3001)
- `npm run seed` - Populate database with sample data
- `npm run build` - Production build
- `npm run lint` - Run ESLint checks

### Development Workflow
1. Run `npm run server` to start the API backend
2. Run `npm run dev` in another terminal for the frontend
3. Use `npm run seed` to populate test data if database is empty

## Architecture Overview

### Tech Stack
- **Frontend**: React 18.3.1 + TypeScript + Vite + Tailwind CSS
- **UI Components**: shadcn/ui (38+ components) built on Radix UI
- **Data Fetching**: TanStack Query for server state management
- **Backend**: Express.js with SQLite3 database
- **Routing**: React Router DOM with internal state-based navigation

### Key Architectural Patterns

**Navigation**: Uses sidebar-based navigation with state switching rather than URL routing. The main page (`src/pages/Index.tsx`) contains a state machine that renders different components based on `currentPage` state.

**Data Layer**: All API interactions go through `src/api.ts` using TanStack Query hooks. No global state management - relies on server state caching.

**Component Organization**:
- `src/components/ui/` - Reusable shadcn/ui components
- `src/components/cases/` - Case management functionality  
- `src/components/layout/` - Layout components (Sidebar)
- `src/components/[reports|tasks|settings]/` - Feature-specific components

**RTL Support**: Configured for Hebrew text with right-to-left layout support.

### Data Model
Four main entities: Cases (תיקים), Hearings (דיונים), Tasks (משימות), and Stats (סטטיסטיקות). All content is in Hebrew.

## Configuration Files

- **vite.config.ts** - Includes path aliases (@/\*), React SWC, and Lovable platform integration
- **tailwind.config.ts** - Comprehensive design system with custom colors and animations
- **components.json** - shadcn/ui configuration (style: "default", css variables, Tailwind prefix)

## Development Notes

**Form Handling**: Uses React Hook Form with Zod validation via @hookform/resolvers.

**TypeScript**: Configured with relaxed strictness settings in tsconfig.json for rapid development.

**Database**: SQLite database created/seeded via seed.js script. Tables use Hebrew field names and content.

**API Endpoints**: Simple REST API with CRUD operations for cases, hearings, tasks, and statistics.