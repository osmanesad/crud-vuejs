<template>
    <div>
        <!-- Mutlaka div ile başlamak iyidir. -->

        <h3>Stok Listesi</h3>

        <p v-if="products.length == 0">Stok'ta ürün bulunmamaktadır.</p>
        <table v-else class="table table-bordered">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>ürün Adı</th>
                    <th>Kategori</th>
                    <th>Ürün Açıklama</th>
                    <th>Birim Fiyat</th>
                    <th>Stok</th>
                    <th></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="product in products" :key="product.id">
                    <td v-if="updateId === product.id">
                        <input v-model="product.id" type="text" class="form-control" id="id" />
                    </td>
                    <td v-else>{{ product.id }}</td>

                    <td v-if="updateId === product.id">
                        <input v-model="product.productName" type="text" class="form-control" id="productName" />
                    </td>
                    <td v-else>{{ product.productName }}</td>

                    <td v-if="updateId === product.id">
                        <input v-model="product.categoryId" type="text" class="form-control" id="categoryId" />
                    </td>
                    <td v-else>{{ product.categoryId }}</td>

                    <td v-if="updateId === product.id">
                        <input v-model="product.quantityPerUnit" type="text" class="form-control"
                            id="quantityPerUnit" />
                    </td>
                    <td v-else>{{ product.quantityPerUnit }}</td>

                    <td v-if="updateId === product.id">
                        <input v-model="product.unitPrice" type="text" class="form-control" id="unitPrice" />
                    </td>
                    <td v-else>{{ product.unitPrice }}</td>

                    <td v-if="updateId === product.id">
                        <input v-model="product.unitInStock" type="text" class="form-control" id="unitInStock" />
                    </td>
                    <td v-else>{{ product.unitInStock }}</td>

                    <td v-if="updateId !== product.id">
                        <button class="btn btn-sm btn-primary" @click="handleUpdate(product)">
                            Güncelle
                        </button>
                        <button class="btn btn-sm btn-danger" @click="handleDelete(product)">
                            Sil
                        </button>
                    </td>
                    <td v-else>
                        <button class="btn btn-sm btn-primary" @click="handleSave(product)">
                            Kaydet
                        </button>
                        <button class="btn btn-sm btn-danger" @click="updateId=null">
                            İptal
                        </button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: "product-list",
    data() {
        return { updateId: null };
    },
    props: {
        products: Array,
    },
    methods: {
        handleDelete(product) {
            this.$emit("delete:product", product);
        },
        handleUpdate(product) {
            this.updateId = product.id;
        },
        handleSave(product) {
            this.$emit("update:product", product)
            this.updateId = null
        }
    },
};
</script>

<style scoped>

</style>
