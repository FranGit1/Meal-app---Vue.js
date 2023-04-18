<template>
  <div class="p-8">
    <input
      type="text"
      v-model="keyword"
      class="rounded border-2 border-gray-200 w-full"
      placeholder="Search for Meals by Name"
      @change="searchMeals"
    />
    <Meals :meals="meals" />
  </div>
</template>

<script setup>
import { computed } from "@vue/reactivity";
import { useRoute } from "vue-router";
import { ref, onMounted } from "vue";
import store from "../store";
import Meals from "../components/Meals.vue";

const route = useRoute();
const keyword = ref("");
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
  store.dispatch("searchMeals", keyword.value);
}

onMounted(() => {
  keyword.value = route.params.name;
  if (keyword.value) {
    searchMeals();
  }
});
</script>
