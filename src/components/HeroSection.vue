<script setup lang="ts">
import Carousel from "./Carousel.vue";
</script>

<template>
  <div class="flex flex-col justify-center items-center text-center h-max my-5">
    <div class="flex justify-center mb-10">
      <Carousel />
    </div>
    <h1 class="text-3xl font-bold text-secondary mb-4">
      Nova coleção Vide Boss 👑
    </h1>
    <p class="text-dark mb-6">
      Peças com estampas exclusivas que combinam sofisticação e conforto. Realce
      sua beleza com produtos que foram feitas para você brilhar!
    </p>
    <button
      class="btn btn btn-secondary w-35 h-13"
      onclick="window.location.href='#collection'"
    >
      Ver coleção
    </button>
  </div>
  <!-- <div class="flex justify-center items-center py-5">
      <img src="../assets/foto2.jpeg" class="size-75 rounded-4xl" />
    </div> -->
</template>
