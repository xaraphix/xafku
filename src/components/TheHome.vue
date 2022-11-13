<script setup lang="ts">
import { themeModes } from "@/constants/theme";
import { themeStore } from "@/store/ThemeStore";
</script>

<template>
  <div
    id="home"
    class="-mt-10 flex h-screen w-full flex-col items-center justify-center gap-5 lg:-mt-36 xl:-mt-32"
  >
    <div class="card mt-auto mb-20 w-3/4 pt-[200px] lg:pt-0 lg:card-side">
      <div class="flex flex-col justify-center gap-10">
        <h1 class="text-neutral-dark text-8xl font-extralight">XAFKU</h1>
        <h2 class="text-neutral-dark py-1 text-3xl font-medium">
          Easily Manage local/remote kafka clusters
        </h2>
        <p class="text-neutral-dark grow-0">
          Conviniently speed up your app development, and leave kafka management
          to xafku.
        </p>
        <div class="flex gap-5">
          <button class="btn-primary btn">Demo</button>
          <button
            class="btn-primary btn bg-opacity-0 text-primary hover:bg-opacity-100 hover:text-primary-content"
          >
            Download
          </button>
        </div>
      </div>
      <img
        v-if="themeStore.theme === themeModes.DARK"
        :src="'../assets/xafku-illustration-dark.svg'"
        class="max-w-lg xl:max-w-3xl"
        alt="Xafku illustration"
      />
      <img
        v-else
        :src="'../assets/xafku-illustration.svg'"
        class="max-w-lg xl:max-w-3xl"
        alt="Xafku illustration"
      />
    </div>
  </div>
</template>
