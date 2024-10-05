<script setup lang="ts">
import { ref } from "vue";
import Button from "./ui/button.vue";
import Input from "./ui/input.vue";

const searchQuery = ref("");

const handleSearch = () => {
  // TODO: Implement search functionality
  console.log("Searching for:", searchQuery.value);
};
</script>

<template>
  <div class="flex">
    <Input
      v-model="searchQuery"
      placeholder="Search..."
      class="flex-grow mr-2"
    />
    <Button @click="handleSearch">Search</Button>
  </div>
</template>
