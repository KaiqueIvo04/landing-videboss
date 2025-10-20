<template>
  <!-- HEADER BAR -->
  <section
    class="bg-base-100 shadow-md flex justify-between items-center h-max p-2"
  >
    <div class="w-20"></div>

    <!-- Logo centralizada -->
    <div class="flex-1 flex justify-center">
      <a href="#">
        <span class="sr-only">Vide T-shirts</span>
        <img src="./assets/vide-logo.png" alt="Vide T-shirts" class="h-20 w-auto" />
      </a>
    </div>

    <!-- Botão de tema -->
    <div class="flex items-center justify-center w-20">
      <label class="swap swap-rotate">
        <!-- this hidden checkbox controls the state -->
        <input
          ref="themeSet"
          type="checkbox"
          class="theme-controller"
          value="dark"
          @change="setDarkTheme"
        />

        <!-- sun icon -->
        <svg
          class="swap-off h-10 w-10 fill-current"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
        >
          <path
            d="M5.64,17l-.71.71a1,1,0,0,0,0,1.41,1,1,0,0,0,1.41,0l.71-.71A1,1,0,0,0,5.64,17ZM5,12a1,1,0,0,0-1-1H3a1,1,0,0,0,0,2H4A1,1,0,0,0,5,12Zm7-7a1,1,0,0,0,1-1V3a1,1,0,0,0-2,0V4A1,1,0,0,0,12,5ZM5.64,7.05a1,1,0,0,0,.7.29,1,1,0,0,0,.71-.29,1,1,0,0,0,0-1.41l-.71-.71A1,1,0,0,0,4.93,6.34Zm12,.29a1,1,0,0,0,.7-.29l.71-.71a1,1,0,1,0-1.41-1.41L17,5.64a1,1,0,0,0,0,1.41A1,1,0,0,0,17.66,7.34ZM21,11H20a1,1,0,0,0,0,2h1a1,1,0,0,0,0-2Zm-9,8a1,1,0,0,0-1,1v1a1,1,0,0,0,2,0V20A1,1,0,0,0,12,19ZM18.36,17A1,1,0,0,0,17,18.36l.71.71a1,1,0,0,0,1.41,0,1,1,0,0,0,0-1.41ZM12,6.5A5.5,5.5,0,1,0,17.5,12,5.51,5.51,0,0,0,12,6.5Zm0,9A3.5,3.5,0,1,1,15.5,12,3.5,3.5,0,0,1,12,15.5Z"
          />
        </svg>

        <!-- moon icon -->
        <svg
          class="swap-on h-10 w-10 fill-current"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
        >
          <path
            d="M21.64,13a1,1,0,0,0-1.05-.14,8.05,8.05,0,0,1-3.37.73A8.15,8.15,0,0,1,9.08,5.49a8.59,8.59,0,0,1,.25-2A1,1,0,0,0,8,2.36,10.14,10.14,0,1,0,22,14.05,1,1,0,0,0,21.64,13Zm-9.5,6.69A8.14,8.14,0,0,1,7.08,5.22v.27A10.15,10.15,0,0,0,17.22,15.63a9.79,9.79,0,0,0,2.1-.22A8.11,8.11,0,0,1,12.14,19.73Z"
          />
        </svg>
      </label>
    </div>
  </section>

  <!-- MAIN CONTENT -->
  <section class="flex justify-center w-full">
    <div class="lg:px-50 md:px-35 sm:px-10">
      <div
        class="flex flex-col justify-center items-center text-center h-max my-5"
      >
        <HeroSection />
      </div>

      <div class="divider mb-10"></div>

      <div class="flex h-max justify-center mb-10">
        <Benefits />
      </div>

      <div class="divider mb-10"></div>

      <div class="flex flex-col items-center justify-center mb-10">
        <Collection />
      </div>

      <div class="divider mb-10"></div>

      <div
        class="flex flex-col justify-center items-center text-center h-max my-5"
      >
        <About />
      </div>

      <div class="divider mb-10"></div>

      <div
        class="flex flex-col justify-center items-center text-center h-max my-5 bg-gradient-to-br"
      >
        <Contact />
      </div>

      <div class="divider mb-10"></div>
    </div>
  </section>

  <!-- FOOTER -->
  <Footer />

  <!-- NAV BAR -->
  <NavBar />
</template>

<script setup>
import { onMounted, ref } from "vue";
import About from "./components/About.vue";
import Benefits from "./components/Benefits.vue";
import Collection from "./components/Collection.vue";
import Contact from "./components/Contact.vue";
import Footer from "./components/Footer.vue";
import HeroSection from "./components/HeroSection.vue";
import NavBar from "./components/NavBar.vue";

const themeSet = ref(null);

function setDarkTheme() {
  const isDark = themeSet.value.checked;

  if (isDark) {
    document.documentElement.setAttribute("data-theme", "dark");
    localStorage.setItem("theme", "dark");
  } else {
    document.documentElement.setAttribute("data-theme", "mytheme");
    localStorage.setItem("theme", "mytheme");
  }
};

onMounted(() => {
  // Pega o tema salvo ou usa o padrão do sistema
  const savedTheme = localStorage.getItem("theme");
  const prefersDark = window.matchMedia("(prefers-color-scheme: dark)").matches;

  const isDark = savedTheme === "dark" || (!savedTheme && prefersDark);

  // Aplica o tema
  if (isDark) {
    document.documentElement.setAttribute("data-theme", "dark");
    if (themeSet.value) {
      themeSet.value.checked = true;
    }
  } else {
    document.documentElement.setAttribute("data-theme", "mytheme");
    if (themeSet.value) {
      themeSet.value.checked = false;
    }
  }

  // Salva no localStorage se ainda não existe
  if (!savedTheme) {
    localStorage.setItem("theme", isDark ? "dark" : "mytheme");
  }
});
</script>

<style scoped></style>
