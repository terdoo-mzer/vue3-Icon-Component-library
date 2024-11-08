# Vue 3 Icon Component Library

This project provides a simple, reusable SVG icon system for Vue 3. Each icon is customizable with properties like `width`, `height`, and `fill` color. Other SVG attributes automatically pass through to the `<svg>` root, making customization easy without declaring extra props.

## Project Structure

The icon library consists of three main parts:

1. **Icon Components** (e.g., `HomeIcon.vue`, `SettingsIcon.vue`):  
   Individual icon files that use `IconBase` to wrap SVG paths. Add new icons here by creating files for each new icon and slotted paths into `IconBase`.

2. **IconBase Component**:  
   A wrapper for all SVG icons, handling attributes like `width`, `height`, and `fill`. Any additional attributes fall through automatically to `<svg>`, allowing custom attributes without needing props.

3. **index.js**:  
   Exports all icons in the `/icons` directory so they can be easily imported as a group in other components.

## Installation and Setup

1. **Clone the Repository**  
   Clone the repository or copy `Icon`, `IconBase`, and `index.js` files into your Vue project.

2. **Import Icons in Your Components**  
   Use `import * as Icons from '@/components/icons'` to import all icons at once.

## Usage Examples

Icons are fully customizable in terms of size and color. Here’s how to use them:

```vue
<template>
  <!-- Basic usage with default size and color -->
  <Icons.HomeIcon />

  <!-- Custom size and color -->
  <Icons.HomeIcon width="30" height="30" fill="#333333" />

  <!-- Settings icon with different sizes and colors -->
  <Icons.SettingsIcon width="24" height="24" fill="#000" />
</template>
```

Attributes like `width`, `height`, `fill`, and other SVG attributes (e.g., `stroke`, `aria-label`) automatically fall through to the `<svg>` in `IconBase`.

## Adding New Icons

1. **Get the SVG Path**  
   Copy the `<path>` element from your SVG source (e.g., Material Icons or custom SVGs).

2. **Create a New Icon Component**  
   Add the new icon file (e.g., `MyNewIcon.vue`). Import `IconBase` and slot the SVG path inside.

Example of a new icon component:

```vue
<template>
  <IconBase :width="width" :height="height" :fill="fill">
    <!-- Paste your SVG path here -->
    <path d="M10 20 ... Z" />
  </IconBase>
</template>

<script setup>
import IconBase from './IconBase.vue';

const props = defineProps({
  width: { type: [String, Number], default: 24 },
  height: { type: [String, Number], default: 24 },
  fill: { type: String, default: 'currentColor' },
});
</script>
```

## Final Notes

- **Props**: `width`, `height`, and `fill` are the main customizable props passed from each icon component to `IconBase`.
- **Attribute Fallthrough**: Other attributes passed to the icon (e.g., `stroke`, `aria-label`) will apply directly to the `<svg>` without needing explicit props.

This setup keeps the code organized, making it easy to add or update icons in your project. Enjoy!
```
