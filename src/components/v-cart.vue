<template>
  <div class="v-cart">
    <router-link :to="{ name: 'catalog' }">
      <button class="btn">На главную</button>
    </router-link>
  </div>

  <p v-if="!CART.length">Корзина пустая</p>

  <vCartItem class= "v-cart-item_div"
    v-for="(item, index) in CART"
    :key="item.article"
    :cart_item_data="item"
    @deleteFromCart="deleteFromCart(index)"
  />
</template>

<script>
import vCartItem from "./v-cart-item.vue";
import { mapActions, mapGetters } from "vuex";

export default {
  name: "v-cart",
  components: { vCartItem },
  props: {
    cart_data: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  data() {
    return {};
  },
  computed: {
    ...mapGetters(["CART"]),
  },

  methods: {
    ...mapActions(["DELETE_FROM_CART"]),
    deleteFromCart(index) {
      this.DELETE_FROM_CART(index);
    },
  },
};
</script>

<style scoped>
.v-cart {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  color: grey;
  font-size: 20px;
  margin-bottom: 50px;
}

.v-cart-item_div{
  margin: 0 auto;
  margin-bottom: 15px;
}
</style>