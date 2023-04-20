<template>
  <div class="flex flex-col items-center p-8 justify-center">
    <form @submit.prevent="search">
      <input
        type="text"
        class="rounded border-2 border-gray-200 w-full"
        placeholder="Search for meals"
        :value="keyword"
        @input="keyword = $event.target.value"
      />
      <button type="submit">Search</button>
    </form>

    <SearchByLetter />
  </div>
</template>

<script>
import { computed, onMounted } from "vue";
import store from "../store";
import axiosClient from "../axiosClient";
import SearchByLetter from "../components/SearchByLetter.vue";

export default {
  data() {
    return {
      keyword: "",
    };
  },
  methods: {
    search() {
      this.$router.push({ path: `/by-name/${this.keyword}` });
    },
  },

  onMounted() {
    const response = axiosClient.get("/list.php?i=list");
    console.log(response);
  },

  components: {
    SearchByLetter,
  },
};
</script>
