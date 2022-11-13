<script setup lang="ts">
import "./assets/base.css";
import TheNavigationVue from "./layout/TheNavigation.vue";
import TheFooterVue from "./layout/TheFooter.vue";
import { themeModes } from "./constants/theme";
import { themeStore } from "./store/ThemeStore";

const darkThemeMq = window.matchMedia("(prefers-color-scheme: dark)");
if (
  localStorage.getItem("color-theme") === "dark" ||
  (!("color-theme" in localStorage) && darkThemeMq.matches)
) {
  localStorage.setItem("color-theme", "dark");
  themeStore.setTheme(themeModes.DARK);
} else {
  localStorage.setItem("color-theme", "light");
  themeStore.setTheme(themeModes.LIGHT);
}
</script>

<template>
  <div
    class="flex flex-col font-sans min-h-screen w-screen"
    :data-theme="themeStore.theme === themeModes.DARK ? 'dark' : 'light'"
  >
    <TheNavigationVue />
    <div class="flex flex-col min-h-screen px-16 xl:px-5 2xl:px-32 py-10">
      <router-view></router-view>
    </div>
    <TheFooterVue />
  </div>
</template>
