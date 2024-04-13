<template>
  <div class="v-cart-item">
    <img class="v-cart-item_img" v-bind:src="cart_item_data.altURL" alt="pic" />
    <div>
      <p>{{ cart_item_data.name }}</p>
      <p>{{ cart_item_data.price }}</p>
      <p>{{ cart_item_data.article }}</p>
    </div>
    <div class="v-cart-item__count"></div>
    <p>Всего:</p>
    <span>{{ cart_item_data.quantity }}</span>
    <button @click="deleteFromCart" class="v-cart-item__delete">Удалить</button>
  </div>
</template>

<script>
export default {
  name: "v-cart-item",
  props: {
    cart_item_data: {
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
    deleteFromCart() {
      this.$emit("deleteFromCart");
    },
  },
};
</script>

<style lang="scss">
.v-cart-item {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: center;
  flex-basis: 25%;
  box-shadow: 0 0 8px 0 grey;
  padding: 20px;
  margin: 20px;
  width: 30%;
}
.v-cart-item_img {
  width: 80px;
}
</style>