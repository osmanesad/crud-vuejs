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
    },
    updateProduct() {
       
    },
    addProduct(product) {
      const newProduct = {...product}
      this.products = [...this.products, newProduct]
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: 10px;
  color: #2c3e50;
  margin-top: 20px;
}
</style>
