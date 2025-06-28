# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**CMS-Admin** - 企业级内容管理系统，基于 Vue 3 + TypeScript 的现代化后台管理平台，为企业提供完整的内容管理解决方案。

**Tech Stack**: Vue 3.5.13, Vite 6.3.4, TypeScript 5.2.2, Element-Plus 2.9.9, Pinia, Vue Router

## Development Commands

```bash
# Install dependencies
pnpm install

# Start development server (runs on port 9848)
pnpm dev

# Type checking
pnpm type-check

# Linting (with auto-fix)
pnpm lint

# Code formatting
pnpm format

# Build for production
pnpm build
```

## Architecture Overview

### Project Structure
- **src/api/**: Feature-based API modules with centralized HTTP client (`RequestHttp` class)
- **src/stores/**: Pinia stores for state management (user, auth, app, options)
- **src/components/**: Reusable components (ProTable, Grid, SearchForm, Upload)
- **src/views/**: Page components organized by feature
- **src/router/**: Dynamic routing system with menu-driven route loading
- **src/layouts/**: Multiple layout options (Classic, Columns, Transverse, Vertical)
- **src/utils/**: Utility functions and helpers
- **src/hooks/**: Composable hooks (useTable, useDict, useHandleData)

### Key Architectural Patterns

**API Layer**: 
- Centralized HTTP client in `src/api/index.ts` with automatic token handling
- Feature-based modules in `src/api/modules/` (system, teacher, toolbox)
- TypeScript types mirror API structure in `src/api/types/`
- Consistent RESTful naming: `getUserList`, `addUser`, `editUser`, `deleteUser`

**State Management**:
- Composition API style Pinia stores
- Persistent state using `pinia-plugin-persistedstate`
- Key stores: user (auth), auth (permissions), app (settings), options (dictionaries)

**Component Patterns**:
- **ProTable**: Main data table component with declarative configuration
- **v-auth directive**: Fine-grained permission control at button level
- Heavy use of Element Plus components with custom theming
- Composition API throughout with TypeScript

**Routing**:
- Dynamic route loading from backend menu data
- Route guards handle token validation and permission checking
- Auto-import view components using `import.meta.glob()`

### Permission System
- Backend-driven permissions loaded via API
- Menu-based navigation with role-based access
- Button-level permissions using `v-auth` directive
- Data permissions for fine-grained access control

### Environment Configuration
- Development: API at http://127.0.0.1:9991, WebSocket at ws://127.0.0.1:9993
- Production: Uses nginx reverse proxy for `/api` and `/socket`
- Bypass permissions available in development (`VITE_ADMIN_BYPASS_PERMISSION`)

## Common Development Tasks

**Adding New API Module**:
1. Create module in `src/api/modules/[feature]/`
2. Add corresponding types in `src/api/types/[feature]/`
3. Export from main API index
4. Use consistent naming conventions for CRUD operations

**Creating New Views**:
1. Use ProTable component for data tables
2. Implement search forms with SearchForm component
3. Add permission checks with `v-auth` directive
4. Follow composition API patterns with proper TypeScript

**State Management**:
- Use existing stores when possible (user, auth, app, options)
- Create new stores in `src/stores/modules/` for feature-specific state
- Enable persistence for data that should survive page refresh

## Code Quality
- ESLint with Vue, TypeScript, and Prettier integration
- Prettier configured with 130 character line width, 2-space tabs
- TypeScript strict mode enabled
- Vue 3 Composition API required for all new components

## Build & Deployment
- Vite build system with SVG sprite generation and gzip compression
- Docker support with nginx configuration
- CI/CD pipeline via GitHub Actions for `preview` branch
- Deploys to Alibaba Cloud Container Registry