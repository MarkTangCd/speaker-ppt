<script setup lang="ts">
import { ref, onMounted } from 'vue'
import ModelViewer from '@metamask/logo';

const logoContainer = ref<Element | null>(null);

const viewer = ModelViewer({
  pxNotRatio: true,
  width: 270,
  height: 170,
  followMouse: false,
  slowDrift: false
});

onMounted(() => {
  if (logoContainer.value) {
    logoContainer.value.appendChild(viewer.container);
  }
});
</script>

<template>
  <div class="pt-12 flex justify-center" ref="logoContainer">
  </div>
</template>
