<template>
  <h1>Наши вакансии</h1>
  <div class="v-catalog">
    <div class="v-catalog_item">
      <vCatalogItem
        v-for:="product in PRODUCTS"
        :key="product.article"
        v-bind:product_data="product"
        @addToCart="addToCart"
      />
    </div>
  </div>
</template>

<script>
import vCatalogItem from "./v-catalog-item.vue";
import { mapActions, mapGetters } from "vuex";

export default {
  name: "v-catalog",
  props: {},
  components: { vCatalogItem },
  data() {
    return {};
  },
  computed: {
    ...mapGetters(["PRODUCTS"]),
    products() {
      return this.PRODUCTS;
    },
  },
  methods: {
    ...mapActions(["GET_PRODUCTS_FROM_API", "ADD_TO_CART"]),

    addToCart(data) {
      this.ADD_TO_CART(data);
    },
  },
  mounted() {
    this.GET_PRODUCTS_FROM_API().then((response) => {
      if (response.data) {
        console.log("Данные получены");
      }
    });
  },
};
</script>

<style>
.v-catalog, .v-catalog_item {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: center;
  /* flex-direction: column; */
}
</style>