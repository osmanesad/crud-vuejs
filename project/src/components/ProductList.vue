<template>
    <div> <!-- Mutlaka div ile başlamak iyidir. -->

        <h3> Product List</h3>

        {{products.length}}

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