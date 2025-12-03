# React + Ionic + Salt Design System - Mobile Web App Instructions

This document contains instructions, patterns, and best practices for building mobile web applications using React, Ionic React, and the Salt Design System. Follow these guidelines to ensure consistency, maintainability, and excellent mobile UX.

### Quick Start - Give This to Your Agent

Copy and paste this simple prompt to your AI coding assistant:

```
Following the instructions given in instructions.md, set up the project and its dependencies and generate a base mobile web application that I can build upon.
``` 


### Prerequisites

Before starting, ensure you have:
- Node.js (v18 or higher)
- npm or yarn package manager
- A code editor with AI coding assistant (VS Code with Cursor, GitHub Copilot, etc.)

### Step 1: Initialize Your Project

Create a new React + TypeScript project with Vite:

```bash
npm create vite@latest my-mobile-app -- --template react-ts
cd my-mobile-app
npm install
```

### Step 2: Install Required Dependencies

Install Ionic React, Salt Design System, and React Router:

```bash
npm install @ionic/react @ionic/react-router react-router react-router-dom @salt-ds/core @salt-ds/theme
npm install -D @types/react-router @types/react-router-dom
```

### Step 2a: Required CSS Imports

Create or update your main entry file (e.g., `main.tsx`) to import required CSS:

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

### Step 3: Add This Instructions File

1. Download or copy this `instructions.md` file into your project root
2. Open it in your IDE
3. Make it available to your AI coding assistant (attach it, reference it, or ensure it's in the workspace)

### Step 4: Use This Single Prompt to Build Your App

Copy and paste this prompt into your AI coding assistant, customizing the app name and features:

```
Build a complete mobile web app following all patterns in instructions.md.

App Requirements:
- App Name: [Your App Name]
- Main Features: [List 3-5 main features/sections]
- Tab Navigation: [List tab names, e.g., Home, List, Settings, Profile]

Follow these steps in order:

1. **Project Setup**:
   - Set up Ionic React with setupIonicReact({ mode: 'ios' })
   - Configure React Router with IonReactRouter
   - Import all required Ionic CSS files
   - Create theme/variables.css and index.css files
   - Follow the App Structure section for base setup

2. **Create App Component**:
   - Build the main App.tsx following the App Structure section
   - Create TabBar component with tab selection logic
   - Set up routes for all main pages
   - Use generic tab names and routes

3. **Create Theme Provider**:
   - Create theme/SaltThemeProvider.tsx
   - Set up SaltThemeProvider with SaltProviderNext
   - Support light/dark mode switching with localStorage persistence
   - Configure SaltProviderNext with density="touch", accent="teal", headingFont="Amplitude", actionFont="Amplitude"
   - Wrap App component in main.tsx with SaltThemeProviderNext

4. **Create Icon System**:
   - Create components/icons/Icon.tsx base component
   - Create icon components for navigation (Home, List, Settings, etc.)
   - Export all icons from components/icons/index.ts
   - Follow the Icons section patterns

5. **Create Base CSS Files**:
   - Create index.css with global styles, font smoothing, and Salt variable overrides
   - Create theme/variables.css for Ionic theme variables
   - Set up salt-toolbar, salt-page-shell, salt-inline-icon CSS classes
   - Follow Styling & Theming section

6. **Create Main Pages**:
   - Build Home page following Page Structure section
   - Build List page with search functionality
   - Build Settings page
   - Each page must use IonPage, IonHeader, IonToolbar, IonContent
   - Use Salt components (StackLayout, FlexLayout, Text, Button, Card)
   - All styling in CSS files using Salt CSS variables

7. **Create Data Files**:
   - Extract all mock data to src/data/ directory
   - Export TypeScript types with data
   - Follow Data Organization section

8. **Apply Styling**:
   - Create CSS files for each page
   - Use only Salt CSS variables (var(--salt-spacing-150), etc.)
   - No inline styles, no hardcoded colors/spacing
   - Follow Styling & Theming section

9. **Verify Checklist**:
   - Check against "Checklist for New Pages" section
   - Ensure no anti-patterns from "Anti-Patterns to Avoid" section
   - Verify all navigation uses useIonRouter
   - Confirm all inputs have font-size: 16px minimum

Reference instructions.md for:
- Navigation patterns (useIonRouter, location.state)
- Header patterns (FlexLayout with three-column layout)
- List patterns (Salt components)
- Action bars (fixed bottom with Salt spacing)
- Mobile UI best practices (safe areas, touch targets, font sizes)

Build the complete app structure, all pages, routing, and styling following every pattern in instructions.md.
```

### Step 5: Customize the Prompt

Replace the placeholders in brackets:
- `[Your App Name]` - Your application name
- `[List 3-5 main features/sections]` - What your app does
- `[List tab names]` - Your navigation tabs

### Step 6: Iterate and Build Features

After the initial app is built, use specific prompts for new features:

```
Add a [FeatureName] feature to the app following instructions.md:
- Create routes under /feature-name/ prefix
- Build [FeatureName]Page component
- Extract mock data to src/data/
- Use Salt components throughout
- Follow all patterns in instructions.md
```

### What You'll Get

Following these instructions will create:
- Complete app structure with Ionic React Router
- Tab navigation with proper selection logic
- All pages using Salt Design System components
- Consistent styling with Salt CSS variables
- Proper navigation patterns with useIonRouter
- Mobile-optimized UI with safe areas and touch targets
- TypeScript types for all data
- Icon component system
- Theme provider with light/dark mode

### Quick Reference: Files to Create

After running the prompt, you should have these files:

**Core Files:**
- `src/main.tsx` - Entry point with SaltThemeProvider
- `src/App.tsx` - Main app with routing and TabBar
- `src/index.css` - Global styles and Salt overrides
- `src/theme/variables.css` - Ionic theme variables
- `src/theme/SaltThemeProvider.tsx` - Theme provider component

**Icon System:**
- `src/components/icons/Icon.tsx` - Base icon component
- `src/components/icons/[IconName].tsx` - Individual icon components
- `src/components/icons/index.ts` - Icon exports

**Pages:**
- `src/pages/Home.tsx` - Home page
- `src/pages/[FeatureName].tsx` - Feature pages
- `src/pages/[FeatureName].css` - Page-specific styles

**Data:**
- `src/data/[featureName]Data.ts` - Mock data with TypeScript types

### Troubleshooting

If the AI assistant doesn't follow patterns correctly:
1. Explicitly reference the section name (e.g., "Follow the Header Patterns section")
2. Point to specific code examples in instructions.md
3. Remind it to check the Checklist for New Pages
4. Ask it to verify against Anti-Patterns section
5. Break down the request into smaller steps if needed

---

## How to Use This Guide

**When building a new screen or component:**

1. **Start with Page Structure**: Use the standard `IonPage`, `IonHeader`, `IonToolbar`, and `IonContent` structure
2. **Follow Component Patterns**: Use Salt components (`StackLayout`, `FlexLayout`, `Text`, `Button`) instead of generic HTML elements
3. **Apply Styling Rules**: Always use Salt CSS variables (`var(--salt-spacing-150)`, `var(--salt-content-primary-foreground)`, etc.) - never hardcode values
4. **Use Navigation Patterns**: Use `useIonRouter` for navigation, pass context via `location.state`
5. **Check the Checklist**: Review the "Checklist for New Pages" section before completing
6. **Avoid Anti-Patterns**: Reference the "Anti-Patterns to Avoid" section to ensure you're not making common mistakes

**Quick Reference:**
- Page structure: See [Page Structure](#page-structure)
- Header patterns: See [Header Patterns](#header-patterns)
- List patterns: See [List Patterns](#list-patterns)
- Action bars: See [Action Bars & Buttons](#action-bars--buttons)
- Styling: See [Styling & Theming](#styling--theming)

## Using This Guide as an Agent Prompt

When working with an AI coding assistant, reference this guide to ensure consistent implementation. Here are example prompts you can use:

### Example 1: Building a New Screen

```
Build a new [ScreenName] page following the patterns in instructions.md. 
The screen should:
- Display a list of items with search functionality
- Include a header with back navigation and title
- Have a fixed action bar at the bottom with primary and secondary actions
- Use Salt components and CSS variables throughout
- Follow the Page Structure and Header Patterns sections
- Check the Checklist for New Pages before completing
```

### Example 2: Building a Detail Screen

```
Create a [DetailScreenName] detail page using instructions.md as a reference. 
Requirements:
- Use the standard IonPage structure
- Header with three-column layout (back button, title, cancel button)
- Pass context via location.state when navigating to this page
- Use Salt StackLayout and FlexLayout for content organization
- Ensure all styling uses Salt CSS variables
- Add ARIA labels to icon-only buttons
```

### Example 3: Adding a Feature

```
Add a new [FeatureName] feature following instructions.md patterns:
- Create routes under /feature-name/ prefix
- Use useIonRouter for all navigation
- Extract mock data to a separate data file with TypeScript types
- Use Salt components (Button, Text, StackLayout, FlexLayout)
- Follow Mobile UI Best Practices section
- Avoid all anti-patterns listed in the guide
```

### Example 4: Quick Component

```
Create a [ComponentName] component following instructions.md:
- Use Salt components instead of generic HTML
- Apply Salt spacing variables (var(--salt-spacing-150))
- Use icon components from the icons directory
- Ensure touch targets are at least 44x44px
- Add proper ARIA labels
```

### Tips for Best Results

1. **Be specific**: Mention which sections of the guide to follow
2. **Reference patterns**: Point to specific patterns (e.g., "Use the Three-Column Header Layout")
3. **Include requirements**: State what the screen/component should do
4. **Mention checklist**: Ask to verify against the Checklist for New Pages
5. **Avoid anti-patterns**: Explicitly mention avoiding the anti-patterns section

## Table of Contents

- [Getting Started: Building a New App from Scratch](#getting-started-building-a-new-app-from-scratch)
- [How to Use This Guide](#how-to-use-this-guide)
- [Using This Guide as an Agent Prompt](#using-this-guide-as-an-agent-prompt)
- [Navigation & Routing](#navigation--routing)
- [Styling & Theming](#styling--theming)
- [Component Patterns](#component-patterns)
- [Icons](#icons)
- [Data Organization](#data-organization)
- [Mobile UI Best Practices](#mobile-ui-best-practices)
- [Page Structure](#page-structure)
- [Header Patterns](#header-patterns)
- [List Patterns](#list-patterns)
- [Action Bars & Buttons](#action-bars--buttons)
- [Animations & Transitions](#animations--transitions)
- [Performance & Accessibility](#performance--accessibility)
- [App Structure](#app-structure)
- [Common Patterns](#common-patterns)

---

## Navigation & Routing

### DO: Use `useIonRouter` for Navigation

**Always use `useIonRouter` instead of `history.push` or `history.replace`** to enable Ionic transitions:

```typescript
import { useIonRouter } from '@ionic/react';

const MyComponent: React.FC = () => {
  const router = useIonRouter();

  const handleNavigation = () => {
    router.push('/target-path', 'root', 'replace');
  };
};
```

### DO: Pass Context via `location.state`

When navigating to detail pages, pass context via `location.state` to maintain tab bar highlighting and provide data:

```typescript
import { useHistory, useLocation } from 'react-router-dom';

history.push('/item-details', {
  item: itemData,
  source: 'list-view',
  actionType: 'edit',
});
const location = useLocation();
const state = location.state as { item: ItemType; source: string };
const item = state?.item;
```

### DO: Use Route Prefixes for Feature Groups

Group related routes under a common prefix:

```typescript
<Route exact path="/feature" />
<Route exact path="/feature/create" />
<Route exact path="/feature/edit" />
<Route exact path="/feature/history" />
```

### DO: Maintain Tab Bar Context

Tab bar highlighting should reflect the current section, even on detail pages:

```typescript
const isTabSelected = (path: string) => {
  const currentPath = location.pathname;
  const state = location.state as TabBarLocationState | undefined;

  if (currentPath === '/item-details' && state?.source) {
    if (state.source === 'list-view' && path === '/list') return true;
    if (state.source === 'dashboard' && path === '/dashboard') return true;
    return false;
  }

  if (currentPath.startsWith('/feature/') && path === '/feature') {
    return true;
  }

  return currentPath === path || currentPath.startsWith(path + '/');
};
```

---

## Styling & Theming

### DO: Always Use Salt Design System CSS Variables

**Never hardcode colors, spacing, or sizing.** Use Salt's CSS variables:

```css
color: var(--salt-content-primary-foreground);
padding: var(--salt-spacing-150);
background: var(--salt-card-background);
border-color: var(--salt-separable-secondary-borderColor);
```

### DO: Use Salt Spacing Variables Consistently

Use Salt spacing scale variables in component props and Salt CSS variables:

```typescript
<StackLayout gap={1}>
  <Text styleAs="h4">Title</Text>
</StackLayout>
```

```css
.content-padding {
  padding: var(--salt-spacing-150);
}
```

```typescript
<div className="content-padding">
  Content
</div>
```

---

## Component Patterns

### DO: Use Salt Components for UI Elements

Prefer Salt components for layout and UI:

```typescript
import { Button, Card, FlexLayout, StackLayout, Text } from '@salt-ds/core';

<StackLayout gap={1}>
  <Text styleAs="h4">Title</Text>
  <Text styleAs="label">Description</Text>
</StackLayout>
```

### DO: Use Ionic Components for Mobile Structure

Use Ionic components for page structure and mobile-specific features:

```typescript
import { IonContent, IonHeader, IonPage, IonToolbar } from '@ionic/react';

<IonPage>
  <IonHeader translucent={false}>
    <IonToolbar>
      {/* Toolbar content */}
    </IonToolbar>
  </IonHeader>
  <IonContent fullscreen>
    {/* Page content */}
  </IonContent>
</IonPage>
```

---

## Icons

### DO: Convert SVGs to TSX Components

All icons should be TSX components in a dedicated icons directory:

```typescript
import React from 'react';
import { Icon, IconProps } from './Icon';

export const ArrowBack: React.FC<Omit<IconProps, 'children'>> = (props) => (
  <Icon {...props} viewBox="0 0 48 48">
    <path d="M30.83 14.83l-2.42-2.42L18 22l10.41 9.59 2.42-2.42L22.84 22z"/>
  </Icon>
);
```

### DO: Use Icon Components Instead of Text

**Always use icon components for navigation and actions:**

```typescript
<ArrowBack size={18} />
```

### DO: Apply Inline Icon Classes

Use the `salt-inline-icon` CSS class for inline icons in buttons and text to ensure proper alignment:

```typescript
<Button>
  <ArrowBack size={18} className="salt-inline-icon" />
  <Text styleAs="label">Back</Text>
</Button>
```

**CSS class definition:**
```css
.salt-inline-icon {
  flex-shrink: 0;
}
```

### DO: Use Consistent Icon Sizes

Standard sizes:
- **18px**: Header navigation (back buttons, cancel buttons)
- **20px**: List items, inline actions
- **24px-30px**: Tab bar icons
- **16px**: Small inline status icons

---

## Data Organization

### DO: Extract Mock Data to Separate Files

Store mock data in a dedicated data directory with TypeScript types:

```typescript
export type Item = {
  id: string;
  title: string;
  value: string;
  status: 'active' | 'inactive';
};

export const itemsData: Item[] = [
  {
    id: '1',
    title: 'Example Item',
    value: '100.00',
    status: 'active',
  },
];
```

### DO: Export Types with Data

Always export the TypeScript type alongside the data:

```typescript
export type MyDataType = { /* ... */ };
export const myData: MyDataType[] = [ /* ... */ ];
```

---

## Mobile UI Best Practices

### DO: Use Full-Screen Content

Use `fullscreen` prop on `IonContent` for immersive mobile experience:

```typescript
<IonContent fullscreen>
  {/* Content */}
</IonContent>
```

### DO: Respect Safe Areas

Always account for safe area insets on iOS using Salt spacing variables:

```css
.safe-area-bottom {
  padding-bottom: calc(var(--salt-spacing-150) + env(safe-area-inset-bottom));
}
```

```typescript
<div className="safe-area-bottom">
  Content
</div>
```

### DO: Implement Touch-Friendly Targets

Ensure interactive elements are at least 44x44px for touch. Salt Button components handle this automatically.

### DO: Set Minimum Font Size for Inputs

**Always set font-size to at least 16px on input fields** to prevent iOS Safari from auto-zooming when users focus on the input:

```css
input,
textarea,
select {
  font-size: 16px;
  font-size: var(--salt-text-fontSize);
}
```

```typescript
<input type="text" />
```

**For Salt Input components**, ensure the font size is at least 16px via CSS or check Salt's default input styling.

### DO: Prevent Text Size Adjustment

Prevent iOS Safari from automatically adjusting text size:

```css
html,
body,
input,
textarea,
select,
button {
  -webkit-text-size-adjust: 100%;
  text-size-adjust: 100%;
}
```

### DO: Optimize Viewport Settings

Ensure proper viewport meta tag for mobile:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
```

**Note**: Consider allowing user scaling for accessibility. Use `user-scalable=yes` if your app needs to support accessibility features.

### DO: Use Edge-to-Edge Lists Where Appropriate

For list views, use Salt components and spacing variables to achieve edge-to-edge design.

### DO: Keep Search Fields in Headers

Search inputs should be in headers to remain fixed during scroll:

```typescript
<IonHeader>
  <IonToolbar>
    {/* Search input */}
  </IonToolbar>
</IonHeader>
```

### DO: Use Consistent List Row Patterns

Use Salt components for consistent list structure. Prefer Salt's layout components for list items.

---

## Page Structure

### DO: Follow Standard Page Structure

Every page should follow this structure:

```typescript
import { IonContent, IonHeader, IonPage, IonToolbar } from '@ionic/react';

const MyPage: React.FC = () => {
  return (
    <IonPage>
      <IonHeader translucent={false}>
        <IonToolbar className="salt-toolbar">
          {/* Header content */}
        </IonToolbar>
      </IonHeader>
      <IonContent fullscreen>
        <div className="salt-page-shell">
          {/* Page content */}
        </div>
      </IonContent>
    </IonPage>
  );
};
```

**CSS classes to define:**
- `.salt-page-shell` - Provides consistent page background using Salt variables

```css
.salt-page-shell {
  background: var(--salt-container-primary-background);
}
```

---

## Header Patterns

### DO: Use Three-Column Header Layout

For headers with back navigation, title, and actions, use Salt's FlexLayout with proper spacing:

```typescript
<IonToolbar className="salt-toolbar">
  <FlexLayout justify="space-between" align="center" gap={2}>
    <Button
      appearance="transparent"
      sentiment="neutral"
      onClick={handleBack}
    >
      <ArrowBack size={18} className="salt-inline-icon" />
    </Button>
    <Text styleAs="h4" className="salt-toolbar-title">Page Title</Text>
    <Button
      appearance="transparent"
      sentiment="neutral"
      onClick={handleCancel}
    >
      <Text styleAs="label">Cancel</Text>
    </Button>
  </FlexLayout>
</IonToolbar>
```

**CSS classes to define:**
- `.salt-toolbar` - Sets Ionic toolbar CSS variables using Salt variables
- `.salt-toolbar-title` - Styles for centered title text
- `.salt-inline-icon` - Utility class for icon alignment (`flex-shrink: 0`)

```css
.salt-toolbar {
  --background: var(--salt-container-primary-background);
  --color: var(--salt-content-primary-foreground);
  padding: var(--salt-spacing-50);
  padding-top: var(--salt-spacing-100);
}

.salt-toolbar-title {
  font-weight: 600;
  text-align: center;
}

.salt-inline-icon {
  flex-shrink: 0;
}
```

### DO: Add Cancel Buttons to Modal-Like Flows

For multi-step flows or modal-like pages, add a cancel button in the header:

```typescript
<Button
  appearance="transparent"
  sentiment="neutral"
  onClick={() => router.push('/home', 'root', 'replace')}
>
  <Text styleAs="label">Cancel</Text>
</Button>
```

---

## List Patterns

### DO: Use Salt Components for Lists

Use Salt components for consistent list styling. Prefer Salt's built-in list components over custom CSS classes.

### DO: Structure List Items Consistently

Use Salt components for list structure:

```typescript
<StackLayout gap={0.5}>
  <Text styleAs="h4">Primary Text</Text>
  <Text styleAs="label">Secondary Text</Text>
</StackLayout>
```

---

## Action Bars & Buttons

### DO: Use Fixed Bottom Action Bars

For primary actions at the bottom of pages, use a fixed container with Salt components:

```css
.action-bar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  padding: var(--salt-spacing-150);
  padding-bottom: calc(var(--salt-spacing-150) + env(safe-area-inset-bottom));
  background: var(--salt-card-background);
  box-shadow: 0 -2px 10px rgba(0, 0, 0, 0.1);
  border-top: 1px solid var(--salt-separable-secondary-borderColor);
}
```

```typescript
<div className="action-bar">
  <FlexLayout gap={1}>
    <Button
      appearance="bordered"
      sentiment="neutral"
      onClick={handleSecondary}
    >
      <Text styleAs="label">Cancel</Text>
    </Button>
    <Button
      appearance="solid"
      sentiment="accented"
      onClick={handlePrimary}
    >
      <Text styleAs="label">Primary Action</Text>
    </Button>
  </FlexLayout>
</div>
```

### DO: Add Bottom Padding for Action Bars

Add padding to content when using fixed action bars using Salt spacing variables:

```css
.content-with-action-bar {
  padding-bottom: var(--salt-spacing-600);
}
```

```typescript
<StackLayout gap={0} className="content-with-action-bar">
  {/* Content */}
</StackLayout>
```

### DO: Use Salt Button Props

Style buttons using Salt Button component props and appearance options. Avoid custom CSS classes.

---

## Animations & Transitions

### DO: Use Salt Components for Animations

Prefer Salt components that handle animations internally. For custom animations, use React state and minimal inline styles with Salt spacing variables.

---

## Performance & Accessibility

### DO: Use Conditional Rendering

Only render expensive components when needed:

```typescript
{isExpanded && (
  <ExpensiveComponent />
)}
```

### DO: Provide ARIA Labels

Add aria-label to icon-only buttons:

```typescript
<Button
  aria-label="Back"
  onClick={handleBack}
>
  <ArrowBack size={18} />
</Button>
```

### DO: Optimize Images

- Use appropriate image formats (WebP, SVG)
- Lazy load images when possible
- Provide alt text for images

### DO: Handle Loading States

Show loading indicators during async operations:

```typescript
{isLoading ? (
  <IonSpinner />
) : (
  <Content />
)}
```

---

## App Structure

### Base App Setup

The main app component should follow this structure with Ionic React Router and Tabs:

```typescript
import { Route, useLocation } from 'react-router-dom';
import {
  IonApp,
  IonLabel,
  IonRouterOutlet,
  IonTabBar,
  IonTabButton,
  IonTabs,
  setupIonicReact,
  useIonRouter
} from '@ionic/react';
import { IonReactRouter } from '@ionic/react-router';
import { Home as HomeIcon, List as ListIcon, Settings as SettingsIcon } from './components/icons';
import HomePage from './pages/Home';
import ListPage from './pages/List';
import SettingsPage from './pages/Settings';

import '@ionic/react/css/core.css';
import '@ionic/react/css/normalize.css';
import '@ionic/react/css/structure.css';
import '@ionic/react/css/typography.css';
import '@ionic/react/css/palettes/dark.system.css';
import './theme/variables.css';
import './index.css';

setupIonicReact({
  mode: 'ios'
});

interface TabBarLocationState {
  source?: string;
}

const TabBar: React.FC = () => {
  const router = useIonRouter();
  const location = useLocation();

  const handleTabClick = (path: string) => {
    router.push(path, 'root', 'replace');
  };

  const isTabSelected = (path: string) => {
    const currentPath = location.pathname;
    const state = location.state as TabBarLocationState | undefined;

    if (currentPath === '/item-details' && state?.source) {
      if (state.source === 'list-view' && path === '/list') return true;
      if (state.source === 'dashboard' && path === '/dashboard') return true;
      return false;
    }

    if (currentPath.startsWith('/feature/') && path === '/feature') {
      return true;
    }

    if (path === '/home' && (currentPath === '/' || currentPath === '/home')) {
      return true;
    }

    return currentPath === path || currentPath.startsWith(path + '/');
  };

  return (
    <IonTabBar slot="bottom">
      <IonTabButton
        tab="home"
        selected={isTabSelected('/home')}
        onClick={() => handleTabClick('/home')}
      >
        <HomeIcon size={30} />
        <IonLabel>Home</IonLabel>
      </IonTabButton>
      <IonTabButton
        tab="list"
        selected={isTabSelected('/list')}
        onClick={() => handleTabClick('/list')}
      >
        <ListIcon size={30} />
        <IonLabel>List</IonLabel>
      </IonTabButton>
      <IonTabButton
        tab="settings"
        selected={isTabSelected('/settings')}
        onClick={() => handleTabClick('/settings')}
      >
        <SettingsIcon size={30} />
        <IonLabel>Settings</IonLabel>
      </IonTabButton>
    </IonTabBar>
  );
};

const App: React.FC = () => (
  <IonApp>
    <IonReactRouter>
      <IonTabs>
        <IonRouterOutlet>
          <Route exact path="/">
            <HomePage />
          </Route>
          <Route exact path="/home">
            <HomePage />
          </Route>
          <Route exact path="/list">
            <ListPage />
          </Route>
          <Route path="/list/item-details/:itemId">
            <ItemDetailsPage />
          </Route>
          <Route exact path="/settings">
            <SettingsPage />
          </Route>
        </IonRouterOutlet>
        <TabBar />
      </IonTabs>
    </IonReactRouter>
  </IonApp>
);

export default App;
```

### Key Points

- Use `IonApp` as the root component
- Wrap everything in `IonReactRouter` for routing
- Use `IonTabs` to enable tab navigation
- `IonRouterOutlet` contains all route definitions
- `TabBar` component handles bottom navigation
- Use `useIonRouter` in TabBar for navigation
- Tab selection logic maintains context across detail pages
- Support route prefixes for feature grouping

---

## Common Patterns

### Tab Bar Implementation

```typescript
const TabBar: React.FC = () => {
  const router = useIonRouter();
  const location = useLocation();

  const handleTabClick = (path: string) => {
    router.push(path, 'root', 'replace');
  };

  const isTabSelected = (path: string) => {
    const currentPath = location.pathname;
    const state = location.state as TabBarLocationState | undefined;

    if (currentPath === '/item-details' && state?.source) {
      if (state.source === 'list-view' && path === '/list') return true;
      if (state.source === 'dashboard' && path === '/dashboard') return true;
      return false;
    }

    if (currentPath.startsWith('/feature/') && path === '/feature') {
      return true;
    }

    return currentPath === path || currentPath.startsWith(path + '/');
  };

  return (
    <IonTabBar slot="bottom">
      <IonTabButton
        tab="home"
        selected={isTabSelected('/home')}
        onClick={() => handleTabClick('/home')}
      >
        <HomeIcon size={30} />
        <IonLabel>Home</IonLabel>
      </IonTabButton>
      {/* More tabs */}
    </IonTabBar>
  );
};
```

### Search with Filter

```typescript
<IonHeader>
  <IonToolbar>
    <FlexLayout align="center" gap={1}>
      <FlexLayout align="center" gap={1}>
        <Search size={20} />
        <input
          type="search"
          value={searchText}
          placeholder="Search"
          onChange={e => setSearchText(e.target.value)}
        />
      </FlexLayout>
      <Button
        appearance="bordered"
        sentiment="neutral"
        aria-label="Filter"
      >
        <Filter size={20} />
      </Button>
    </FlexLayout>
  </IonToolbar>
</IonHeader>
```

---

## Checklist for New Pages

- [ ] Page uses `IonPage`, `IonHeader`, `IonToolbar`, `IonContent`
- [ ] Header uses Salt components for layout
- [ ] Back navigation uses icon components
- [ ] All styling uses Salt CSS variables
- [ ] Spacing uses Salt spacing variables
- [ ] Icons are TSX components (not inline SVG)
- [ ] Mock data extracted to dedicated data directory if applicable
- [ ] Safe area insets respected for bottom padding
- [ ] Touch targets are at least 44x44px
- [ ] Input fields have font-size of at least 16px to prevent iOS auto-zoom
- [ ] Text size adjustment prevented with `-webkit-text-size-adjust: 100%`
- [ ] ARIA labels on icon-only buttons
- [ ] Navigation uses `useIonRouter` with proper direction
- [ ] Context passed via `location.state` when needed

---

## Anti-Patterns to Avoid

### DON'T: Use `history.push` Directly

```typescript
import { useIonRouter } from '@ionic/react';

const router = useIonRouter();
router.push('/target', 'root', 'replace');
```

### DON'T: Hardcode Colors or Spacing

```css
.example {
  color: var(--salt-content-primary-foreground);
  padding: var(--salt-spacing-150);
}
```

```typescript
<div className="example">
```

### DON'T: Use Text for Navigation

```typescript
<ArrowBack size={18} />
```

### DON'T: Store Mock Data in Components

```typescript
export const data = [/* ... */];
```

### DON'T: Ignore Safe Areas

```css
padding-bottom: calc(var(--salt-spacing-150) + env(safe-area-inset-bottom));
```

### DON'T: Use Small Font Sizes on Inputs

```css
input {
  font-size: 16px;
  font-size: var(--salt-text-fontSize);
}
```

```typescript
<input type="text" />
```

---

## Additional Resources

- [Ionic React Documentation](https://ionicframework.com/docs/react)
- [Salt Design System Documentation](https://www.saltdesignsystem.com/)
- [React Router Documentation](https://reactrouter.com/)
- [Mobile Web Best Practices](https://web.dev/mobile/)

---

**Remember**: Consistency is key. Following these patterns ensures maintainability, scalability, and excellent mobile UX across your application.


