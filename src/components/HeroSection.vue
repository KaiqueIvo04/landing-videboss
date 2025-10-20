<script setup lang="ts">
import Carousel from "./Carousel.vue";
</script>

<template>
  <div class="flex justify-center mb-10">
    <Carousel />
  </div>
  <h1 class="text-3xl text-shadow-md font-bold text-secondary mb-4">
    Nova coleção Vide Boss 👑
  </h1>
  <p class="mb-6 text-shadow-md">
    Peças com estampas exclusivas que combinam sofisticação e conforto. Realce
    sua beleza com produtos que foram feitos para você brilhar!
  </p>
  <button
    class="btn btn btn-secondary w-35 h-13"
    onclick="window.location.href='#collection'"
  >
    Ver coleção
  </button>
</template>
