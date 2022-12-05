<template>
  <div class="hello">
   <h3 class="alert alert-danger">{{ msg }}</h3> <!-- Burada ne istersem yapabilrim. HTML koduyla from gibi. -->
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String /* msg = message */
  }
}
</script>


<style scoped>

</style>
