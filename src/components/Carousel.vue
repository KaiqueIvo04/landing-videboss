<template>
  <div class="relative overflow-hidden lg:w-100 rounded-2xl shadow-2xl">
    <div
      class="flex transition-transform duration-700 ease-in-out"
      :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
    >
      <img
        v-for="(img, i) in images"
        :key="i"
        :src="img"
        class="w-full flex-shrink-0 rounded-2xl"
      />
    </div>

    <div
      class="absolute left-5 right-5 top-1/2 flex -translate-y-1/2 transform justify-between"
    >
      <button class="btn btn-circle" @click="prevSlide">❮</button>
      <button class="btn btn-circle" @click="nextSlide">❯</button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

// Importa imagens de forma compatível com Vite
const images = [
  new URL("../assets/foto1.jpeg", import.meta.url).href,
  new URL("../assets/foto2.jpeg", import.meta.url).href,
  new URL("../assets/foto3.jpeg", import.meta.url).href,
  new URL("../assets/foto4.jpeg", import.meta.url).href,
];

const currentIndex = ref(0);
let intervalId;

function nextSlide() {
  currentIndex.value = (currentIndex.value + 1) % images.length;
}

function prevSlide() {
  currentIndex.value = (currentIndex.value - 1 + images.length) % images.length;
}

onMounted(() => {
  intervalId = setInterval(nextSlide, 3000);
});

onBeforeUnmount(() => {
  clearInterval(intervalId);
});
</script>

<style>
</style>
