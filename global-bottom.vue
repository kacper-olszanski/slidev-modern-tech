<style>
.signet {
  height: 2em;
  width: 2em;
}
.right {
  display: flex;
  flex-direction: row;
  min-width: 6em;
  justify-content: space-between;
  align-items: center;
  align-content: center;
}
.spacer {
  width: 0.125em;
  height: 80%;
  border-radius: 25%;
  background-color: var(--bright-color);
}
.foot {
    display: flex;
    justify-content: space-between;
}
</style>
<template>
    <footer class="absolute bottom-0 right-0 left-0 p-3 foot">
      <p>{{ $slidev.configs.bottomText }}</p>
      <div class="right"> 
        <div class="signet" v-if="props.logoFooter || $slidev.configs.logoFooter" :style="style">
          
        </div>
        <div class="spacer">

        </div>
        <div>
            <SlideCurrentNo /> / <SlidesTotal />
        </div>
    </div>
    </footer>
  </template>
  
  <script setup lang="ts">
  import { computed, defineProps } from 'vue'
    import { handleBackground, resolveAssetUrl } from './layoutHelper';
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

    const style =  computed(() => handleBackground(props.logoFooter ?? $slidev.configs.logoFooter));
    const logoSrc =  computed(() => resolveAssetUrl(props.logoFooter ?? $slidev.configs.logoFooter));
  </script>