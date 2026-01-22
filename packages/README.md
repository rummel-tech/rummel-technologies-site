# Rummel Technologies Design System Packages

This directory contains the Rummel Technologies design system - a centralized source of truth for UI design across all platforms and applications.

## Packages

### 1. `design-tokens/`

Platform-agnostic design tokens following the W3C Design Tokens Community Group specification.

**File**: `design-tokens.json` (15KB)

Contains:
- Colors (brand, semantic, neutral, surface)
- Typography (fonts, sizes, weights, line heights, letter spacing)
- Spacing (4px baseline grid)
- Border radius
- Shadows
- Breakpoints
- Animation (durations and easings)

These tokens are the single source of truth and can be transformed into any platform-specific format:
- Flutter (Dart)
- Web (CSS, SCSS, Tailwind)
- iOS (Swift)
- Android (XML)

### 2. `web-theme/`

Web-specific implementations of the design system.

**Includes**:
- **CSS Custom Properties** (`css/variables.css`) - Runtime theming
- **SCSS** (`scss/`) - Variables, mixins, and utilities
- **Tailwind Configuration** (`tailwind.config.js`) - Extended Tailwind with Rummel tokens

See [web-theme/README.md](web-theme/README.md) for complete documentation.

## Usage

### In This Repository (Website)

The website automatically uses the design system:

```html
<!-- HTML -->
<link rel="stylesheet" href="/packages/web-theme/css/variables.css">
```

```javascript
// Tailwind config
module.exports = require('./packages/web-theme/tailwind.config.js');
```

### In Flutter Applications

Reference from your Flutter app's `pubspec.yaml`:

```yaml
dependencies:
  rummel_blue_theme:
    path: ../../rummel-technologies-site/packages/flutter/rummel_blue_theme
```

The Flutter theme package is maintained separately but references these design tokens.

### In Other Web Projects

#### Option 1: Copy Files
Copy the needed files to your project:
```bash
cp -r rummel-technologies-site/packages/web-theme/css/ my-project/src/styles/
```

#### Option 2: Git Submodule
Add as a submodule:
```bash
git submodule add https://github.com/rummel-technologies/rummel-technologies-site.git design-system
```

#### Option 3: npm Package (Future)
Once published to npm:
```bash
npm install @rummel/web-theme
```

## Design System Structure

```
packages/
├── design-tokens/
│   └── design-tokens.json          # Source of truth (W3C standard)
│
└── web-theme/
    ├── css/
    │   └── variables.css           # CSS custom properties
    ├── scss/
    │   ├── _variables.scss         # SCSS variables
    │   ├── _mixins.scss            # Reusable mixins
    │   └── rummel-theme.scss       # Main SCSS entry
    ├── tailwind.config.js          # Tailwind configuration
    ├── package.json
    └── README.md
```

## Design Tokens Schema

The `design-tokens.json` follows this structure:

```json
{
  "rummel-technologies": {
    "color": {
      "brand": { "primary": { "$type": "color", "$value": "#1E88E5" } },
      "semantic": { "success": { "$type": "color", "$value": "#388E3C" } },
      "neutral": { "white": { "$type": "color", "$value": "#FFFFFF" } }
    },
    "typography": {
      "font-family": { "primary": { "$type": "fontFamily", "$value": [...] } },
      "font-size": { "base": { "$type": "dimension", "$value": "1rem" } }
    },
    "spacing": {
      "4": { "$type": "dimension", "$value": "1rem" }
    },
    "border-radius": {
      "base": { "$type": "dimension", "$value": "0.5rem" }
    },
    "shadow": {
      "base": { "$type": "shadow", "$value": {...} }
    },
    "breakpoints": {
      "tablet": { "$type": "dimension", "$value": "768px" }
    },
    "animation": {
      "duration": { "normal": { "$type": "duration", "$value": "300ms" } }
    }
  }
}
```

## Transforming Tokens

To generate platform-specific files from design tokens:

### Manual Method
1. Update `design-tokens.json`
2. Manually update platform files (CSS, SCSS, Flutter, etc.)
3. Ensure consistency across platforms

### Automated Method (Future)
Use token transformation tools like [Style Dictionary](https://amzn.github.io/style-dictionary/):

```bash
npm run build:tokens
```

This will automatically generate:
- `css/variables.css`
- `scss/_variables.scss`
- Flutter color constants
- iOS color assets
- Android color resources

## Validation

To validate design system consistency:

```bash
npm run validate:tokens      # Validate JSON structure
npm run validate:css         # Validate CSS syntax
npm run validate:scss        # Compile SCSS
npm run validate:consistency # Check cross-platform consistency
```

Or run all validations:
```bash
npm run validate
```

## Contributing

### Adding New Tokens

1. Add to `design-tokens.json`:
```json
{
  "rummel-technologies": {
    "color": {
      "brand": {
        "tertiary": {
          "$type": "color",
          "$value": "#FF5722",
          "$description": "Tertiary accent color"
        }
      }
    }
  }
}
```

2. Update platform files:
   - Add to `css/variables.css`: `--rt-color-tertiary: #FF5722;`
   - Add to `scss/_variables.scss`: `$rt-color-tertiary: #FF5722;`
   - Add to `tailwind.config.js`: `'rummel-tertiary': '#FF5722'`
   - Add to Flutter `colors.dart`: `static const Color tertiary = Color(0xFFFF5722);`

3. Update documentation in `/docs/`

4. Run validation

5. Submit pull request

### Deprecating Tokens

1. Mark as deprecated in `design-tokens.json`:
```json
{
  "old-color": {
    "$type": "color",
    "$value": "#000000",
    "$deprecated": true,
    "$description": "Deprecated: Use neutral.black instead"
  }
}
```

2. Update migration guide

3. Provide transition period (minimum 2 releases)

4. Remove in major version update

## Version History

- **1.0.0** (2026-01-22) - Initial release
  - Complete design tokens
  - CSS, SCSS, and Tailwind implementations
  - Flutter theme package
  - Comprehensive documentation

## Support

For design system questions:
1. Check [design system documentation](/docs/)
2. Review [quick reference](/docs/DESIGN_SYSTEM_QUICK_REFERENCE.md)
3. Look at [examples](/examples/)
4. Contact design system team

## License

Copyright © 2026 Rummel Technologies. All rights reserved.
