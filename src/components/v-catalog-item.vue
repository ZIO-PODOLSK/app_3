<template>
  <div class="v-catalog-item">
    <img
      class="v-catalog-item_img"
      v-bind:src="product_data.altURL"
      alt="pic"
    />
    <p class="v-catalog-item__name">{{ product_data.name }}</p>
    <p class="v-catalog-item__about">{{ product_data.about }}</p>
    <p class="v-catalog-item__price">{{ product_data.price }}</p>
    <button class="v-catalog-item__btn" @click="addToCart">Купить</button>
  </div>
</template>

<script>
export default {
  name: "v-catalog-item",
  props: {
    product_data: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  data() {
    return {};
  },
  methods: {
    addToCart() {
      this.$emit("addToCart", this.product_data);
    },
  },
};
</script>

<style lang="scss">
.v-catalog-item {
  flex-basis: 40%;
  box-shadow: 0 0 8px 0 grey;
  padding: 20px;
  margin: 20px;
  max-width: 25%;
}

.v-catalog-item_img {
  width: 160px;
  display: block;
  margin: 0 auto;
}
</style>