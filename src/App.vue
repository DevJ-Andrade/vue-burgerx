<template>
  <div>
    <Navbar :logo="logo_src" :alt="app_name" />

    <router-view/>


   <!-- <Footer /> -->
    
  </div>
</template>

<script>
import Navbar from'./components/Navbar.vue'
// import Footer from './components/Footer.vue'
export default {
  components: {
    Navbar,
 //  Footer
  },
  data() {
    return {
      logo_src: "/img/logo.png",
      app_name: "Make Your Burger"
    }
  }
}
</script>

<style>
* {

  font-family: Helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

#nav {
    background-color: #222;
    border-bottom: 4px solid #111;
    padding: 15px 50px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
}

#nav #logo-url {
    margin:auto;
    margin-left: 0;
}

#logo {
    width: 40px;
    height: 40px;
}

#nav a{
    color: #FCBA03;
    text-decoration: none;
    margin: 12px;
    transition: .5s;
}

#nav a:hover {
    color: #FFF;
}

.main-container {
  margin: 50px;
  min-height: 250px;
}

h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}


</style>
