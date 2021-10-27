<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <router-view/>
  <Footer />
</template>

<script lang="ts">
import Navbar from './components/Navbar.vue'
import Footer from './components/Footer.vue'

export default{
  components: {
    Navbar,
    Footer,
  },
  data(){
    return{
      logo_src: '/img/logo.png',
      app_name: 'make your burguer'
    }
  }
}
</script>