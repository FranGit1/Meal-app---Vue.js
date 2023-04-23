<template>
  <div class="p-8 flex flex-col items-center">
    <SearchByLetter />

    <Meals :meals="meals" />
  </div>
</template>

<script setup>
import store from "../store";
import { computed, reactive } from "@vue/reactivity";
import Meals from "../components/Meals.vue";
import SearchByLetter from "../components/SearchByLetter.vue";
import { onUpdated, onUnmounted, onMounted } from "vue";
import { useRoute, onBeforeRouteLeave } from "vue-router";

const route = useRoute();
const meals = computed(() => store.state.searchedMeals);

onMounted(() => {
  store.commit("setSearchedMeals", null);
});

onUpdated(() => {
  if (route.params.letter) {
    searchByletter(route.params.letter);
  }
});

onBeforeRouteLeave((to, from, next) => {
  store.dispatch("setSearchedMeals", null);
  next();
});

function searchByletter(letter) {
  store.dispatch("searchByFirstLetter", letter);
}
</script>
