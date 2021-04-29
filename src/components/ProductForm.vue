<template>
  <form v-on:submit.prevent="addProduct">
    <input type="text" v-model="name">
    <button type="submit">Registrar</button>
  </form>
</template>

<script>
export default {
  props: {
    onAddProduct: Function
  },
  data() {
    return {
      name: ""
    };
  },
  methods: {
    addProduct() {
      const product = {
        name: this.name
      };

      this.onAddProduct(product);
    }
  }
};
</script>
