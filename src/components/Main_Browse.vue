<template>
  <div class="container">

    <div class="title">
      <h2 class="font-25">Browse by category</h2>
      <p>
        Augue purus et, tincidunt condimentum mauris. At nibh rutrum mi in. Nisi, vitae interdum eleifend dui, consequat nulla rhoncus dictum. Viverra.
      </p>
    </div>
    <div class="categories">
      <ul class="flex-row">
        <li v-for="item in arrayTypeOfProducts" :key="item.name">
          <img :src="productImg(item.name)" :alt="item.name">
          <div>
            {{item.name}} ({{item.items}})
          </div>
        </li>
      </ul>
    </div>

    <div class="dog-food">
      <ul class="flex-row">
        <li v-for="item in arrayFood" :key="item.name">
          <h2 class="font-25">{{item.brandName}}</h2>
          <p>{{item.definition}}</p>
          <img :src="foodImg(item.brandName)" :alt="item.name">
          <button class="btn btn__secondary">Shop {{item.name}}</button>
        </li>
      </ul>
    </div>

    <div class="banner">
      <p class="font-09">FIND THE BEST ANIMAL SUPPLIES</p>
      <h1 class="font-30">New arrivals weekly</h1>
      <button class="btn btn__primary">Learn more about us</button>
    </div>

    <div class="item-loved">
      <div class="description-box flex-row">
        <div class="text">
          <p>All-time best sellers</p>
          <h2 class="font-25">Items everyone loves</h2>
        </div>
        <div class="button">
          <button v-if="!toggleAllProduct" 
                  @click="functionToggle" 
                  class="btn btn__secondary"
          >
            View all product
          </button>
          <button v-if="toggleAllProduct" 
                  @click="functionToggle" 
                  class="btn btn__secondary"
          >
            View top-rated product
          </button>
        </div>
      </div>
      <ul class="flex-row">
        <li v-for="item in arrayItemLoved" :key="item.name">
          <!-- <div v-if="item.onSale.length > 1" class="sale flex-row font-09" >Sale!</div> -->
          <product-card :item="item"></product-card>
          <!-- <div class="img-container">
            <img :src="item.imgPath" :alt="item.name">
            <div class="text-hover">
              <div>
                <font-awesome-icon v-for="number in item.rating" 
                          :key="'fillStar:' + number"  
                          icon="fa-solid fa-star" 
                          class="fillStar" 
                  />
                  <font-awesome-icon v-for="number in (5 - item.rating)" 
                          :key="'emptyStar:' + number" 
                          icon="fa-regular fa-star" 
                  /> 
              </div>
              <p>ADD TO CART / QUICK VIEW</p>
            </div>
          </div> -->
          <!-- <h3>{{item.name}}</h3>
          <p v-if="item.onSale.length === 0">{{item.price}}</p>
          <p v-else class="on-sale flex-row">
            <span class="font-07">{{item.price}}</span> 
            <span>{{item.onSale}}</span>
          </p> -->
        </li>
      </ul>
    </div>
    
  </div>
</template>

<script>
import arrayProducts from "@/data/products.json"

import ProductCard from '@/components/ProductCard'


export default {
    name: "MainBrowse",
    components: { ProductCard },
    data() {
      return {
        arrayProducts,
        toggleAllProduct: false
      }
    },
    computed: {
      arrayTypeOfProducts() {
        let count = {};
        this.arrayProducts.forEach(e => {
          count[e.type] = (count[e.type] || 0) + 1;
        });
        const array = Object.keys(count)
                   .map((key) => ({name: key, items: count[key]}))
        return array;
      },
      arrayFood() {
        const foodArray = this.arrayProducts.filter(e => {
            return e.definition.includes("dog")
          })
          console.log(foodArray)
        return foodArray
      },
      arrayItemLoved() {
        if (this.toggleAllProduct) {
          return this.arrayProducts
        }
        return this.arrayProducts.filter(e => e.allTimeSell >= 159)
      }
    }, 
    methods: {
      productImg(path) {
        return require(`@/assets/product-${path.toLowerCase()}.jpg`)
      },
      foodImg(path) {
        return require(`@/assets/food-transparent-${path.toLowerCase()}.png`)
      },
      functionToggle() {
        this.toggleAllProduct = !this.toggleAllProduct
      }
    }

}
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;

.title {
  width: 50%;
  margin: 5.5rem auto 3.5rem;
  text-align: center;
  p {
    line-height: 1.5;
    padding-top: 1rem;
    font-weight: 600;
  }
}
.categories {
  ul {
    gap: 0.7rem;
    li {
      text-align: center;
      flex-basis: calc(100% / 4 - 0.7rem * 3 / 4);
      img {
        cursor: pointer;
        border-radius: 2px;
        width: 100%;
        padding-bottom: 1rem;
      }
    }
  }
}
.dog-food {
  margin: 6rem auto;
  ul {
    gap: 1rem;
    li {
      border-radius: 5px;
      padding: 4rem;
      background: $bg-brand;
      background-image: url("@/assets/bg-transparent-3.png");
      background-repeat: repeat-x;
      background-position: top;
      background-size: 60%;
      text-align: center;
      flex-basis: calc(100% / 3 - 1rem * 2 / 3);
      transition: 0.5s;
      &:hover {
        transform: scale(1.05);
        box-shadow: 0 0 25px 5px rgb(0 0 0 / 20%);
        opacity: 0.955;
      }
      h2 {
        color: $text-title;
      }
      p {
        color: $text-subtitle;
        padding-top: 1rem;
      }
      img {
        width: 100%;
        aspect-ratio: 1/1;
      }
    }
  }
}
.banner {
  background-image: url("@/assets/banner-3-2x-scaled.jpg");
  background-position: center;
  background-size: cover;
  background-blend-mode: multiply;
  background-color: rgba($color: #000000, $alpha: 0.3);
  color: $text-title;
  text-align: center;
  p {
    padding: 9rem 0 2rem;
    font-weight: 600;
  }
  button {
    margin: 2rem 0 9rem;
  }
}
.item-loved {
  margin: 6rem auto 3.75rem;
  .description-box {
    margin-bottom: 3rem;
    justify-content: space-between;
    p {
      color: $text-tertiary;
      padding-bottom: 1rem;
      font-weight: 600;
    }
  }
  ul {
    flex-wrap: wrap;
    gap: 0.7rem;
    li {
      position: relative;
      text-align: center;
      flex-basis: calc(100% / 4 - 0.7rem * 3 / 4);
    }
  }
}
</style>