<template>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
    <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal" />
  </div>
  <div v-if="meals === null" class="flex justify-center text-gray-600 p-8">
    No meals that start with that name
  </div>

  <!-- <div v-if="!meals.length" class="flex justify-center text-gray-600 p-8">
    Search for meals to display them
  </div> -->
</template>

<script setup>
import MealItem from "./MealItem.vue";
import { onUpdated } from "vue";
const { meals } = defineProps({
  meals: {
    required: true,
    type: Array,
  },
});

onUpdated(() => {});
</script>
