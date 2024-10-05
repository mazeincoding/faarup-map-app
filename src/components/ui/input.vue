<script setup lang="ts">
import { computed } from "vue";

interface InputProps {
  type?: string;
  placeholder?: string;
  disabled?: boolean;
}

const props = withDefaults(defineProps<InputProps>(), {
  type: "text",
  placeholder: "",
  disabled: false,
});

const emit = defineEmits<{
  (e: "update:modelValue", value: string): void;
}>();

const inputClasses = computed(() => [
  "flex h-10 w-full rounded bg-secondary px-3 py-2 text-base ring-offset-background",
  "file:border-0 file:bg-transparent file:text-base file:font-medium",
  "placeholder:text-muted-foreground",
  "focus-visible:outline-none focus-visible:ring-1 focus-visible:ring-ring focus-visible:ring-offset-1 outline-none",
  "disabled:cursor-not-allowed disabled:opacity-50",
  "transition-all duration-200 ease-in-out", // Added transition
]);
</script>

<template>
  <input
    :type="type"
    :placeholder="placeholder"
    :disabled="disabled"
    :class="inputClasses"
    @input="
      emit('update:modelValue', ($event.target as HTMLInputElement).value)
    "
  />
</template>
