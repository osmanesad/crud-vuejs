<template>
    <div> <!-- Mutlaka div ile başlamak iyidir. -->

        <h3> Product List</h3>

        <p v-if="products.length==0">Stok'ta ürün bulunmamaktadır.</p>
        <table class="table table-bordered">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>ürün Adı</th>
                    <th>Kategori</th>
                    <th>Ürün Açıklama</th>
                    <th>Birim Fiyat</th>
                    <th>Stok</th>
                </tr>
            </thead>
            <tbody>
                    <tr v-for="product in products" :key="product.id">
                        <td>{{product.id}}</td>
                        <td>{{product.productName}}</td>
                        <td>{{product.categoryId}}</td>
                        <td>{{product.quantityPerUnit}}</td>
                        <td>{{product.unitPrice}}</td>
                        <td>{{product.unitInStock}}</td>
                    </tr>
                </tbody>
        </table>

    </div>
</template>



<script>
export default {
    name:"product-list",
    props:{
        products:Array
    }
};

</script>





<style scoped>

</style>