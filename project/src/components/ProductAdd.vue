<template>
  <div id="addForm">
    <form @submit.prevent="handleAdd">

        <div class="form-group">
            <label for="id">Id</label>
            <input v-model="product.id" placeholder="ID Otomatik atanmaktadır." readonly type="text" class="form-control" id="id" />
        </div>

        <div class="form-group">
            <label for="categoryId">Kategori</label>
            <input v-model="product.categoryId" type="text" class="form-control" id="categoryId" />
        </div>

        <div class="form-group">
            <label for="productName">Ürün Adı</label>
            <input v-model="product.productName" type="text" class="form-control" id="productName" />
        </div>

        <div class="form-group">
            <label for="quantityPerUnit">Açıklama</label>
            <input v-model="product.quantityPerUnit" type="text" class="form-control" id="quantityPerUnit" />
        </div>

        <div class="form-group">
            <label for="unitPrice">Birim Fiyat</label>
            <input v-model="product.unitPrice" type="text" class="form-control" id="unitPrice" />
        </div>

        <div class="form-group">
            <label for="v">Stok</label>
            <input v-model="product.unitInStock" type="text" class="form-control" id="unitInStock" />
        </div>
        <br/>

        <button type="submit" class="btn btn-success">Ekle</button>

    </form>
  </div>
</template>

<script>


export default {
    name: "product-add",
    data() {
        return {
            product:{id:'',categoryId:'',productName:'',quantityPerUnit:'',unitPrice:'',unitInStock:''}
        }
    },
    methods: {
        handleAdd() {
            this.$emit("add:product", this.product)
        }
    }
};
</script>

<style scoped>

</style>
