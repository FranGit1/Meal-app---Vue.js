<template>
  <div class="p-8">
    <SearchBar :keyword="keyword" v-on:update:keyword="keyword = $event" />
    <Meals :meals="meals" />
  </div>
</template>

<script setup>
import SearchBar from "../components/SearchBar.vue";
import { computed } from "@vue/reactivity";
import { useRoute } from "vue-router";
import { ref, onBeforeMount } from "vue";
import store from "../store";
import Meals from "../components/Meals.vue";

const route = useRoute();
const keyword = ref("");
const meals = computed(() => store.state.searchedMeals);

// function searchMeals() {
//   store.dispatch("searchMeals", keyword.value);
// }

onBeforeMount(() => {
  keyword.value = route.params.name;
  // if (keyword.value) {
  //   searchMeals();
  // }
});
</script>
