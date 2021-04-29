<template>
  <div>
    <ul>
      <li v-for="product in products" :key="product.id">
        <ProductItem :product="product" />
      </li>
    </ul>
    {{ totalProducts }}
  </div>
</template>

<script>
import ProductItem from "./ProductItem";

export default {
  props: {
    products: Array,
  },
  components: {
    ProductItem,
  },
  computed: {
    totalProducts() {
      const total = this.products.length;
      return total > 1 ? `Total: ${total} produtos` : `Total: ${total} produto`;
    },
  },
};
</script>
