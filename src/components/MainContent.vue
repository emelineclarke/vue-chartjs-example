<template>
  <div class="container-fluid">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'MainContent',
  props: {
    msg: String
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
</style>
