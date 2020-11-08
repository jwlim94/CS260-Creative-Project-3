<template>
<div class="wrapper">
  <div class="products">
    <div v-if="numProducts === 0" class="empty-cart">Cart is empty</div>
    <div v-else class="product" v-for="product in cart" :key="product.id">
        <div class="image">
            <img :src="'/images/products/'+product.image">
        </div>
        <div class="info">
            <p>{{product.name}}</p>
            <h3>{{product.description}}</h3>
            <h2>{{product.price}} EA</h2>
            <div class="order">
                <div class="quantity">Qty: {{product.quantity}}</div>
                <button @click="removeFromCart(product)" class="auto">Remove all</button>
            </div>
        </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'CartList',
  props: {
    cart: Array
  },
  computed: {
    numProducts() {
        return this.$root.$data.cart.length;
    },
  },
  methods: {
    removeFromCart(product) {
        this.$root.$data.cart.splice(this.$root.$data.cart.indexOf(product), 1);
    },
  }
}
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  padding-bottom: 150px;
}

.empty-cart {
    font-size: 2em;
    font-weight: bold;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  margin: 10px;
  margin-top: 50px;
  width: 400px;
  display: flex;
}

.product img {
  border: 2px solid #333;
  height: 200px;
  width: 200px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #18224b;
  color: #F4E022;
  padding: 10px 20px;
  height: 200px;
  width: 250px;
}

.info p {
  font-size: 20px;
}

.info h2 {
  font-size: 14px;
}

.info h3 {
  font-size: 14px;
  margin-bottom: 20px;
}

.order {
    display:flex;
    justify-content: center;
    align-items: center;
}

.quantity {
    color: #f26868;
    font-weight: bold;
}

button {
  height: 40px;
  background: #f26868;
  color: white;
  border: none;
}

.auto {
  margin-left: auto;
}
</style>