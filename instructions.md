# React + Ionic + Salt Design System - Mobile Web App Instructions


### Quick Start

Copy and paste this example prompt to your AI coding assistant:

Build a complete mobile web app following instructions.md exactly. Include:
- Install all dependencies (run npm install commands)
- All setup (dependencies, CSS imports, SaltThemeProvider)
- App.tsx with tab navigation
- 3 tab pages (Home, Details, Settings) using the Tab Page Template
  * use the web page image as a refernce for the Home page and convert to a responsive view
  * use the hand drawn image as a reference for the Details page
- Add a light mode dark mode toggle switch on the settings page
- Tab bar with Salt icons

Use the templates in instructions.md - do not create custom patterns.

## For AI Agents

**When building or modifying this application, you MUST:**

1. **Install dependencies FIRST** - Run `npm install` commands before creating any source files
2. **Follow ALL patterns exactly** - Use the templates and code examples provided
3. **Use Salt Design System components** - Never use generic HTML when a Salt component exists
4. **Use Salt CSS variables** - Never hardcode colors, spacing, or sizing
5. **Include headers on ALL pages** - Every page MUST have `IonHeader` with `IonToolbar`
6. **Use Salt icons only** - Import from `@salt-ds/icons`, never use Ionic or Material icons
7. **Follow the Tab Page Template** - Use the provided template for all tab pages
8. **Check the Checklist** - Verify all requirements before completing any page

**Quick Reference:**
- Tab page template: See "Page Template" section
- Header pattern: See "Header Pattern" section  
- CSS setup: See "Required CSS Variables" section
- Icons: See "Icons" section
- Navigation: See "Navigation" section

---

Essential patterns and requirements for building mobile web applications with React, Ionic React, and Salt Design System.

## Critical Requirements

- **All icons MUST be Salt Design System icons** from `@salt-ds/icons`
- **Every page MUST have an `IonHeader` with `IonToolbar`** - NO EXCEPTIONS
- **All styling MUST use Salt CSS variables** - no hardcoded colors, spacing, or sizing
- **Tab bar background MUST match app content background** using Salt variables

## Setup

### Setup Steps (For AI Agents Building from Scratch)

**Follow these steps in order:**

1. **Create project structure** (if needed) - Create `package.json`, `vite.config.ts`, `tsconfig.json`, `.gitignore`, and `index.html`
2. **Install dependencies** - Run the npm install commands below (REQUIRED before creating source files)
3. **Create source files** - Create all files in `src/` directory following the templates
4. **Verify setup** - Check that all files are created and dependencies are installed

### Initial Project Setup

If starting from scratch, create a new Vite + React + TypeScript project:

```bash
npm create vite@latest mobile-web-starter -- --template react-ts
cd mobile-web-starter
```

### Dependencies

**CRITICAL: You MUST install all dependencies before creating source files. Run these commands:**

```bash
npm install @ionic/react@^8.5.0 @ionic/react-router@^8.5.0 react-router@^5.3.4 react-router-dom@^5.3.4 @salt-ds/core@^1.54.0 @salt-ds/icons@^1.15.0 @salt-ds/theme@^1.37.0 react@^18.2.0 react-dom@^18.2.0 react-chartjs-2
npm install -D @types/react@^18.2.66 @types/react-dom@^18.2.22 @types/react-router@^5.1.20 @types/react-router-dom@^5.3.3 @typescript-eslint/eslint-plugin@^7.2.0 @typescript-eslint/parser@^7.2.0 @vitejs/plugin-react@^4.2.1 eslint@^8.57.0 eslint-plugin-react-hooks@^4.6.0 eslint-plugin-react-refresh@^0.4.6 typescript@^5.2.2 vite@^5.2.0
```

**For AI Agents:** If you are building the app from scratch, you MUST execute these npm install commands using the terminal before proceeding to create source files. Do not skip this step.

**Important Version Notes:**
- Use React 18 (not React 19) for compatibility with type definitions
- Salt Design System packages have different version numbers:
  - `@salt-ds/core`: `^1.54.0`
  - `@salt-ds/icons`: `^1.15.0`
  - `@salt-ds/theme`: `^1.37.0`

### Project Structure

Create the following directory structure:

```
src/
├── components/
├── data/
├── pages/
│   ├── Home.tsx
│   ├── List.tsx
│   └── Settings.tsx
├── theme/
│   ├── SaltThemeProvider.tsx
│   └── variables.css
├── App.tsx
├── main.tsx
├── index.css
└── style.css
```

### Vite Configuration

Ensure `vite.config.ts` includes the React plugin:

```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
})
```

### TypeScript Configuration

Ensure `tsconfig.json` includes:

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "jsx": "react-jsx",
    "moduleResolution": "bundler",
    "strict": true
  },
  "include": ["src"]
}
```

### .gitignore Setup

Create a `.gitignore` file in the project root with common patterns:

```gitignore
node_modules
dist
logs
*.log
.vite
```

**Key directories/files to ignore:**
- `node_modules/` - Dependencies (always ignore)
- `dist/` - Build output directory
- `.env*` - Environment variable files (may contain secrets)
- Editor configs (`.vscode/`, `.idea/`, `.DS_Store`)
- Log files (`*.log`)
- Cache directories (`.vite/`, `.cache/`, `.parcel-cache/`)

### main.tsx Setup

Create `src/main.tsx` with Ionic setup and all required CSS imports:

```typescript
import React from 'react';
import ReactDOM from 'react-dom/client';
import { setupIonicReact } from '@ionic/react';
import App from './App';

// Ionic CSS imports
import '@ionic/react/css/core.css';
import '@ionic/react/css/normalize.css';
import '@ionic/react/css/structure.css';
import '@ionic/react/css/typography.css';
import '@ionic/react/css/palettes/dark.system.css';
import './theme/variables.css';
import './style.css';
import './index.css';

setupIonicReact({
  mode: 'ios',
});

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
);
```

**Critical:** 
- `setupIonicReact` MUST be called with `mode: 'ios'`
- All CSS imports must be in this exact order
- Salt CSS imports are in `SaltThemeProvider.tsx`, NOT in `main.tsx`

### Required CSS Imports in SaltThemeProvider.tsx

```typescript
import '@salt-ds/core/css/salt-core.css';
import '@salt-ds/theme/css/theme-next.css';
import '@salt-ds/theme/css/theme.css';
```

### Required CSS Variables in style.css

**CRITICAL: All styles MUST be in `style.css`. Do NOT create individual CSS files for pages or components. Use utility classes for maximum reuse.**

```css
:root.salt-theme,
html.salt-theme,
.salt-theme {
  --saltButton-borderRadius: 10px;
  --saltCard-borderRadius: 10px;
  --salt-palette-text-fontFamily: "Amplitude", -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif !important;
}

.salt-theme[data-mode=light] {
  --salt-container-primary-background: #fafafa;
  --salt-card-background: white;
}

.salt-theme[data-mode=dark] {
  --salt-container-primary-background: #171e26;
  --salt-card-background: rgb(8, 8, 8);
}

.salt-search-input {
  flex: 1;
  align-items: center;
  gap: var(--salt-spacing-100);
  background: var(--salt-container-secondary-background);
  border: 1px solid var(--salt-separable-secondary-borderColor);
  border-radius: var(--sale-button-radius);
  padding: var(--salt-spacing-50);
}

.salt-search-input input {
  flex: 1;
  background: transparent;
  border: none;
  outline: none;
  font-size: 0.875rem;
  color: var(--salt-content-primary-foreground);
  font-family: inherit;
}

/* Tab bar styling */
ion-tab-bar {
  --background: var(--salt-card-background);
  --color: var(--salt-content-secondary-foreground);
  --color-selected: var(--salt-accent-foreground);
  --border: 1px solid var(--salt-separable-secondary-borderColor);
  border-top: 1px solid var(--salt-separable-secondary-borderColor);
  height: 70px;
}

ion-tab-bar::part(native) {
  background: var(--salt-card-background);
  color: var(--salt-content-secondary-foreground);
  border-top: 1px solid var(--salt-separable-secondary-borderColor);
}

ion-tab-button {
  --color: var(--salt-content-primary-foreground);
  --color-selected: var(--salt-accent-foreground);
  --padding-top: 6px;
  --padding-bottom: 6px;
  --padding-start: 6px;
  --padding-end: 6px;
  font-size: 0.75rem;
  color: var(--salt-content-primary-foreground);
  font-weight: 500;
}

ion-tab-button.tab-selected {
  --color: var(--salt-accent-foreground);
  color: var(--salt-accent-foreground);
  opacity: 1;
  font-weight: 600;
}

ion-tab-button::part(native) {
  background: transparent;
  border-radius: 12px;
  overflow: hidden;
  margin: 4px;
  width: calc(100% - 8px);
  height: calc(100% - 8px);
  box-sizing: border-box;
}

ion-tab-button.tab-selected::part(native) {
  background: color-mix(in srgb, var(--salt-accent-background) 90%, transparent);
}

ion-tab-button ion-label {
  color: var(--salt-content-primary-foreground);
  opacity: 1 !important;
  transition: color 0.2s ease;
}

ion-tab-button.tab-selected ion-label {
  color: var(--salt-accent-foreground) !important;
  opacity: 1 !important;
}

ion-tab-button:hover ion-label,
ion-tab-button:focus ion-label {
  color: var(--salt-content-primary-foreground);
  opacity: 1 !important;
}

ion-tab-button.tab-selected:hover ion-label,
ion-tab-button.tab-selected:focus ion-label {
  color: var(--salt-accent-foreground) !important;
  opacity: 1 !important;
}

ion-tab-button img,
ion-tab-button ion-icon,
ion-tab-button .tab-icon {
  opacity: 0.8;
  color: var(--salt-content-primary-foreground);
  transition: opacity 0.2s ease, color 0.2s ease;
}

ion-tab-button.tab-selected img,
ion-tab-button.tab-selected ion-icon,
ion-tab-button.tab-selected .tab-icon {
  opacity: 1;
  color: var(--salt-accent-foreground);
}

ion-tab-button:hover .tab-icon,
ion-tab-button:focus .tab-icon {
  opacity: 1;
  color: var(--salt-content-primary-foreground);
}

ion-tab-button.tab-selected:hover .tab-icon,
ion-tab-button.tab-selected:focus .tab-icon {
  opacity: 1;
  color: var(--salt-accent-foreground);
}

/* Ionic component variables */
ion-app {
  --background: var(--salt-container-primary-background);
  --color: var(--salt-content-primary-foreground);
}

ion-content {
  --background: var(--salt-container-primary-background);
  --color: var(--salt-content-primary-foreground);
}

ion-page {
  --background: var(--salt-container-primary-background);
  --color: var(--salt-content-primary-foreground);
}

ion-header {
  --background: var(--salt-container-primary-background);
  --color: var(--salt-content-primary-foreground);
}

ion-toolbar {
  --background: var(--salt-container-primary-background);
  --color: var(--salt-content-primary-foreground);
  --border-color: var(--salt-separable-secondary-borderColor);
}

.salt-page-shell {
  background: var(--salt-container-primary-background);
}
```

## Page Template

### Tab Page Template

Use this template for all tab pages:

```typescript
import { IonContent, IonHeader, IonPage, IonToolbar } from '@ionic/react';
import { Button, Card, FlexLayout, StackLayout, Text } from '@salt-ds/core';
import { useHistory } from 'react-router-dom';
import { FilterIcon, SearchIcon } from '@salt-ds/icons';

const Tab1: React.FC = () => {
  const history = useHistory();
  const handleBack = () => history.goBack();

  return (
    <IonPage>
      <IonHeader translucent={false}>
        <IonToolbar className="salt-toolbar">
          <StackLayout gap={1} className="salt-toolbar-content">
            <FlexLayout justify="space-between" align="center" gap={2} style={{ width: '100%' }}>
              <Button
                appearance="transparent"
                sentiment="neutral"
                onClick={handleBack}
                style={{ padding: `0 var(--salt-spacing-100)` }}
              >
                <Text styleAs="label">Back</Text>
              </Button>
              <Text styleAs="h4">
                Tab 1
              </Text>
              <div style={{ width: '44px' }} />
            </FlexLayout>
          </StackLayout>
        </IonToolbar>
      </IonHeader>

      <IonContent fullscreen>
        <div className="salt-page-shell">
          <StackLayout className="salt-page-content" gap={1}>
            <Card>
              <Text styleAs="h4">Tab 1 content</Text>
            </Card>
          </StackLayout>
        </div>
      </IonContent>
    </IonPage>
  );
};

export default Tab1;
```



**Required CSS classes (all in style.css):**

```css
/* Toolbar Classes */
.salt-toolbar {
  --background: var(--salt-container-primary-background);
  --color: var(--salt-content-primary-foreground);
  --border-width: 0;
  --border-style: none;
  --box-shadow: none;
  border-bottom: none !important;
  box-shadow: none !important;
  padding: 0;
  height: auto;
}

.salt-toolbar-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0;
  height: 100%;
  gap: 5px;
}

.salt-toolbar-title {
  font-weight: 600;
  letter-spacing: 0.01em;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  max-width: 100%;
}

.salt-toolbar-button {
  padding: 0 var(--salt-spacing-100);
  min-width: auto;
}

.salt-inline-icon {
  flex-shrink: 0;
}

.salt-page-content {
  padding: var(--salt-spacing-150);
  padding-bottom: var(--salt-spacing-300);
}
```

### index.css (Global Styles Only)

Create `src/index.css` for **global styles only** (box-sizing, body, root). All component and utility styles go in `style.css`:

```css
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: "Amplitude", -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#root {
  width: 100%;
  height: 100vh;
}
```

**Important:** 
- `index.css` is for global resets and base styles only
- `style.css` contains ALL component styles, utility classes, and Ionic/Salt customizations
- `theme/variables.css` contains Ionic CSS variables only
- **DO NOT create individual CSS files for pages or components**

## Icons

**ALWAYS use Salt icons from `@salt-ds/icons`:**

```typescript
import { HomeIcon, ChevronLeftIcon, SearchIcon } from '@salt-ds/icons';

<HomeIcon size={2} />
<ChevronLeftIcon size={1} />
<SearchIcon size={1.5} />
```

**Size guidelines:**
- `size={1}`: Small (header navigation, back buttons)
- `size={1.5}`: Medium (list items, inline actions)
- `size={2}`: Large (tab bar icons)

## App.tsx Setup

**Complete App.tsx with tab navigation:**

```typescript
import { IonApp, IonRouterOutlet, IonTabs, IonTabBar, IonTabButton, IonLabel } from '@ionic/react';
import { IonReactRouter } from '@ionic/react-router';
import { Route, Redirect } from 'react-router-dom';
import { SaltThemeProviderNext } from './theme/SaltThemeProvider';
import Home from './pages/Home';
import List from './pages/List';
import Settings from './pages/Settings';
import { HomeIcon, ListIcon, SettingsIcon } from '@salt-ds/icons';

const App: React.FC = () => {
  return (
    <SaltThemeProviderNext>
      <IonApp>
        <IonReactRouter>
          <IonTabs>
            <IonRouterOutlet>
              <Route exact path="/home">
                <Home />
              </Route>
              <Route exact path="/list">
                <List />
              </Route>
              <Route exact path="/settings">
                <Settings />
              </Route>
              <Route exact path="/">
                <Redirect to="/home" />
              </Route>
            </IonRouterOutlet>
            <IonTabBar slot="bottom">
              <IonTabButton tab="home" href="/home">
                <div className="tab-icon">
                  <HomeIcon size={1.5} />
                </div>
                <IonLabel>Home</IonLabel>
              </IonTabButton>
              <IonTabButton tab="list" href="/list">
                <div className="tab-icon">
                  <ListIcon size={1.5} />
                </div>
                <IonLabel>List</IonLabel>
              </IonTabButton>
              <IonTabButton tab="settings" href="/settings">
                <div className="tab-icon">
                  <SettingsIcon size={1.5} />
                </div>
                <IonLabel>Settings</IonLabel>
              </IonTabButton>
            </IonTabBar>
          </IonTabs>
        </IonReactRouter>
      </IonApp>
    </SaltThemeProviderNext>
  );
};

export default App;
```

**Key Points:**
- Wrap everything in `SaltThemeProviderNext`
- Use `IonReactRouter` for routing
- Tab icons use `size={1.5}` (medium size for tab bar)
- Icons are wrapped in `<div className="tab-icon">` for proper styling
- **All styles must be in `style.css` - use utility classes, not component-specific classes**

## Navigation

**ALWAYS use `useIonRouter` for navigation:**

```typescript
import { useIonRouter } from '@ionic/react';

const router = useIonRouter();
router.push('/path', 'root', 'replace');
```

**Note:** The Tab Page Template uses `useHistory` for back navigation, which is acceptable for simple back navigation. For programmatic navigation, prefer `useIonRouter`.

## SaltThemeProvider

**Complete SaltThemeProvider.tsx:**

```typescript
import React, {
  createContext,
  useCallback,
  useContext,
  useEffect,
  useMemo,
  useState,
  type ReactNode,
} from 'react';
import { SaltProviderNext, type Mode } from '@salt-ds/core';

// CRITICAL: These CSS imports MUST be in this file
import '@salt-ds/core/css/salt-core.css';
import '@salt-ds/theme/css/theme-next.css';
import '@salt-ds/theme/css/theme.css';

type SaltThemeContextValue = {
  mode: Mode;
  setMode: (mode: Mode) => void;
  toggleMode: () => void;
};

const SALT_THEME_STORAGE_KEY = 'salt-theme-mode';
const SaltThemeContext = createContext<SaltThemeContextValue | undefined>(undefined);

export const useSaltTheme = (): SaltThemeContextValue => {
  const context = useContext(SaltThemeContext);
  if (!context) {
    throw new Error('useSaltTheme must be used within a SaltThemeProvider');
  }
  return context;
};

type SaltThemeProviderProps = {
  children: ReactNode;
};

export const SaltThemeProviderNext: React.FC<SaltThemeProviderProps> = ({ children }) => {
  const [mode, setMode] = useState<Mode>(() => {
    if (typeof window !== 'undefined') {
      const storedMode = window.localStorage.getItem(SALT_THEME_STORAGE_KEY) as Mode | null;
      if (storedMode === 'light' || storedMode === 'dark') {
        return storedMode;
      }
    }
    return 'dark';
  });

  useEffect(() => {
    if (typeof window !== 'undefined') {
      window.localStorage.setItem(SALT_THEME_STORAGE_KEY, mode);
    }
  }, [mode]);

  const toggleMode = useCallback(() => {
    setMode(prev => (prev === 'light' ? 'dark' : 'light'));
  }, []);

  const contextValue = useMemo(
    () => ({ mode, setMode, toggleMode }),
    [mode, toggleMode],
  );

  return (
    <SaltThemeContext.Provider value={contextValue}>
      <SaltProviderNext 
        mode={mode} 
        density="touch" 
        accent="teal"
        headingFont="Amplitude"
        actionFont="Amplitude"
      >
        {children}
      </SaltProviderNext>
    </SaltThemeContext.Provider>
  );
};
```

## Patterns

### Search Field
When adding a search field use the following code:

```typescript
          <FlexLayout align="center" gap={1}>
              <FlexLayout align="center" gap={1} className="salt-search-input">
                <SearchIcon size={1}/>
                <input type="search" placeholder="Search"/>
              </FlexLayout>
              <Button
                appearance="bordered"
                sentiment="neutral"
                aria-label="Filter"
              >
                <FilterIcon size={0.5} />
              </Button>
            </FlexLayout>
```


### Charts
Use react-charts-2 for any charts

example chart:
```typescript
            <Card>
              <StackLayout gap={1} className="salt-card-section">
                <Text styleAs="h4">Sample Donut Chart</Text>
                <div style={{ height: '300px', width: '100%' }}>
                  <Doughnut data={chartData} options={chartOptions} />
                </div>
              </StackLayout>
            </Card>
```

### Lists




## Development

### Running the Development Server

```bash
npm run dev
```

The app will be available at `http://localhost:5173` (default Vite port).

### Building for Production

```bash
npm run build
```

Output will be in the `dist/` directory.

### Preview Production Build

```bash
npm run preview
```

## Troubleshooting

### Common Issues

**Error: "Cannot find module 'react' or its corresponding type declarations"**
- Run `npm install` to install all dependencies
- Verify React version is `^18.2.0` (not React 19)
- Ensure `@types/react` and `@types/react-dom` are installed

**Error: "No matching version found for @salt-ds/core@^4.0.0"**
- Salt Design System packages use different version numbers
- Use: `@salt-ds/core@^1.54.0`, `@salt-ds/icons@^1.15.0`, `@salt-ds/theme@^1.37.0`

**Icons not displaying in tab bar**
- Verify icons are imported from `@salt-ds/icons`
- Check that icons are wrapped in `<div className="tab-icon">`
- Ensure icon size is `size={2}` for tab bar icons

**Tab label text disappears on hover**
- Ensure `ion-label` has explicit `opacity: 1 !important` in CSS
- Add hover and focus states for `ion-label` to maintain visibility
- Check that the CSS includes the hover/focus rules from the style.css template

**TypeScript errors after installation**
- Restart your IDE/editor
- Run `npm install` again to ensure all packages are installed
- Check that `tsconfig.json` has correct configuration

**CSS variables not working**
- Verify `SaltThemeProvider.tsx` is wrapping your app
- Check that all CSS files are imported in the correct order
- Ensure Salt CSS imports are in `SaltThemeProvider.tsx`, not `main.tsx`

## Checklist for New Pages

- [ ] Page uses `IonPage`, `IonHeader`, `IonToolbar`, `IonContent`
- [ ] Header uses three-column layout pattern
- [ ] All icons are Salt icons from `@salt-ds/icons`
- [ ] All styling uses Salt CSS variables
- [ ] **All styles are in `style.css` using utility classes**
- [ ] **No individual CSS files created for the page**
- [ ] Navigation uses `useIonRouter` (or `useHistory` for simple back navigation)
- [ ] Touch targets are at least 44x44px
- [ ] Input fields have font-size of at least 16px
