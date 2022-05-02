<template>
  <main>
    <Hero />
    <Browse />
    <Interaction />
    <NewProduct />
  </main>
</template>

<script>
import Hero from '@/components/Main_Hero.vue'
import Browse from '@/components/Main_Browse.vue'
import Interaction from '@/components/Main_Interaction.vue'
import NewProduct from '@/components/Main_NewProduct.vue'


export default {
    name: "MainComponent",
    components: {
      Hero,
      Browse,
      Interaction,
      NewProduct
    }

}
</script>

<style lang="scss" scoped>

</style>