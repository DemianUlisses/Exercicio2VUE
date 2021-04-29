<template>
  <div id="app">
    <img width="25%" src="./assets/logo.png" />
    <SearchBar :onSearch="handleSearchProducts" />
    <ProductForm :onAddProduct="handleAddProduct" />
    <ProductsList
      :products="listedProducts.length > 0 ? listedProducts : products"
    />
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar";
import ProductsList from "./components/ProductsList";
import ProductForm from "./components/ProductForm";

export default {
  name: "App",
  components: {
    ProductsList,
    ProductForm,
    SearchBar,
  },
  methods: {
    handleAddProduct(product) {
      this.products = this.products.concat({
        id: this.products.length + 1,
        ...product,
      });
    },
    handleSearchProducts(text) {
      const results = this.products.filter((p) => p.name.startsWith(text));
      if (results.length > 0) {
        this.listedProducts = results;
      } else {
        this.listedProducts = this.products;
      }
    },
  },
  data() {
    return {
      products: [],
      listedProducts: [],
    };
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
