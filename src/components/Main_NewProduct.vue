<template>
  <div class="container">

    <div class="title">
      <h2 class="font-25">New products arrival</h2>
      <p>Latest products</p>
    </div>

    <ul class="flex-row">
      <li v-for="item in arrayLatestItems" :key="item.name">
        <div v-if="item.onSale.length > 1" class="sale flex-row font-09" >Sale!</div>
        <product-card :item="item"></product-card>
      </li>
    </ul>

  </div>
</template>

<script>
import arrayProducts from "@/data/products.json"

import ProductCard from '@/components/ProductCard'


export default {
    name: "MainNewProduct",
    components: {
      ProductCard
    },
    data() {
      return {
        arrayProducts,
      }
    },
    computed: {
      arrayLatestItems() {
        // if (this.toggleAllProduct) {
        //   return this.arrayProducts
        // }
        return this.arrayProducts.filter(e => e.newProduct)
      }
    }

}
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;

.title {
  margin: 4.75rem auto 3rem;
  text-align: center;
  p{
    color: $text-tertiary;
    padding-top: 1.5rem;
    font-weight: 600;
  }
}
ul {
    margin-bottom: 3.75rem;
    flex-wrap: wrap;
    gap: 1rem;
    li {
      position: relative;
      text-align: center;
      flex-basis: calc(100% / 3 - 1rem * 2 / 3);
      .sale {
        position: absolute;
        top: 0.5rem;
        left: 0.5rem;
        color: $text-title;
        justify-content: center;
        border-radius: 50%;
        width: 3rem;
        height: 3rem;
        background: $btn-bg-secondary;
      }
      h3 {
        padding-top: 1rem;
        cursor: pointer;
        &:hover {
          color: $text-subtitle;
        }
      }
      p {
        color: $text-tertiary;
        margin: 0.7rem auto 1rem;
        &.on-sale {
          justify-content: center;
          gap: 0.2rem;
          span:first-child {
            text-decoration: line-through;
          }
        }
      }
    }
  }
</style>