# Rummel Technologies - Official Website & Design System

This repository contains the official Rummel Technologies website and the centralized design system used across all Rummel Technologies applications.

## Repository Structure

```
rummel-technologies-site/
├── packages/
│   ├── design-tokens/          # Platform-agnostic design tokens (W3C standard)
│   └── web-theme/              # Web theme (CSS, SCSS, Tailwind)
├── website/                     # Official Rummel Technologies website
│   ├── public/                 # Static assets
│   └── src/                    # Website source code
├── docs/                        # Design system documentation
└── examples/                    # Usage examples
```

## What's Inside

### 1. Design System (`/packages/`)

The Rummel Technologies design system is the single source of truth for UI design across all platforms:

- **`design-tokens/`** - Platform-agnostic design values (colors, typography, spacing, etc.)
  - Used by Flutter apps, web applications, and future platforms
  - Follows W3C Design Tokens Community Group specification

- **`web-theme/`** - Web-specific theme implementations
  - CSS Custom Properties (`css/variables.css`)
  - SCSS variables and mixins (`scss/`)
  - Tailwind CSS configuration (`tailwind.config.js`)

### 2. Website (`/website/`)

The official Rummel Technologies organization website showcasing:
- Company information
- Products and services
- Design system documentation
- Developer resources

### 3. Documentation (`/docs/`)

Comprehensive design system documentation:
- **DESIGN_SYSTEM_GUIDE.md** - Complete implementation guide
- **DESIGN_SYSTEM_QUICK_REFERENCE.md** - Developer cheat sheet
- **DESIGN_SYSTEM_SUMMARY.md** - Executive overview

### 4. Examples (`/examples/`)

Example implementations showing how to use the design system in various contexts.

## Quick Start

### For Website Development

```bash
cd website
npm install
npm run dev
```

### For Design System Usage

#### Web Projects

**Option 1: CSS Custom Properties**
```html
<link rel="stylesheet" href="path/to/packages/web-theme/css/variables.css">
```

**Option 2: SCSS**
```scss
@import '~@rummel/web-theme/scss/rummel-theme';
```

**Option 3: Tailwind**
```javascript
// tailwind.config.js
const rummelConfig = require('./packages/web-theme/tailwind.config.js');
module.exports = { ...rummelConfig };
```

#### Flutter Projects

Update your `pubspec.yaml`:
```yaml
dependencies:
  rummel_blue_theme:
    path: ../../rummel-technologies-site/packages/flutter/rummel_blue_theme
```

**Note**: The Flutter theme package references design tokens from this repository.

## Applications Using This Design System

- **Artemis App** - Main application
- **Home Manager App** - Home automation management
- **Vehicle Manager App** - Vehicle tracking and management
- **Meal Planner App** - Meal planning and recipes
- **Rummel Technologies Website** - This website

## Design System Highlights

### Colors
- **Primary**: `#1E88E5` (Rummel Blue)
- **Secondary**: `#26A69A` (Teal)
- **Semantic**: Success, Warning, Error, Info

### Typography
- **Primary Font**: Inter (with system fallbacks)
- **Monospace**: JetBrains Mono
- **Scale**: 12px to 60px

### Spacing
- **Base Unit**: 16px (1rem)
- **Scale**: 4px baseline grid (4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96)

### Features
- ✅ Light and dark mode support
- ✅ Responsive breakpoints (mobile to ultrawide)
- ✅ Accessible color contrasts (WCAG 2.1 AA)
- ✅ Cross-platform consistency
- ✅ Comprehensive component theming

## Documentation

- **[Complete Guide](docs/DESIGN_SYSTEM_GUIDE.md)** - Implementation instructions
- **[Quick Reference](docs/DESIGN_SYSTEM_QUICK_REFERENCE.md)** - Cheat sheet for developers
- **[Summary](docs/DESIGN_SYSTEM_SUMMARY.md)** - Executive overview
- **[Web Theme README](packages/web-theme/README.md)** - Web-specific documentation

## Development

### Prerequisites
- Node.js 20+
- npm or yarn

### Setup
```bash
git clone https://github.com/rummel-technologies/rummel-technologies-site.git
cd rummel-technologies-site
npm install
```

### Commands
```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run preview      # Preview production build
npm run lint         # Lint code
npm run format       # Format code
npm run validate     # Validate design system
```

## Contributing

### Making Design System Changes

1. **Update design tokens** in `packages/design-tokens/design-tokens.json`
2. **Regenerate platform files** (CSS, SCSS, Tailwind, Flutter)
3. **Update documentation** if adding new tokens
4. **Run validation** to ensure consistency
5. **Test across platforms** (web and Flutter apps)
6. **Submit pull request** with examples

### Making Website Changes

1. **Make changes** in `website/src/`
2. **Test locally** with `npm run dev`
3. **Build** with `npm run build`
4. **Submit pull request**

## Deployment

The website is automatically deployed when changes are pushed to `main`:
- **Production**: https://rummel.tech (configured in CI/CD)
- **Preview**: Automatic preview deploys for pull requests

## License

Copyright © 2026 Rummel Technologies. All rights reserved.

## Support

For questions or issues:
- **Design System**: Review documentation in `/docs/`
- **Website**: Create an issue in this repository
- **General**: Contact development team

## Version

- **Design System**: 1.0.0
- **Website**: 1.0.0
- **Last Updated**: 2026-01-22
