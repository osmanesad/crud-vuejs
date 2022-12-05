<template>
  <!-- Buraya HelloWorld.veu içerisinde "template" kısmında ne yaptıysam oonu çağırıyor.  -->
  <div id="app">
    <ProductList @delete:product="deleteProduct"  :products="products"/> <!-- Eyy ProductList eğer olurda bana bir event yollarsan -> @delete:product="" -->
  </div>
</template>

<script>
import ProductList from "./components/ProductList.vue";

export default {
  name: "app",
  components: {
    ProductList
  },
  data() {
    return {
      products: [
        {id: 1,categoryId: 1, productName: "A4 Fotokopi Kağıdı", quantityPerUnit: "CopierBon 80gr Fotokopi kağıdı." /* Ürün açıklaması */, unitPrice: 470, unitInStock: 20},
        {id: 2, categoryId: 1, productName: "Pensan Büro Kalemi", quantityPerUnit: "Mavi ince uçlu tükenmez kalem" /* Ürün açıklaması */, unitPrice: 45, unitInStock: 13},
        {id: 3, categoryId: 2, productName: "AYT Soru Bankası", quantityPerUnit: "AYT Sayısal bölümü tüm dersler soru bankası" /* Ürün açıklaması */, unitPrice: 138, unitInStock: 34}
      ]
    }
  },
  methods: {
    deleteProduct(product) {
      this.products = this.products.filter(
        productToFilter=>productToFilter.id!==product.id
      )
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
