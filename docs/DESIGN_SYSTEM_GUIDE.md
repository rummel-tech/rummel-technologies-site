# Rummel Technologies Design System Implementation Guide

This guide provides instructions for implementing the Rummel Technologies design system across all applications and services.

## Table of Contents

1. [Overview](#overview)
2. [Design System Structure](#design-system-structure)
3. [Flutter Applications](#flutter-applications)
4. [Web Applications](#web-applications)
5. [Migration Strategy](#migration-strategy)
6. [Best Practices](#best-practices)
7. [Troubleshooting](#troubleshooting)

## Overview

The Rummel Technologies design system is a centralized set of design standards, components, and guidelines that ensure consistency across all products. It consists of:

- **Design Tokens** - Platform-agnostic design values (colors, typography, spacing)
- **Flutter Theme** - Material Design 3 theme for Flutter applications
- **Web Theme** - CSS variables, SCSS, and Tailwind config for web applications

### Benefits

- ✅ **Consistency** - Same look and feel across all platforms
- ✅ **Efficiency** - Faster development with pre-built components
- ✅ **Maintainability** - Single source of truth for design updates
- ✅ **Accessibility** - Built-in support for light/dark modes
- ✅ **Scalability** - Easy to extend and customize

## Design System Structure

```
packages/
├── design-system/
│   └── design-tokens.json          # Platform-agnostic design tokens (W3C standard)
├── flutter/
│   └── rummel_blue_theme/          # Flutter theme package
│       ├── lib/
│       │   ├── rummel_blue_theme.dart
│       │   └── src/
│       │       ├── colors.dart      # Color definitions
│       │       ├── typography.dart  # Text styles
│       │       ├── spacing.dart     # Spacing & sizing
│       │       └── theme_data.dart  # Complete theme config
│       ├── pubspec.yaml
│       └── README.md
└── web-theme/                       # Web theme package
    ├── css/
    │   └── variables.css            # CSS custom properties
    ├── scss/
    │   ├── _variables.scss          # SCSS variables
    │   ├── _mixins.scss             # SCSS mixins
    │   └── rummel-theme.scss        # Main SCSS file
    ├── tailwind.config.js           # Tailwind configuration
    └── README.md
```

## Flutter Applications

### Installation

1. **Add dependency** to your `pubspec.yaml`:

```yaml
dependencies:
  rummel_blue_theme:
    path: ../../packages/flutter/rummel_blue_theme
```

2. **Run** `flutter pub get`

### Basic Setup

Update your main application file:

```dart
import 'package:flutter/material.dart';
import 'package:rummel_blue_theme/rummel_blue_theme.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Your App Name',
      theme: RummelThemeData.light(),
      darkTheme: RummelThemeData.dark(),
      themeMode: ThemeMode.system,
      home: const HomePage(),
    );
  }
}
```

### Using the Theme

#### Colors

```dart
import 'package:rummel_blue_theme/rummel_blue_theme.dart';

// Brand colors
Container(
  color: RummelBrandColors.primary,
  child: Text('Primary', style: TextStyle(color: RummelNeutralColors.white)),
)

// Semantic colors
Icon(Icons.check, color: RummelSemanticColors.success)
Icon(Icons.warning, color: RummelSemanticColors.warning)
Icon(Icons.error, color: RummelSemanticColors.error)

// Theme colors (adapts to light/dark mode)
Container(
  color: Theme.of(context).colorScheme.surface,
  child: Text(
    'Adaptive text',
    style: TextStyle(color: Theme.of(context).colorScheme.onSurface),
  ),
)
```

#### Typography

```dart
// Use theme text styles
Text('Display Large', style: Theme.of(context).textTheme.displayLarge)
Text('Headline Medium', style: Theme.of(context).textTheme.headlineMedium)
Text('Body Large', style: Theme.of(context).textTheme.bodyLarge)

// Monospace for code
Text('const x = 42;', style: RummelTypography.monospace())
```

#### Spacing

```dart
// Use spacing constants
Padding(
  padding: const EdgeInsets.all(RummelSpacing.space4),
  child: Column(
    children: [
      Text('Item 1'),
      SizedBox(height: RummelSpacing.space2),
      Text('Item 2'),
    ],
  ),
)

// Border radius
Container(
  decoration: BoxDecoration(
    color: Colors.blue,
    borderRadius: BorderRadius.circular(RummelBorderRadius.base),
  ),
)
```

### Migration Checklist for Existing Flutter Apps

- [ ] Add `rummel_blue_theme` dependency to `pubspec.yaml`
- [ ] Update `MaterialApp` to use `RummelThemeData.light()` and `RummelThemeData.dark()`
- [ ] Replace hardcoded colors with theme colors
- [ ] Replace hardcoded text styles with theme text styles
- [ ] Replace hardcoded spacing with `RummelSpacing` constants
- [ ] Replace hardcoded border radius with `RummelBorderRadius` constants
- [ ] Test in both light and dark modes
- [ ] Update any custom widgets to use theme values

## Web Applications

### Installation

The web theme can be used in three ways:

#### Option 1: CSS Custom Properties (Recommended for simple sites)

1. Copy `packages/web-theme/css/variables.css` to your project
2. Link it in your HTML:

```html
<link rel="stylesheet" href="/css/variables.css">
```

3. Use CSS variables:

```css
.button {
  background-color: var(--rt-color-primary);
  color: var(--rt-color-white);
  padding: var(--rt-spacing-3) var(--rt-spacing-6);
  border-radius: var(--rt-radius-base);
}
```

#### Option 2: SCSS (Recommended for complex applications)

1. Install the theme package (when published to npm):

```bash
npm install @rummel/web-theme
```

2. Import in your main SCSS file:

```scss
@import '~@rummel/web-theme/scss/rummel-theme';
```

3. Use variables and mixins:

```scss
.my-button {
  @include button-primary;
}

.my-card {
  @include card;
  padding: $rt-spacing-4;
}
```

#### Option 3: Tailwind CSS (Recommended for utility-first development)

1. Install Tailwind and the theme package

2. Import config in `tailwind.config.js`:

```javascript
const rummelConfig = require('@rummel/web-theme/tailwind.config.js');

module.exports = {
  ...rummelConfig,
  content: ['./src/**/*.{html,js,jsx,ts,tsx}'],
};
```

3. Use Rummel utilities:

```html
<button class="bg-rummel-primary text-white p-rummel-4 rounded-rummel-base">
  Primary Button
</button>
```

### Dark Mode Support

Set the theme attribute on the root element:

```javascript
// Set dark mode
document.documentElement.setAttribute('data-theme', 'dark');

// Set light mode
document.documentElement.setAttribute('data-theme', 'light');

// Respect system preference
if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
  document.documentElement.setAttribute('data-theme', 'dark');
}

// Listen for system preference changes
window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', (e) => {
  document.documentElement.setAttribute('data-theme', e.matches ? 'dark' : 'light');
});
```

### Migration Checklist for Existing Web Apps

- [ ] Choose implementation method (CSS/SCSS/Tailwind)
- [ ] Add theme package to project
- [ ] Update build configuration if needed
- [ ] Replace hardcoded colors with theme colors
- [ ] Replace hardcoded spacing with theme spacing
- [ ] Replace hardcoded typography with theme typography
- [ ] Add dark mode support
- [ ] Test responsiveness at all breakpoints
- [ ] Verify accessibility (contrast ratios, focus states)

## Migration Strategy

### Phase 1: Setup (Week 1)

1. **Install theme packages** in all applications
2. **Update build configurations** (pubspec.yaml, package.json)
3. **Test basic integration** - ensure apps still build and run

### Phase 2: Core Components (Weeks 2-3)

1. **Update app theme configuration**
   - Flutter: Update MaterialApp theme
   - Web: Import CSS/SCSS/Tailwind config

2. **Migrate buttons and form elements**
   - Update button styles
   - Update input fields
   - Update checkboxes, radio buttons

3. **Test interactive elements**

### Phase 3: Layout & Typography (Weeks 4-5)

1. **Replace spacing values**
   - Margins and padding
   - Gap between elements

2. **Update typography**
   - Headings
   - Body text
   - Labels

3. **Test layout consistency**

### Phase 4: Colors & Theming (Week 6)

1. **Replace color values**
   - Brand colors
   - Semantic colors (success, warning, error)
   - Neutral colors

2. **Implement dark mode**
   - Flutter: Verify dark theme works
   - Web: Add theme toggle

3. **Test both themes**

### Phase 5: Polish & Testing (Week 7)

1. **Visual consistency check** across all apps
2. **Accessibility audit** (contrast, focus states)
3. **Performance testing**
4. **Documentation updates**

## Best Practices

### Do's ✅

- **Use theme values** instead of hardcoding colors, spacing, etc.
- **Test in both light and dark modes** during development
- **Use semantic colors** (success, warning, error) for status indicators
- **Follow Material Design 3 guidelines** for Flutter apps
- **Use CSS custom properties** for runtime theming in web apps
- **Keep design tokens updated** as the single source of truth

### Don'ts ❌

- **Don't hardcode colors** - always use theme colors
- **Don't use arbitrary spacing** - use the spacing scale
- **Don't create custom color variants** - use the provided palette
- **Don't mix different font families** - stick to the theme fonts
- **Don't skip accessibility testing** - verify contrast and focus states
- **Don't modify theme files directly** - extend through proper channels

### Code Review Checklist

When reviewing code that uses the design system:

- [ ] Are theme colors used instead of hardcoded values?
- [ ] Is spacing from the spacing scale (RummelSpacing or --rt-spacing-*)?
- [ ] Are typography styles from the theme (Theme.of(context).textTheme)?
- [ ] Does it work in both light and dark modes?
- [ ] Are focus states visible for keyboard navigation?
- [ ] Is the code accessible (proper contrast, semantic HTML)?

## Troubleshooting

### Flutter

**Problem**: Theme not applying to widgets

**Solution**: Ensure you're using `Theme.of(context)` to access theme values, not hardcoded colors.

```dart
// ❌ Wrong
Container(color: Colors.blue)

// ✅ Correct
Container(color: Theme.of(context).colorScheme.primary)
```

**Problem**: Colors look wrong in dark mode

**Solution**: Use theme-aware colors from `ColorScheme`:

```dart
// Adapts to light/dark mode automatically
Container(
  color: Theme.of(context).colorScheme.surface,
  child: Text(
    'Text',
    style: TextStyle(color: Theme.of(context).colorScheme.onSurface),
  ),
)
```

### Web

**Problem**: CSS variables not working

**Solution**: Ensure `variables.css` is loaded before your custom styles:

```html
<link rel="stylesheet" href="/css/variables.css">
<link rel="stylesheet" href="/css/app.css">
```

**Problem**: Dark mode not switching

**Solution**: Verify the `data-theme` attribute is set on the root element:

```javascript
document.documentElement.setAttribute('data-theme', 'dark');
```

**Problem**: SCSS compilation errors

**Solution**: Ensure you're importing files in the correct order:

```scss
@import '~@rummel/web-theme/scss/variables';  // First
@import '~@rummel/web-theme/scss/mixins';     // Second
// Your custom styles here
```

### Common Issues

**Problem**: Inconsistent spacing between platforms

**Solution**: Verify you're using the same spacing scale values. The Flutter `RummelSpacing.space4` should equal CSS `var(--rt-spacing-4)` (both 16px).

**Problem**: Font loading issues

**Solution**: Ensure Inter and JetBrains Mono fonts are loaded:

```html
<!-- In your HTML head -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

## Support

For questions or issues:

1. Check this documentation first
2. Review the package READMEs:
   - `/packages/flutter/rummel_blue_theme/README.md`
   - `/packages/web-theme/README.md`
3. Check the design tokens: `/packages/design-system/design-tokens.json`
4. Contact the design system maintainers

## Updates

When the design system is updated:

1. **Pull latest changes** from the repository
2. **Update dependencies** (`flutter pub get` / `npm install`)
3. **Test your application** in both light and dark modes
4. **Review changelogs** for breaking changes
5. **Update custom extensions** if needed

## Contributing

To contribute to the design system:

1. Update design tokens first: `/packages/design-system/design-tokens.json`
2. Regenerate platform-specific files
3. Test changes across all platforms
4. Document new additions
5. Submit pull request with examples

---

**Version**: 1.0.0
**Last Updated**: 2026-01-22
**Maintained by**: Rummel Technologies
