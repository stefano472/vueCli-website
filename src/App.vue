<template>
  <div id="app">

    <Header />
    <Main />
    <Footer />
    
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import Footer from './components/Footer.vue'
import "@fontsource/raleway"
import "@fontsource/raleway/600.css"
import "@fontsource/libre-bodoni"
import "@fontsource/libre-bodoni/700.css"


export default {
  name: 'App',
  components: {
    Header,
    Main,
    Footer
  }
}
</script>

<style lang="scss">
@use '@/style/style';
@use '@/style/variables' as *;

#app {
  scroll-behavior: smooth;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  // header {
  //   color: $text-title;
  // }
}
</style>
