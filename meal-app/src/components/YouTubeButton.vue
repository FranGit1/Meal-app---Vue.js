<template>
  <a
    :href="href"
    target="_blank"
    class="px-3 py-2 rounded border-2 border-red-600 hover:bg-red-600 hover:text-white transition-colors"
    >Youtube</a
  >
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  href: {
    type: String,
    default: "https://www.youtube.com/",
  },
});
</script>
