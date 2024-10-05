<script setup lang="ts">
import SearchBar from "./search-bar.vue";
</script>

<template>
  <header class="w-full p-4 bg-background shadow-sm">
    <div class="mx-auto flex justify-between items-center gap-6">
      <h1
        class="text-2xl font-bold text-foreground whitespace-nowrap hidden sm:block"
      >
        Fårup Map
      </h1>
      <SearchBar class="w-full max-w-none sm:max-w-md" />
    </div>
  </header>
</template>
