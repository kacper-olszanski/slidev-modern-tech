<template>
    <header v-if="logoHeader || $slidev.configs.logoHeader">
      <img :src="logoSrc" width="60" height="60" class="object-contain" />
    </header>
  </template>
  
  <script setup lang="ts">
  import { defineProps, computed } from 'vue'
  import { resolveAssetUrl } from './layoutHelper'
  const props = defineProps({
    logoHeader: {
      type: String,
    },

  })

  const colors = {
    primary: $slidev.configs.primary,
    secondary: $slidev.configs.secondary,
    accent: $slidev.configs.accent,
  }
  let root = document.documentElement;
  Object.entries(colors).filter(([k, v]) => v !== undefined).forEach(([key, color])=> {
    root.style.setProperty(`--slidev-theme-${key}`, color);
  });
  const logoSrc = computed(() => resolveAssetUrl(props.logoHeader ?? $slidev.configs.logoHeader))
  </script>