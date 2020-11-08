<template>
    <div class="wrapper">
        <div>
            <CartList :cart="cart" />
        </div>
    </div>
</template>

<script>
import CartList from "../components/CartList.vue"
export default {
  name: 'Cart',
  components: {
    CartList
  },
  data() {
    return {
    }
  },
  computed: {
    cart() {
      return this.$root.$data.cart;
    }
  },
}
</script>

<style scoped>
.wrapper {
    margin: 50px 100px;
}
</style>