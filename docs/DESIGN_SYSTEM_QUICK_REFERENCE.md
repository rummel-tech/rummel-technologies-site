# Rummel Technologies Design System - Quick Reference

A cheat sheet for using the Rummel Technologies design system.

## Colors

### Brand Colors

| Color | Hex | Flutter | CSS Variable | Tailwind |
|-------|-----|---------|--------------|----------|
| Primary | `#1E88E5` | `RummelBrandColors.primary` | `var(--rt-color-primary)` | `bg-rummel-primary` |
| Primary Light | `#42A5F5` | `RummelBrandColors.primaryLight` | `var(--rt-color-primary-light)` | `bg-rummel-primary-light` |
| Primary Dark | `#1565C0` | `RummelBrandColors.primaryDark` | `var(--rt-color-primary-dark)` | `bg-rummel-primary-dark` |
| Secondary | `#26A69A` | `RummelBrandColors.secondary` | `var(--rt-color-secondary)` | `bg-rummel-secondary` |
| Secondary Light | `#4DB6AC` | `RummelBrandColors.secondaryLight` | `var(--rt-color-secondary-light)` | `bg-rummel-secondary-light` |

### Semantic Colors

| Purpose | Hex | Flutter | CSS Variable | Tailwind |
|---------|-----|---------|--------------|----------|
| Success | `#388E3C` | `RummelSemanticColors.success` | `var(--rt-color-success)` | `text-rummel-success` |
| Warning | `#F57C00` | `RummelSemanticColors.warning` | `var(--rt-color-warning)` | `text-rummel-warning` |
| Error | `#D32F2F` | `RummelSemanticColors.error` | `var(--rt-color-error)` | `text-rummel-error` |
| Info | `#0288D1` | `RummelSemanticColors.info` | `var(--rt-color-info)` | `text-rummel-info` |

### Neutral Colors

| Color | Hex | Flutter | CSS Variable |
|-------|-----|---------|--------------|
| White | `#FFFFFF` | `RummelNeutralColors.white` | `var(--rt-color-white)` |
| Gray 50 | `#FAFAFA` | `RummelNeutralColors.gray50` | `var(--rt-color-gray-50)` |
| Gray 100 | `#F5F5F5` | `RummelNeutralColors.gray100` | `var(--rt-color-gray-100)` |
| Gray 200 | `#EEEEEE` | `RummelNeutralColors.gray200` | `var(--rt-color-gray-200)` |
| Gray 300 | `#E0E0E0` | `RummelNeutralColors.gray300` | `var(--rt-color-gray-300)` |
| Gray 500 | `#9E9E9E` | `RummelNeutralColors.gray500` | `var(--rt-color-gray-500)` |
| Gray 700 | `#616161` | `RummelNeutralColors.gray700` | `var(--rt-color-gray-700)` |
| Gray 900 | `#212121` | `RummelNeutralColors.gray900` | `var(--rt-color-gray-900)` |
| Black | `#000000` | `RummelNeutralColors.black` | `var(--rt-color-black)` |

## Typography

### Font Families

| Type | Value | Flutter | CSS Variable |
|------|-------|---------|--------------|
| Primary | Inter (with fallbacks) | `RummelTypography.primaryFontFamily` | `var(--rt-font-family-primary)` |
| Monospace | JetBrains Mono | `RummelTypography.monospaceFontFamily` | `var(--rt-font-family-monospace)` |

### Font Sizes

| Name | Size | Flutter TextTheme | CSS Variable |
|------|------|-------------------|--------------|
| xs | 12px | - | `var(--rt-font-size-xs)` |
| sm | 14px | `bodySmall` / `labelMedium` | `var(--rt-font-size-sm)` |
| base | 16px | `bodyMedium` | `var(--rt-font-size-base)` |
| lg | 18px | - | `var(--rt-font-size-lg)` |
| xl | 20px | - | `var(--rt-font-size-xl)` |
| 2xl | 24px | `headlineSmall` | `var(--rt-font-size-2xl)` |
| 3xl | 30px | - | `var(--rt-font-size-3xl)` |
| 4xl | 36px | `displaySmall` | `var(--rt-font-size-4xl)` |
| 5xl | 48px | - | `var(--rt-font-size-5xl)` |
| 6xl | 60px | - | `var(--rt-font-size-6xl)` |

### Font Weights

| Name | Value | Flutter | CSS Variable |
|------|-------|---------|--------------|
| Light | 300 | `RummelTypography.light` | `var(--rt-font-weight-light)` |
| Regular | 400 | `RummelTypography.regular` | `var(--rt-font-weight-regular)` |
| Medium | 500 | `RummelTypography.medium` | `var(--rt-font-weight-medium)` |
| Semibold | 600 | `RummelTypography.semibold` | `var(--rt-font-weight-semibold)` |
| Bold | 700 | `RummelTypography.bold` | `var(--rt-font-weight-bold)` |

## Spacing

Based on 4px baseline grid:

| Name | Pixels | Rem | Flutter | CSS Variable | SCSS |
|------|--------|-----|---------|--------------|------|
| 0 | 0px | 0 | `RummelSpacing.space0` | `var(--rt-spacing-0)` | `$rt-spacing-0` |
| 1 | 4px | 0.25rem | `RummelSpacing.space1` | `var(--rt-spacing-1)` | `$rt-spacing-1` |
| 2 | 8px | 0.5rem | `RummelSpacing.space2` | `var(--rt-spacing-2)` | `$rt-spacing-2` |
| 3 | 12px | 0.75rem | `RummelSpacing.space3` | `var(--rt-spacing-3)` | `$rt-spacing-3` |
| 4 | 16px | 1rem | `RummelSpacing.space4` | `var(--rt-spacing-4)` | `$rt-spacing-4` |
| 5 | 20px | 1.25rem | `RummelSpacing.space5` | `var(--rt-spacing-5)` | `$rt-spacing-5` |
| 6 | 24px | 1.5rem | `RummelSpacing.space6` | `var(--rt-spacing-6)` | `$rt-spacing-6` |
| 8 | 32px | 2rem | `RummelSpacing.space8` | `var(--rt-spacing-8)` | `$rt-spacing-8` |
| 10 | 40px | 2.5rem | `RummelSpacing.space10` | `var(--rt-spacing-10)` | `$rt-spacing-10` |
| 12 | 48px | 3rem | `RummelSpacing.space12` | `var(--rt-spacing-12)` | `$rt-spacing-12` |
| 16 | 64px | 4rem | `RummelSpacing.space16` | `var(--rt-spacing-16)` | `$rt-spacing-16` |
| 20 | 80px | 5rem | `RummelSpacing.space20` | `var(--rt-spacing-20)` | `$rt-spacing-20` |
| 24 | 96px | 6rem | `RummelSpacing.space24` | `var(--rt-spacing-24)` | `$rt-spacing-24` |

## Border Radius

| Name | Pixels | Flutter | CSS Variable | SCSS |
|------|--------|---------|--------------|------|
| none | 0px | `RummelBorderRadius.none` | `var(--rt-radius-none)` | `$rt-radius-none` |
| sm | 4px | `RummelBorderRadius.sm` | `var(--rt-radius-sm)` | `$rt-radius-sm` |
| base | 8px | `RummelBorderRadius.base` | `var(--rt-radius-base)` | `$rt-radius-base` |
| md | 12px | `RummelBorderRadius.md` | `var(--rt-radius-md)` | `$rt-radius-md` |
| lg | 16px | `RummelBorderRadius.lg` | `var(--rt-radius-lg)` | `$rt-radius-lg` |
| xl | 24px | `RummelBorderRadius.xl` | `var(--rt-radius-xl)` | `$rt-radius-xl` |
| full | 9999px | `RummelBorderRadius.full` | `var(--rt-radius-full)` | `$rt-radius-full` |

## Shadows

| Name | Flutter | CSS Variable | SCSS |
|------|---------|--------------|------|
| sm | `RummelElevation.level1` | `var(--rt-shadow-sm)` | `$rt-shadow-sm` |
| base | `RummelElevation.level2` | `var(--rt-shadow-base)` | `$rt-shadow-base` |
| md | `RummelElevation.level3` | `var(--rt-shadow-md)` | `$rt-shadow-md` |
| lg | `RummelElevation.level4` | `var(--rt-shadow-lg)` | `$rt-shadow-lg` |
| xl | `RummelElevation.level5` | `var(--rt-shadow-xl)` | `$rt-shadow-xl` |

## Breakpoints

| Name | Pixels | SCSS Mixin | CSS Variable | Tailwind |
|------|--------|------------|--------------|----------|
| mobile | 640px | `@include breakpoint(mobile)` | `var(--rt-breakpoint-mobile)` | `rummel-mobile:` |
| tablet | 768px | `@include breakpoint(tablet)` | `var(--rt-breakpoint-tablet)` | `rummel-tablet:` |
| desktop | 1024px | `@include breakpoint(desktop)` | `var(--rt-breakpoint-desktop)` | `rummel-desktop:` |
| wide | 1280px | `@include breakpoint(wide)` | `var(--rt-breakpoint-wide)` | `rummel-wide:` |
| ultrawide | 1536px | `@include breakpoint(ultrawide)` | `var(--rt-breakpoint-ultrawide)` | `rummel-ultrawide:` |

## Animation

### Durations

| Name | Value | Flutter | CSS Variable |
|------|-------|---------|--------------|
| fast | 150ms | `RummelDuration.fast` | `var(--rt-duration-fast)` |
| normal | 300ms | `RummelDuration.normal` | `var(--rt-duration-normal)` |
| slow | 500ms | `RummelDuration.slow` | `var(--rt-duration-slow)` |

### Easings

| Name | Value | CSS Variable |
|------|-------|--------------|
| ease-in | cubic-bezier(0.4, 0, 1, 1) | `var(--rt-easing-ease-in)` |
| ease-out | cubic-bezier(0, 0, 0.2, 1) | `var(--rt-easing-ease-out)` |
| ease-in-out | cubic-bezier(0.4, 0, 0.2, 1) | `var(--rt-easing-ease-in-out)` |

## Common Patterns

### Flutter

```dart
// Button with theme colors
ElevatedButton(
  onPressed: () {},
  child: const Text('Button'),
);

// Card
Card(
  child: Padding(
    padding: const EdgeInsets.all(RummelSpacing.space4),
    child: Text('Card content'),
  ),
);

// Spacing between widgets
Column(
  children: [
    Text('Item 1'),
    SizedBox(height: RummelSpacing.space2),
    Text('Item 2'),
  ],
);

// Theme-aware colors
Container(
  color: Theme.of(context).colorScheme.surface,
  child: Text(
    'Text',
    style: TextStyle(
      color: Theme.of(context).colorScheme.onSurface,
    ),
  ),
);
```

### CSS

```css
/* Button */
.button {
  background-color: var(--rt-color-primary);
  color: var(--rt-color-white);
  padding: var(--rt-spacing-3) var(--rt-spacing-6);
  border-radius: var(--rt-radius-base);
  font-size: var(--rt-font-size-base);
  transition: background-color var(--rt-duration-normal) var(--rt-easing-ease-in-out);
}

/* Card */
.card {
  background-color: var(--rt-color-surface);
  border-radius: var(--rt-radius-base);
  padding: var(--rt-spacing-4);
  box-shadow: var(--rt-shadow-base);
}

/* Responsive spacing */
.container {
  padding: var(--rt-spacing-4);
}

@media (min-width: 768px) {
  .container {
    padding: var(--rt-spacing-8);
  }
}
```

### SCSS

```scss
// Button
.button {
  @include button-primary;
}

// Card
.card {
  @include card;
}

// Responsive
.container {
  padding: $rt-spacing-4;

  @include breakpoint(tablet) {
    padding: $rt-spacing-8;
  }
}

// Typography
h1 {
  @include text-headline-large;
}
```

### Tailwind

```html
<!-- Button -->
<button class="bg-rummel-primary text-white p-rummel-4 rounded-rummel-base">
  Button
</button>

<!-- Card -->
<div class="bg-rummel-surface p-rummel-4 rounded-rummel-base shadow-rummel-base">
  Card content
</div>

<!-- Responsive -->
<div class="p-rummel-4 rummel-tablet:p-rummel-8 rummel-desktop:p-rummel-12">
  Responsive content
</div>
```

## Dark Mode

### Flutter
```dart
// Automatically handled by ThemeData.dark()
MaterialApp(
  theme: RummelThemeData.light(),
  darkTheme: RummelThemeData.dark(),
  themeMode: ThemeMode.system, // Follows system preference
);
```

### Web
```javascript
// Set dark mode
document.documentElement.setAttribute('data-theme', 'dark');

// Set light mode
document.documentElement.setAttribute('data-theme', 'light');

// Follow system preference
const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
document.documentElement.setAttribute('data-theme', prefersDark ? 'dark' : 'light');
```

---

**Version**: 1.0.0
**Last Updated**: 2026-01-22
**Full Documentation**: See `DESIGN_SYSTEM_GUIDE.md`
