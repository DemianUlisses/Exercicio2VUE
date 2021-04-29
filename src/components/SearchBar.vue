<template>
  <form v-on:submit.prevent="handleSearch">
    <input type="text" v-on:keyup="handleSearch" v-model="search" />
    <button type="submit">Buscar</button>
  </form>
</template>

<script>
export default {
  props: {
    onSearch: Function,
  },
  data() {
    return {
      search: "",
    };
  },
  methods: {
    handleSearch() {
      this.onSearch(this.search);
    },
  },
};
</script>