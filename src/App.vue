<script setup lang="ts">
import { ref, computed } from "vue";
import Button from "./components/ui/button.vue";
import Header from "./components/header.vue";

const title = ref("Quick Vue Page");
const message = ref("Hey there! This is a quick Vue page.");

const count = ref(0);
const increment = () => {
  if (count.value < 5) {
    count.value++;
  }
};

const decrement = () => {
  if (count.value > 0) {
    count.value--;
  }
};

const isIncrementDisabled = computed(() => count.value >= 5);
const isDecrementDisabled = computed(() => count.value <= 0);
</script>

<template>
  <div class="min-h-screen bg-background flex flex-col">
    <Header />
    <main class="flex-grow flex flex-col items-center justify-center gap-6">
      <h1 class="text-4xl font-bold text-foreground">{{ title }}</h1>
      <p class="text-lg text-foreground">{{ message }}</p>
      <p class="text-3xl text-foreground">Count: {{ count }}</p>
      <div class="flex gap-4">
        <Button
          @click="decrement"
          :disabled="isDecrementDisabled"
          variant="secondary"
        >
          Decrement
        </Button>
        <Button
          @click="increment"
          :disabled="isIncrementDisabled"
          variant="primary"
        >
          Increment
        </Button>
      </div>
    </main>
  </div>
</template>
