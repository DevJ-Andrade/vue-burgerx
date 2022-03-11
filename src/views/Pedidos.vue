<template>
<div>
  <h1>Manage orders:</h1>
<Dashboard />
<Footer />
</div>
</template>

<script>
import Dashboard from '../components/Dashboard.vue'
import Footer from '../components/Footer.vue'

export default {
name:"Pedidos",

components: {
    Dashboard,
    Footer
}
}
</script>

<style scoped>


</style>