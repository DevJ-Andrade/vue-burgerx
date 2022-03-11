<template>  
<div>
  <Banner />

<div class="main-container">
<h1>Make your burger:</h1>
 <BurgerForm />
  </div>
<FooterHome />
</div>
</template>

<script>
import Banner from '../components/Banner.vue'
import BurgerForm from '../components/BurgerForm.vue'
import FooterHome from '../components/FooterHome.vue'

export default {
  name: "Home",
  components: {
    Banner,
    BurgerForm,
    FooterHome
}
}
</script>
