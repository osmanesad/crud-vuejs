<template>
  <!-- Buraya HelloWorld.veu içerisinde "template" kısmında ne yaptıysam oonu çağırıyor.  -->
  <div id="app">
    
    <ProductList @delete:product="deleteProduct" @update:product="updateProduct"  :products="products"/> <!-- Eyy ProductList eğer olurda bana bir event yollarsan -> @delete:product="" -->
    <br/>
    <h3>Ürün Ekle</h3>
    <ProductAdd @add:product="addProduct" />
  </div>
</template>

<script>
import ProductList from "./components/ProductList.vue";
import ProductAdd from "./components/ProductAdd.vue";

export default {
  name: "app",
  components: {
    ProductList, ProductAdd
  },
  data() {
    return {
      products: []
    }
  },
  mounted() {
    this.getProducts()
  },
  methods: {
    async getProducts() {
      const result = await fetch('http://localhost:3000/products')
      const data = await result.json()
      this.products = data;
    },
    async deleteProduct(product) {
      await fetch('http://localhost:3000/products/'+product.id, {
        method:'DELETE'
      })
      this.products = this.products.filter(
        productToFilter=>productToFilter.id!==product.id
      )
    },
    async updateProduct(product) {
      const result = await fetch('http://localhost:3000/products/'+product.id, {
        method: 'PUT',
        body: JSON.stringify(product),
        headers:{"Content-Type":"application/json"}
      })
      const updatedProduct = await result.json()
      this.products = this.products.map(product=>product.id===updatedProduct.id?updatedProduct:product)

      },
    async addProduct(product) {
      const result = await fetch('http://localhost:3000/products', {
        method: 'POST',
        body: JSON.stringify(product),
        headers:{"Content-Type":"application/json"}
      })

      const newProduct = await result.json()
      this.products = [...this.products, newProduct]
    }
  }
}
</script>

<style>
#app {
  
 margin-top: 20px;
  color: rgb(0, 0, 0);
  display: flex;
  padding: 20px;
  flex-direction: column;
  width: 100%;
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  
}
</style>
