# AGENTS.md

This file provides AI coding agents with essential context and instructions for working with this project. For detailed patterns, best practices, and comprehensive guidelines, see [instructions.md](./instructions.md).

## Project Overview

A mobile web application built with React, Ionic React, and Salt Design System. This is a Progressive Web App (PWA) optimized for mobile devices.

## Tech Stack

- **React 19** with TypeScript
- **Ionic React 8.5** for mobile UI components
- **Salt Design System** for UI components and theming
- **Vite** for build tooling
- **React Router 5** for routing

## Setup

### Prerequisites
- Node.js v18 or higher
- npm or yarn

### Installation

```bash
npm install
```

### Development

```bash
npm run dev
```

Starts the development server at `http://localhost:5173`

### Build

```bash
npm run build
```

Builds the production bundle to `dist/`

### Preview Production Build

```bash
npm run preview
```

## Testing

```bash
# Unit tests
npm run test.unit

# E2E tests
npm run test.e2e

# Linting
npm run lint
```

## Code Style & Conventions

**CRITICAL: Always follow patterns in [instructions.md](./instructions.md)**

### Key Principles

1. **Use Salt Design System components** - Never use generic HTML elements when a Salt component exists
2. **Use Salt CSS variables** - Never hardcode colors, spacing, or sizing
3. **Use Ionic components** - For page structure (`IonPage`, `IonHeader`, `IonContent`, etc.)
4. **Use `useIonRouter`** - Always use `useIonRouter` for navigation, never `history.push`
5. **Extract data** - All mock data goes in `src/data/` with TypeScript types
6. **Icon components** - All icons are TSX components in `src/components/icons/`

### File Structure

```
src/
├── components/
│   └── icons/          # Icon components (TSX)
├── data/               # Mock data with TypeScript types
├── pages/              # Page components
├── theme/              # Theme configuration
│   ├── SaltThemeProvider.tsx
│   └── variables.css
├── App.tsx             # Main app with routing
├── main.tsx            # Entry point
└── index.css           # Global styles
```

### Required CSS Imports

All CSS imports must be in `main.tsx`:

```typescript
import '@ionic/react/css/core.css';
import '@ionic/react/css/normalize.css';
import '@ionic/react/css/structure.css';
import '@ionic/react/css/typography.css';
import '@ionic/react/css/palettes/dark.system.css';
import '@salt-ds/core/css/salt-core.css';
import '@salt-ds/theme/css/theme-next.css';
import '@salt-ds/theme/css/theme.css';
import './theme/variables.css';
import './index.css';
```

## Building New Features

When building new features, follow this process:

1. **Read [instructions.md](./instructions.md)** - Especially the "Getting Started" section
2. **Create routes** - Use route prefixes for feature groups (`/feature-name/...`)
3. **Create page component** - Use `IonPage`, `IonHeader`, `IonToolbar`, `IonContent`
4. **Use Salt components** - `StackLayout`, `FlexLayout`, `Text`, `Button`, `Card`
5. **Extract data** - Put mock data in `src/data/[featureName]Data.ts`
6. **Create CSS file** - Use only Salt CSS variables
7. **Verify checklist** - Check against "Checklist for New Pages" in instructions.md

## Quick Agent Prompt

For building a new app from scratch, use this prompt:

```
Following the instructions given in instructions.md, set up the project and its dependencies and generate a base mobile web application that I can build upon. Include sample tab pages (Home, List, Settings) with basic structure so I have a working app to start from.
```

## Common Commands

```bash
# Development
npm run dev

# Build
npm run build

# Test
npm run test.unit
npm run test.e2e

# Lint
npm run lint
```

## Important Notes

- **Never hardcode colors or spacing** - Always use Salt CSS variables
- **Never use inline styles** - Use CSS classes with Salt variables
- **Always use `useIonRouter`** - Never use `history.push` directly
- **Input font size** - Must be at least 16px to prevent iOS auto-zoom
- **Touch targets** - Must be at least 44x44px
- **Safe areas** - Always account for iOS safe area insets

## Reference Documentation

- **Detailed Patterns**: See [instructions.md](./instructions.md) for comprehensive patterns, examples, and best practices
- **Ionic React**: https://ionicframework.com/docs/react
- **Salt Design System**: https://www.saltdesignsystem.com/
- **React Router**: https://reactrouter.com/

## Project-Specific Rules

1. **Ionic mode**: Always use `mode: 'ios'` in `setupIonicReact`
2. **Theme provider**: Must wrap App in `SaltThemeProviderNext` with `density="touch"`, `accent="teal"`, `headingFont="Amplitude"`, `actionFont="Amplitude"`
3. **Tab navigation**: Use `IonTabs` with custom `TabBar` component
4. **Font**: Use Amplitude font family (configured in SaltThemeProvider)
5. **PWA**: Service worker registered in `main.tsx`

---

**Remember**: When in doubt, check [instructions.md](./instructions.md) for detailed patterns and examples.

