<template>
<div class="wrapper">
  <div class="products">
    <div class="product" v-for="product in products" :key="product.id">
      <div class="image">
        <img :src="'/images/products/'+product.image">
      </div>
      <div class="info">
        <p>{{product.name}}</p>
        <h3>{{product.description}}</h3>
        <h2>{{product.price}}</h2>
        <button @click="addToCart(product)" class="auto">Add to Cart</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'ProductList',
  props: {
    products: Array
  },
  methods: {
      addToCart(product) {
          let exist = false;
          this.$root.$data.cart.forEach(item => {
            if (item.id == product.id) {
                exist = true;
            } 
          });
          if (!exist) {
            product.quantity = 1;
            this.$root.$data.cart.push(product);
          }
          else {
            product.quantity++;
          }
      }
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

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  margin: 10px;
  margin-top: 50px;
  width: 450px;
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

button {
  height: 40px;
  background: #33427e;
  color: #F4E022;
  border: none;
}

.auto {
  margin-left: auto;
}
</style>