# Rummel Technologies Web Theme

A centralized design system for all Rummel Technologies web applications. This package provides CSS variables, SCSS utilities, and Tailwind configuration based on the Rummel Technologies design tokens.

## Features

- **CSS Custom Properties** for runtime theming
- **SCSS variables and mixins** for advanced styling
- **Tailwind CSS configuration** for utility-first development
- **Light and dark mode** support
- **Consistent with Flutter theme** - same design tokens
- **W3C Design Tokens** standard compliant

## Installation

### For Plain HTML/CSS Projects

1. Copy the CSS file to your project:
   ```bash
   cp packages/web-theme/css/variables.css public/css/
   ```

2. Link it in your HTML:
   ```html
   <link rel="stylesheet" href="/css/variables.css">
   ```

### For SCSS Projects

Add to your main SCSS file:
```scss
@import '~@rummel/web-theme/scss/rummel-theme';
```

Or import just what you need:
```scss
@import '~@rummel/web-theme/scss/variables';
@import '~@rummel/web-theme/scss/mixins';
```

### For Tailwind CSS Projects

In your `tailwind.config.js`:
```javascript
const rummelConfig = require('@rummel/web-theme/tailwind.config.js');

module.exports = {
  ...rummelConfig,
  content: [
    './src/**/*.{js,jsx,ts,tsx,html}',
  ],
};
```

## Usage

### CSS Custom Properties

Use CSS variables directly in your styles:

```css
.button {
  background-color: var(--rt-color-primary);
  color: var(--rt-color-white);
  padding: var(--rt-spacing-3) var(--rt-spacing-6);
  border-radius: var(--rt-radius-base);
  font-family: var(--rt-font-family-primary);
  font-size: var(--rt-font-size-base);
  transition: background-color var(--rt-duration-normal) var(--rt-easing-ease-in-out);
}

.button:hover {
  background-color: var(--rt-color-primary-dark);
}

.card {
  background-color: var(--rt-color-surface);
  border: 1px solid var(--rt-color-border);
  border-radius: var(--rt-radius-base);
  padding: var(--rt-spacing-4);
  box-shadow: var(--rt-shadow-base);
}
```

### Dark Mode

Set the `data-theme` attribute on your root element:

```html
<!-- Light mode (default) -->
<html>

<!-- Dark mode -->
<html data-theme="dark">
```

Or use JavaScript to toggle:
```javascript
// Set theme
document.documentElement.setAttribute('data-theme', 'dark');

// Toggle theme
const currentTheme = document.documentElement.getAttribute('data-theme');
const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
document.documentElement.setAttribute('data-theme', newTheme);

// Respect system preference
const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
if (prefersDark) {
  document.documentElement.setAttribute('data-theme', 'dark');
}
```

### SCSS Mixins

Use predefined mixins for common patterns:

```scss
@import '~@rummel/web-theme/scss/rummel-theme';

.my-button {
  @include button-primary;
}

.my-card {
  @include card;
}

.my-heading {
  @include text-headline-large;
}

.my-input {
  @include input-field;
}

// Responsive design
.my-container {
  padding: $rt-spacing-4;

  @include breakpoint(tablet) {
    padding: $rt-spacing-8;
  }

  @include breakpoint(desktop) {
    padding: $rt-spacing-12;
  }
}

// Flex utilities
.my-header {
  @include flex-between;
  padding: $rt-spacing-4;
}

// Dark theme specific styles
.my-component {
  background: $rt-color-surface-light;

  @include dark-theme {
    background: $rt-color-surface-dark;
  }
}
```

### Tailwind CSS

Use Rummel prefixed utilities:

```html
<!-- Brand colors -->
<button class="bg-rummel-primary text-white hover:bg-rummel-primary-dark">
  Primary Button
</button>

<div class="bg-rummel-secondary text-white">
  Secondary Background
</div>

<!-- Semantic colors -->
<div class="text-rummel-success">Success message</div>
<div class="text-rummel-error">Error message</div>
<div class="border-rummel-warning">Warning border</div>

<!-- Spacing -->
<div class="p-rummel-4 m-rummel-2">
  Content with Rummel spacing
</div>

<!-- Border radius -->
<div class="rounded-rummel-base">Rounded corners</div>
<div class="rounded-rummel-lg">More rounded</div>

<!-- Shadows -->
<div class="shadow-rummel-base">Card with shadow</div>

<!-- Typography -->
<h1 class="font-rummel-sans text-rummel-4xl font-rummel-bold">
  Heading
</h1>

<p class="font-rummel-sans text-rummel-base">
  Body text
</p>

<code class="font-rummel-mono text-rummel-sm">
  Code block
</code>

<!-- Responsive -->
<div class="p-rummel-4 rummel-tablet:p-rummel-8 rummel-desktop:p-rummel-12">
  Responsive padding
</div>
```

## Color Palette

### Brand Colors
- Primary: `#1E88E5` (Rummel Blue)
  - Light: `#42A5F5`
  - Dark: `#1565C0`
  - Darker: `#0D47A1`
- Secondary: `#26A69A` (Teal)
  - Light: `#4DB6AC`

### Semantic Colors
- Success: `#388E3C` (Green)
- Warning: `#F57C00` (Orange)
- Error: `#D32F2F` (Red)
- Info: `#0288D1` (Blue)

### Neutral Colors
- Gray scale: `gray-50` through `gray-900`
- White: `#FFFFFF`
- Black: `#000000`

## Typography

### Font Families
- **Primary**: Inter (with system fallbacks)
- **Monospace**: JetBrains Mono (with fallbacks)

### Font Sizes
- xs: 12px
- sm: 14px
- base: 16px (default)
- lg: 18px
- xl: 20px
- 2xl: 24px
- 3xl: 30px
- 4xl: 36px
- 5xl: 48px
- 6xl: 60px

## Spacing Scale

Based on 4px baseline grid:
- 0: 0px
- 1: 4px
- 2: 8px
- 3: 12px
- 4: 16px (base unit)
- 5: 20px
- 6: 24px
- 8: 32px
- 10: 40px
- 12: 48px
- 16: 64px
- 20: 80px
- 24: 96px

## Breakpoints

- mobile: 640px
- tablet: 768px
- desktop: 1024px
- wide: 1280px
- ultrawide: 1536px

## Available Utility Classes

When using the full SCSS import (`rummel-theme.scss`):

### Layout
- `.rt-container` - Responsive container
- `.rt-flex-center` - Centered flex container
- `.rt-flex-between` - Space-between flex container
- `.rt-flex-column` - Column flex container

### Buttons
- `.rt-btn` - Base button
- `.rt-btn-primary` - Primary button
- `.rt-btn-secondary` - Secondary button
- `.rt-btn-outlined` - Outlined button
- `.rt-btn-text` - Text button

### Components
- `.rt-card` - Card component
- `.rt-input` - Input field

### Text
- `.rt-truncate` - Truncate text with ellipsis
- `.rt-visually-hidden` - Screen reader only

### Spacing
- `.rt-m-{0-24}` - Margin
- `.rt-p-{0-24}` - Padding
- `.rt-mt-{0-24}`, `.rt-mr-{0-24}`, etc. - Directional spacing

### Colors
- `.rt-text-{primary|secondary|success|warning|error|info}` - Text colors
- `.rt-bg-{primary|secondary|success|warning|error|info}` - Background colors

## Design Tokens

This package is generated from the platform-agnostic design tokens at:
```
/packages/design-system/design-tokens.json
```

The tokens follow the W3C Design Tokens Community Group specification and can be transformed for any platform.

## Consistency with Flutter

This web theme uses the exact same design tokens as the Flutter theme package (`rummel_blue_theme`), ensuring visual consistency across all Rummel Technologies applications:

- Mobile apps (Flutter)
- Web applications (this package)
- Potential future platforms (iOS, Android native)

## Examples

### Complete HTML Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Rummel Technologies</title>
  <link rel="stylesheet" href="/css/variables.css">
  <style>
    .hero {
      background-color: var(--rt-color-primary);
      color: var(--rt-color-white);
      padding: var(--rt-spacing-12);
      text-align: center;
    }

    .card {
      background-color: var(--rt-color-surface);
      border-radius: var(--rt-radius-base);
      padding: var(--rt-spacing-4);
      box-shadow: var(--rt-shadow-base);
      margin-bottom: var(--rt-spacing-4);
    }

    .button {
      background-color: var(--rt-color-primary);
      color: var(--rt-color-white);
      padding: var(--rt-spacing-3) var(--rt-spacing-6);
      border: none;
      border-radius: var(--rt-radius-base);
      font-family: var(--rt-font-family-primary);
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="hero">
    <h1>Welcome to Rummel Technologies</h1>
    <p>Building the future together</p>
  </div>

  <div class="container">
    <div class="card">
      <h2>Feature One</h2>
      <p>Description of feature one</p>
      <button class="button">Learn More</button>
    </div>
  </div>
</body>
</html>
```

## Contributing

When making changes:

1. Update design tokens: `/packages/design-system/design-tokens.json`
2. Regenerate CSS/SCSS files
3. Test in both light and dark modes
4. Verify across different browsers
5. Update this README

## License

Copyright © 2026 Rummel Technologies. All rights reserved.
