<script setup lang="ts">
import { computed } from "vue";

type ButtonVariant = "primary" | "secondary" | "outline" | "ghost";

interface Props {
  variant?: ButtonVariant;
  disabled?: boolean;
}

const props = withDefaults(defineProps<Props>(), {
  variant: "primary",
  disabled: false,
});

const emit = defineEmits<{
  (e: "click", event: MouseEvent): void;
}>();

const variantClasses = computed(() => {
  switch (props.variant) {
    case "primary":
      return "bg-primary text-primary-foreground hover:bg-primary/90";
    case "secondary":
      return "bg-secondary text-secondary-foreground hover:bg-secondary/80";
    case "outline":
      return "border border-input bg-background hover:bg-accent hover:text-accent-foreground";
    case "ghost":
      return "hover:bg-accent hover:text-accent-foreground";
    default:
      return "";
  }
});

const buttonClasses = computed(() => [
  "inline-flex items-center justify-center rounded text-sm font-medium ring-offset-background transition-colors",
  "focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2",
  "disabled:pointer-events-none disabled:opacity-50",
  "px-4 py-2",
  variantClasses.value,
]);
</script>

<template>
  <button
    :class="buttonClasses"
    :disabled="disabled"
    @click="emit('click', $event)"
  >
    <slot></slot>
  </button>
</template>
