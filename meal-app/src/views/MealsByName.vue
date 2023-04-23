<template>
  <div class="p-8">
    <SearchBar
      :keyword="keyword"
      v-on:update:keyword="keyword = $event"
      searchBy="Name"
    />
    <Meals :meals="meals" />
  </div>
</template>

<script setup>
import SearchBar from "../components/SearchBar.vue";
import { computed, reactive } from "@vue/reactivity";
import { useRoute } from "vue-router";
import { ref, onBeforeMount, onMounted } from "vue";
import store from "../store";
import Meals from "../components/Meals.vue";

const route = useRoute();
const keyword = ref("");
const meals = computed(() => store.state.searchedMeals);
onMounted(() => {
  store.commit("setSearchedMeals", null);
});
onBeforeMount(() => {
  keyword.value = route.params.name;
});
</script>
