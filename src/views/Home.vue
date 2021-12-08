<template>
  <div class="home">
    <ProductDescriptionDrawer 
    :product="product"
    :active="active.product_drawer"
    v-on:close-product-drawer="closeProductDrawer()"
    />
    <div class="products-cards-conteiner">
      <ProductsSummaryCard
        v-for="product in items"
        :key="product.id"
        :product="product"
        v-on:view-product="viewProduct($event)"
      />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import items from "../data/items.js";
import ProductsSummaryCard from "../components/products/ProductsSummaryCard.vue";
import ProductDescriptionDrawer from "../components/products/ProductDescriptionDrawer.vue";

export default {
  name: "Home",
  components: {
    ProductsSummaryCard,
    ProductDescriptionDrawer,
  },
  data() {
    return {
      items: items,
      product: null,
      active: {
        product_drawer: false
      }
    };
  },
  methods: {
    viewProduct(product) {
      this.product = product;
      this.active.product_drawer = true;
    },
    closeProductDrawer() {
      this.active.product_drawer = false;
    }
  },
};
</script>

<style>
.products-cards-conteiner {
  display: flex;
  justify-content: center;
  align-items: center;
}
@media screen and (max-width: 600px) {
  .products-cards-conteiner {
    display: flex;
    flex-direction: column;
  }
}
</style>
