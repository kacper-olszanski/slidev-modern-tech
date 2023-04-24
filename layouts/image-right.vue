<script setup lang="ts">
import { computed } from 'vue'
import { handleBackground } from '../layoutHelper'
const props = defineProps({
  image: {
    type: String,
  },
  class: {
    type: String,
  },
})
const style = computed(() => handleBackground(props.image))
</script>

<template>
  <div class="grid grid-cols-5 w-full h-full">
    <div class="slidev-layout default image-right" :class="props.class">
        <div class="my-auto card">
            <slot />
        </div>

    </div>
    <div class="image-right-img" :style="style"></div>

  </div>
</template>