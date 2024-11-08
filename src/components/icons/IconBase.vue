<template>
    <svg
      :width="width"
      :height="height"
      :fill="fill"
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 -960 960 960"
    >
      <slot />
    </svg>
  </template>
  
  <script setup>
  import { computed } from "vue";
  
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
  