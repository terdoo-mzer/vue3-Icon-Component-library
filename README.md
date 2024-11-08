# Vue 3 Icon Component Library

This project provides a simple, reusable SVG icon system for Vue 3, consisting of:

1. **IconBase Component**: Defines SVG attributes like `width`, `height`, and `fill`, and allows other attributes to fall through automatically.
2. **Icon Components** (e.g., `HomeIcon.vue`, `SettingsIcon.vue`): Individual icons that slot specific SVG paths into `IconBase`. No props are defined here.
3. **Parent Component**: Imports and uses icons with customizable attributes.

With this structure, any attribute passed in the parent component will override the defaults `width, height and fill` set in `IconBase`.

## Project Structure

- `IconBase.vue`: The root SVG wrapper with attributes and defaults.
- `Icon Components`: Files for each icon, where the path is added. These do not have props or additional configurations.
- `index.js`: Exports all icons for easy import.

## Installation and Setup

1. **Clone the Repository**  
   Clone or copy `IconBase`, the individual icon components, and `index.js` into your Vue project.

2. **Import Icons**  
   In any component where you need icons, import them as follows:

   ```javascript
   import * as Icons from '@/components/icons';
   ```

## Usage Examples

In your **parent component**, you can now use the icons as follows:

```vue
<template>
  <!-- Default icon with IconBase defaults applied -->
  <Icons.HomeIcon />

  <!-- Custom width, height, and color -->
  <Icons.HomeIcon width="30" height="30" fill="#333333" />

  <!-- Another icon with custom attributes -->
  <Icons.SettingsIcon />
</template>
```

### How it Works

When an icon is used in the parent component:

1. **Attributes** like `width`, `height`, and `fill` can be passed to customize each icon. The mentioned attributes are also added to the IconBase.vue as default props. If they are ommited, the default values will apply.
2. **Unspecified attributes** will default to values set in `IconBase`.
3. **Other SVG attributes** (e.g., `stroke`, `aria-label`) will automatically fall through to `<svg>` without requiring additional props in the icon components.

## Adding New Icons

To add a new icon:

1. **Get the SVG Path**  
   Copy the `<path>` from the SVG file (e.g., an SVG gotten from Material Icons or any other SVG library).

2. **Create a New Icon Component**  
   Inside the `icons` directory, create a new file (e.g., `MyNewIcon.vue`) and add the path. There is no need to add the wrapper (svg) tag as that is already set inside `IconBase.vue`. The `path` will be passed as a slot to the base component. 

Example of a new icon component:

```vue
<template>
  <IconBase>
    <!-- Place your SVG path(s) here -->
    <path d="M10 20 ... Z" />
  </IconBase>
</template>

<script setup>
import IconBase from './IconBase.vue';
</script>
```

## IconBase.vue

The `IconBase` component looks like this:

```vue
<template>
  <svg :width="width" :height="height" :fill="fill" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24">
    <slot />
  </svg>
</template>

<script setup>
  const props = defineProps({
    height: {
      type: [String, Number],
      default: 24,
    },
    width: {
      type: [String, Number],
      default: 24,
    },
    fill: {
      type: [String, Number],
      default: "#4d4d4d",
    },
  });
</script>
```

Here’s how `IconBase` works:

- It defines `width`, `height`, and `fill` as customizable props with default values.
- Any additional attributes passed in the parent component will be automatically applied to the `<svg>`, thanks to Vue’s attribute fallthrough.

## Final Notes

This structure keeps the code clean by centralizing SVG configuration in `IconBase`. Just update `index.js` when adding new icons, and they’ll be available project-wide with customizable attributes.