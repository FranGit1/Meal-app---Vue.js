<template>
  <div class="p-8 flex flex-col items-center">
    <SearchByLetter />

    <Meals :meals="meals" />
  </div>
</template>

<script setup>
import store from "../store";
import SearchBar from "../components/SearchBar.vue";
import { computed } from "@vue/reactivity";
import Meals from "../components/Meals.vue";
import SearchByLetter from "../components/SearchByLetter.vue";
import { onUpdated } from "vue";
import { useRoute } from "vue-router";

const route = useRoute();
const meals = computed(() => store.state.searchedMeals);

onUpdated(() => {
  if (route.params.letter) {
    searchByletter(route.params.letter);
  }
});

function searchByletter(letter) {
  store.dispatch("searchByFirstLetter", letter);
}
</script>
