<style>
.foot {
    display: flex;
    justify-content: space-between;
}
</style>
<template>
    <footer class="absolute bottom-0 right-0 left-0 p-3 foot">
      <p>{{ $slidev.configs.bottomText }}</p>
      <div> 
        <div v-if="logoFooter" :style="logoSrc">

        </div>
        <div>
            <SlideCurrentNo /> / <SlidesTotal />
        </div>
    </div>
    </footer>
  </template>
  
  <script setup lang="ts">
  import { computed, defineProps } from 'vue'
    import { handleBackground } from './layoutHelper';
  const props = defineProps({
    bottomText: {
        type: String,
        default: "",
      }
    ,
    logoFooter: {
        type: String,
      },
    })

    const logoSrc =  computed(() => handleBackground(props.logoFooter ?? $slidev.configs.logoFooter));
  </script>