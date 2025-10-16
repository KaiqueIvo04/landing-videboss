<template>
  <header class="fixed inset-x-0 bottom-0 z-50">
    <nav
      class="bg-pink-500/70 backdrop-blur-md rounded-t-3xl shadow-[0_-4px_12px_rgba(0,0,0,0.2)] p-2 justify-items-center"
    >
      <div class="lg:w-3/5 w-full">
        <ul class="flex justify-around items-center">
          <li>
            <a href="#" class="flex flex-col items-center gap-1">
              <span class="material-symbols-outlined text-white text-3xl"
                >home</span
              >
              <span class="text-xs text-white">Início</span>
            </a>
          </li>
          <li>
            <a href="#" class="flex flex-col items-center gap-1">
              <span class="material-symbols-outlined text-white text-3xl"
                >favorite</span
              >
              <span class="text-xs text-white">Favoritos</span>
            </a>
          </li>
          <li>
            <a href="#" class="flex flex-col items-center gap-1">
              <span class="material-symbols-outlined text-white text-3xl"
                >phone</span
              >
              <span class="text-xs text-white">Contato</span>
            </a>
          </li>
          <li>
            <a href="#" class="flex flex-col items-center gap-1">
              <span class="material-symbols-outlined text-white text-3xl"
                >info</span
              >
              <span class="text-xs text-white">Sobre</span>
            </a>
          </li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<style scoped>
/* Pequeno ajuste pra área de toque */
li a {
  padding: 8px;
}
</style>
