<template>
  <!-- COLEÇÃO 1-->
  <div id="collection">
    <h2 class="text-3xl text-shadow-md font-bold text-secondary mb-4">
      Coleção Lisas ❣️
    </h2>
  </div>
  <div class="grid lg:grid-cols-3 grid-cols-1 gap-4 h-full lg:w-3/4">
    <div
      v-for="(item, i) in images_collection1"
      :key="i"
      class="card bg-primary shadow-sm hover:shadow-xl transition-shadow"
    >
      <figure>
        <img :src="item.image" />
      </figure>

      <div class="card-body">
        <h2 class="card-title lg:text-md sm:text-sm">{{ item.name }}</h2>
        <div class="card-actions justify-end">
          <div class="badge badge-secondary">NEW</div>
        </div>
      </div>
    </div>
  </div>

  <!-- COLEÇÃO 2 -->
  <div class="mt-15">
    <h2 class="text-3xl text-shadow-md font-bold text-secondary mb-4">
      Coleção Estampadas 💝
    </h2>
  </div>
  <div class="grid lg:grid-cols-3 grid-cols-1 gap-4 h-full lg:w-3/4">
    <div
      v-for="(item, i) in images_collection2"
      :key="i"
      class="card bg-primary shadow-sm hover:shadow-xl transition-shadow"
    >
      <figure>
        <img :src="item.image" />
      </figure>

      <div class="card-body">
        <h2 class="card-title lg:text-md sm:text-sm">{{ item.name }}</h2>
        <div class="card-actions justify-end">
          <div class="badge badge-secondary">NEW</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { util } from "../script/util";

const images_collection1 = ref([]);
const images_collection2 = ref([]);

async function loadImages() {
  images_collection1.value = await util.loadImagesAndNames(
    import.meta.env.VITE_URL_COLECAO1
  );
  images_collection2.value = await util.loadImagesAndNames(
    import.meta.env.VITE_URL_COLECAO2
  );
}

onMounted(async () => {
  await loadImages();
});
</script>
