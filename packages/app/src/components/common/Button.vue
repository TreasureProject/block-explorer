<template>
  <component class="button" :is="tag" :type="type" :class="[variant, color, size]" v-bind="$attrs">
    <LoadingIcon v-if="loading === true" />
    <slot />
  </component>
</template>

<script lang="ts">
import { defineComponent } from "vue";

import LoadingIcon from "@/components/icons/LoadingIcon.vue";

import type { PropType } from "vue";

export default defineComponent({
  inheritAttrs: false,
  props: {
    tag: {
      type: String,
      default: "button",
    },
    color: {
      type: String as PropType<"primary" | "secondary">,
      default: "primary",
    },
    size: {
      type: String as PropType<"md" | "lg" | "sm">,
      default: "md",
    },
    variant: {
      type: String as PropType<"contained" | "outlined">,
      default: "contained",
    },
    type: {
      type: String,
      default: "button",
    },
    loading: {
      type: Boolean,
      default: false,
    },
  },
  components: { LoadingIcon },
});
</script>

<style lang="scss" scoped>
.button {
  @apply flex items-center justify-center rounded-md px-4 py-3 text-lg font-light leading-none no-underline shadow-sm;
  @apply focus:outline-none focus:ring-2 focus:ring-primary-500 focus:ring-offset-2;
  @apply appearance-none disabled:cursor-not-allowed disabled:opacity-50;

  &.sm {
    @apply px-3 py-1.5 text-sm font-medium;
  }
  &.md {
    @apply px-4 py-2.5 text-sm font-medium;
  }
  &.lg {
    @apply px-4 py-3 text-xl font-bold;
  }

  &.contained {
    @apply text-cream;
    @apply border border-transparent;

    &.primary {
      @apply bg-primary-600 hover:bg-primary-700 disabled:hover:bg-primary-600;
    }

    &.secondary {
      @apply bg-secondary-600 hover:bg-secondary-700 disabled:hover:bg-secondary-600;
    }
  }
  &.outlined {
    @apply border border-night-800;
    @apply bg-night-700 hover:bg-night-500 disabled:hover:bg-night-800;

    &.primary {
      @apply text-primary-700;
    }

    &.secondary {
      @apply text-secondary-700;
    }

    &.neutral {
      @apply text-silver-500;
    }
  }
}
</style>
