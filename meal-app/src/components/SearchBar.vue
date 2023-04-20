<template>
  <input
    type="text"
    :value="props.keyword"
    class="rounded border-2 border-gray-200 w-full"
    @input="$emit('update:keyword', $event.target.value)"
    :placeholder="`Search for Meals by ${props.searchBy}`"
    @change="searchMeals"
  />
</template>

<script setup>
import store from "../store";
import { onMounted } from "vue";

onMounted(() => {
  if (props.keyword) {
    searchMeals();
  }
});

const props = defineProps({
  searchBy: {
    type: String,
    required: false,
  },

  keyword: {
    type: String,
    required: true,
  },
});

function searchMeals() {
  store.dispatch("searchMeals", props.keyword);
}
</script>
