<script setup lang="ts">
useHead({
  titleTemplate: (title) => (title ? `${title} - Gecynd` : "Gecynd"),
});
</script>

<template>
  <UApp>
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </UApp>
</template>

<style>
@import "tailwindcss";
@import "@nuxt/ui";

@theme {
  --color-primary: #2d6a8f;
}
</style>
