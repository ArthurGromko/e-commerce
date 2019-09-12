<template>
  <div class="products-list">
    <div style="border:3px solid black" v-for="(product, index) in $store.getters.products" :key="index" @click="$router.push(`/product/${product.slug}`)">
      <img :src="product.imageUrl" />
      <h2>{{product.name}}</h2>
      <p class="description">{{product.description}}</p>
      <p class="price">${{product.price}}</p>
      <button @click.stop="deleteProduct(index)">Remove product</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Products',
  methods: {
    deleteProduct(index) {
      this.$store.commit('deleteProduct', index)
    }
  }
}
</script>

<style scoped>
.products-list {
  display: flex;
  padding-top: 30px;
}
.products-list div {
  width: 33%;
    background-color: rgb(235, 235, 235);
  padding: 30px;
  
}

button {
  font-size: 1.3rem;
  background-color: darkslategrey;
  color: white;
  border-width: 0.3rem
}

.description,
.price {
  padding-top: 20px;
}
</style>