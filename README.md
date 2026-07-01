# @polly-fe/design-foundations

Framework-agnostic design primitives including icon fonts, global styles, typography, and shared CSS utilities used across Polly microfrontends.

---

## 📦 Entry Points

This package provides **two separate CSS bundles** for different use cases:

### 1. **Default (Lightweight)** - `@polly-fe/design-foundations`

Base styles without PrimeNG theme. Use this for non-Angular projects or when you don't need PrimeNG components.

```typescript
// Import in your project
import '@polly-fe/design-foundations';
// or
import '@polly-fe/design-foundations/styles';
```

**Includes:**
- ✅ Fonts
- ✅ Global styles  
- ✅ Icons
- ✅ Typography
- ✅ Animations
- ✅ Utilities
- ✅ PrimeNG theme

**File size:** ~50-100KB (smaller, lightweight)

---

### 2. **With PrimeNG Theme** - `@polly-fe/design-foundations/primeng`

Full package including PrimeNG theme. Use this for Angular projects using PrimeNG components.

```typescript
// Import in your Angular project
import '@polly-fe/design-foundations/primeng';
```

**Includes:**
- ✅ Everything from default
- ✅ PrimeNG theme
- ✅ Design tokens (variables, mixins)
- ✅ Component styles (forms, overlays, panels, data, messages, etc.)

**File size:** ~200-300KB (larger, includes PrimeNG)

---

## 🚀 Installation

```bash
npm install @polly-fe/design-foundations
```

---

## 📖 Usage

### For React / Vue / Plain JS Projects (No PrimeNG)

```typescript
// In your main entry file (e.g., main.ts, index.tsx, main.js)
import '@polly-fe/design-foundations';
```

```html
<!-- Or in HTML -->
<link rel="stylesheet" href="node_modules/@polly-fe/design-foundations/dist/styles/index.css">
```

---

### For Angular Projects with PrimeNG

#### Option 1: In `angular.json` (Recommended)

```json
{
  "projects": {
    "your-app": {
      "architect": {
        "build": {
          "options": {
            "styles": [
              "node_modules/@polly-fe/design-foundations/dist/styles/primeng.css",
              "src/styles.scss"
            ]
          }
        }
      }
    }
  }
}
```

#### Option 2: In `styles.scss`

```scss
@import '@polly-fe/design-foundations/primeng';
```

---

## 📁 Package Structure

After build, the `dist/` folder contains:

```
dist/
├── styles/
│   ├── index.css        ← Default bundle (foundation styles only)
│   └── primeng.css      ← PrimeNG bundle (foundation + PrimeNG theme)
└── fonts/
    ├── iconset.eot
    ├── iconset.svg
    ├── iconset.ttf
    └── iconset.woff
```

---

## 🔧 Development

### Build Commands

```bash
# Build both versions (default + primeng)
npm run build

# Build only default (lightweight)
npm run build:scss:default

# Build only PrimeNG version
npm run build:scss:primeng

# Clean dist folder
npm run clean

# Copy fonts to dist
npm run build:copy
```

### Source Structure

```
src/
├── fonts/                  ← Icon font files
└── styles/
    ├── foundation/         ← Base styles (animations, fonts, globals, etc.)
    │   ├── utilities/      ← Utility classes
    │   ├── animations.scss
    │   ├── fonts.scss
    │   ├── globals.scss
    │   ├── icons.scss
    │   ├── index.scss      ← Entry point for default bundle
    │   ├── typography.scss
    │   └── utilities.scss
    └── primeng/            ← PrimeNG theme
        ├── abstracts/      ← Variables, mixins, fonts
        ├── designer/       ← PrimeNG component styles
        ├── polly/          ← Polly-specific theme customizations
        ├── primeng-full.scss  ← Entry point for PrimeNG bundle
        └── index.scss
```

---

## 📊 When to Use Which?

| Use Case | Import |
|----------|--------|
| React app | `@polly-fe/design-foundations` |
| Vue app | `@polly-fe/design-foundations` |
| Svelte app | `@polly-fe/design-foundations` |
| Plain HTML/CSS | `@polly-fe/design-foundations` |
| Angular app WITHOUT PrimeNG | `@polly-fe/design-foundations` |
| **Angular app WITH PrimeNG** | `@polly-fe/design-foundations/primeng` |

---

## 🎨 What's Included

### Foundation Styles (Both Bundles)

- **Fonts**: Icon font family (`iconset`) for custom icons
- **Globals**: CSS reset, base HTML element styles
- **Icons**: Icon utility classes
- **Typography**: Font families, sizes, weights, line heights
- **Animations**: Transition and animation utilities
- **Utilities**: Layout, spacing, display, flexbox, borders, etc.

### PrimeNG Theme (PrimeNG Bundle Only)

- **Design Tokens**: SCSS variables for colors, spacing, typography
- **Component Styles**: Pre-styled PrimeNG components
  - Forms (inputs, checkboxes, radio buttons, dropdowns)
  - Overlays (modals, dialogs, tooltips)
  - Panels (accordion, fieldset, tabs)
  - Data (tables, lists, trees)
  - Messages (toast, inline messages)
- **Custom Mixins**: Typography mixins (display, headline, title, body, label, tag, CLI)

---

## 🔄 Migrating from CSS to SCSS

If you need to customize the styles, note that:

- **Foundation styles** are pure CSS (can be used as-is or renamed to `.scss`)
- **PrimeNG theme** uses SCSS features (variables, mixins, imports)

To customize, fork the repository and modify the source files in `src/styles/`.

---

## 🐛 Troubleshooting

### Issue: Styles not loading

**Solution:** Ensure you're importing from the correct path:
- Default: `@polly-fe/design-foundations` or `@polly-fe/design-foundations/styles`
- PrimeNG: `@polly-fe/design-foundations/primeng`

### Issue: Fonts not loading

**Solution:** The fonts are in `dist/fonts/`. Ensure your bundler is configured to handle font files. The CSS references fonts with relative paths that should work automatically.

### Issue: PrimeNG components not styled

**Solution:** Make sure you're importing `/primeng` version, not the default:
```typescript
import '@polly-fe/design-foundations/primeng'; // ✅ Correct for PrimeNG
// NOT import '@polly-fe/design-foundations'; // ❌ This is default only
```

---

## 📝 License

ISC

---

## 🤝 Contributing

This is an internal Polly FE package. For issues or feature requests, please contact the Polly frontend team.

---

## 📦 Publishing

```bash
# Patch version (bug fixes)
npm run version:patch

# Minor version (new features)
npm run version:minor

# Major version (breaking changes)
npm run version:major
```

The package is published to npm under the `@polly-fe` scope with public access.