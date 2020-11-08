<template>
<div>
  <div class="wrapper">
    <div class="search">
      <form class="pure-form">
        <i class="fas fa-search"></i><input v-model="searchText" />
      </form>
    </div>
    <div class="pure-menu pure-menu-horizontal">
      <ul class="pure-menu-list">
        <li class="pure-menu-item"><a @click="select('equipment')" href="#" class="pure-menu-link">Equipment</a></li>
        <li class="pure-menu-item"><a @click="select('clothing')" href="#" class="pure-menu-link">Clothing</a></li>
        <li class="pure-menu-item"><a @click="select('dietary')" href="#" class="pure-menu-link">Deitary</a></li>
      </ul>
    </div>
  </div>
  <ProductList :products="products" />
</div>
</template>

<script>
import ProductList from "../components/ProductList.vue"
export default {
  name: 'Home',
  components: {
    ProductList
  },
  data() {
    return {
      searchText: '',
      type: '',
    }
  },
  computed: {
    products() {
      let result = [];
      result = this.$root.$data.products.filter(product => product.name.toLowerCase().search(this.searchText) >= 0);
      if (this.type === 'equipment' || this.type === 'clothing' || this.type === 'dietary') {
        return result.filter(product => product.type === this.type);
      }
      else {
        return result;
      }
    }
  },
  methods: {
    select(type) {
      this.type = type;
    }
  },
}
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin: 50px 75px;
}

.search {
  border: 1px solid #ccc;
  border-radius: 4px;
  width: 50%;
}

form {
  display: table;
  width: 100%;
}

i {
  display: table-cell;
  padding-left: 10px;
  width: 1px;
}

input {
  display: table-cell;
  font-size: 20px;
  border: none !important;
  box-shadow: none !important;
  width: 100%;
  height: 40px;
}

.pure-menu {
  margin-top:30px;
}

.pure-menu-list {
  display: flex;
  justify-content: center;
}
</style>