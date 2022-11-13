<script setup lang="ts">
import TheMenuItems from "@/components/TheMenuItems.vue";
import ThemeSwitcher from "@/components/ThemeSwitcher.vue";
import { themeModes } from "@/constants/theme";
import { themeStore } from "@/store/ThemeStore";
import { computed } from "@vue/reactivity";
import { onMounted, onUnmounted, reactive } from "vue";
import { useRouter } from "vue-router";

const scrollState = reactive({ scrolled: false });
const isAtTop = () => {
  scrollState.scrolled = window.scrollY > 50;
};

const routes = computed(() => useRouter().currentRoute.value);
onMounted(() => {
  const pageLink = document.querySelectorAll(".menu-scroll-link");
  document.querySelectorAll(".menu-scroll-link");
  pageLink.forEach((elem) => {
    elem.addEventListener("click", (e) => {
      e.preventDefault();
      const link = elem.getAttribute("href");
      console.log(link);
      if (link?.startsWith("#home")) {
        document.querySelector(link)?.scrollIntoView({
          behavior: "smooth",
        });
      } else if (link && document) {
        document.querySelector(link)?.scrollIntoView({
          behavior: "smooth",
        });
      }
    });
  });
});

onMounted(() => window.addEventListener("scroll", isAtTop));
onUnmounted(() => window.removeEventListener("scroll", isAtTop));
</script>

<template>
  <div
    class="navbar sticky top-0 z-[9999] h-12 w-full bg-base-100 py-0 xl:px-5 2xl:mt-16 2xl:px-32"
    :class="scrollState.scrolled ? 'drop-shadow-xl' : ''"
  >
    <div class="navbar-start">
      <div class="dropdown">
        <label tabIndex="{0}" class="btn-ghost btn xl:hidden">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-5 w-5"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              strokeLinecap="round"
              strokeLinejoin="round"
              strokeWidth="2"
              d="M4 6h16M4 12h8m-8 6h16"
            />
          </svg>
        </label>
        <ul
          tabIndex="{0}"
          class="dropdown-content menu rounded-box menu-compact mt-3 w-52 bg-base-100 p-2 shadow"
        >
          <TheMenuItems />
        </ul>
      </div>
      <router-link to="/">
        <a class="btn-ghost btn px-0 normal-case">
          <img
            v-if="themeStore.theme === themeModes.LIGHT"
            :src="'../assets/projects/xafkulogo-dark.svg'"
            class="w-32"
            alt="Avatar"
          />
          <img
            v-else
            :src="'../assets/projects/xafkulogo.svg'"
            class="w-32"
            alt="Avatar"
          />
        </a>
      </router-link>
    </div>

    <div class="navbar-end">
      <ul
        class="menu menu-horizontal mr-10 hidden flex-nowrap gap-12 p-0 xl:flex"
      >
        <TheMenuItems />
      </ul>

      <ThemeSwitcher />
    </div>
  </div>
</template>
1
