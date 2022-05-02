<template>
  <div class="hide-overflow">

    <div class="testimonials">
      <div class="container">
        <h2 class="font-25">User testimonials</h2>
        <Carousel></Carousel>
      </div>
    </div>

    <div class="tips container">

      <div class="newsletter">
        <div class="container">
          <div class="wrapper">
            <h2 class="font-25">Join our newsletter</h2>
            <p class="font-09">Volutpat vel turpis nulla lorem sed semper. Aliquam sagittis sem libero viverra vehicula nullam ut nisl.</p>
            <div class="subscribe flex-row">
              <input v-model="inputEmail" type="text" class="input" placeholder="Insert your email ...*">
              <button @click="getInput" class="btn btn__secondary">Subscribe</button>
            </div>
          </div>
        </div>
      </div>

      <h2 class="font-25">Get the best tips & tricks</h2>
      <p class="subtitle">All-time best sellers</p>
      <ul class="flex-row">
        <li v-for="tips in showTipsTricks" :key="tips.id">
          <div class="img-container">
              <img :src="tipsImg(tips.id)" :alt="'blog:'+ tips.id">
              <div class="text-hover">
                  <div class="flex-column align">
                      <p>{{tips.title}}</p>
                      <p class="font-07">{{tips.type}}</p>
                  </div>
              </div>
          </div>
          <!-- <img :src="tipsImg(tips.id)" :alt="'blog:'+ tips.id"> -->
          <div class="tips-text">
            <p>{{tips.title}}</p>
            <p class="font-07">{{tips.date}}</p>
          </div>
        </li>
      </ul>
      <div class="button">
          <button v-if="!showAllTipsTricks" 
                  @click="showAllTipsTricks = !showAllTipsTricks" 
                  class="btn btn__secondary"
          >
            Read all articles
          </button>
          <button v-if="showAllTipsTricks" 
                  @click="showAllTipsTricks = !showAllTipsTricks" 
                  class="btn btn__secondary"
          >
            Show the latest articles
          </button>
        </div>
      <!-- <button class="btn btn__secondary">read all articles</button> -->

    </div>

    <div class="product">

      <div class="best-product flex-row">
        <div class="banner banner__supplies">
          <p class="font-09">FIND THE BEST ANIMAL SUPPLIES</p>
          <h2 class="font-25">Popular accessories</h2>
          <button class="btn btn__primary">View all toys accessories</button>
        </div>
        <div class="banner banner__food">
          <p class="font-09">FIND THE BEST FOOD</p>
          <h2 class="font-25">New food arrival</h2>
          <button class="btn btn__primary">View all food products</button>
        </div>
      </div>

      <div class="company-feature">
        <ul class="flex-row">
          <li class="flex-column">
            <font-awesome-icon class="font-25" icon="fa-solid fa-truck" />
            <p class="font-09">Free worldwide deliveries</p>
          </li>
          <li class="flex-column">
            <font-awesome-icon class="font-25" icon="fa-regular fa-map" />
            <p class="font-09">Find stores near you</p>
          </li>
          <li class="flex-column">
            <font-awesome-icon class="font-25" icon="fa-solid fa-dollar-sign" />
            <p class="font-09">Best prices guaranteed</p>
          </li>
          <li class="flex-column">
            <font-awesome-icon class="font-25" icon="fa-solid fa-credit-card" />
            <p class="font-09">All credit card accepted</p>
          </li>
        </ul>
      </div>

    </div>

  </div>
</template>

<script>
// import userTestimonials from "@/data/testimonials.json"
import allTipsTrick from "@/data/tips.json"

import Carousel from "@/components/Carousel";

export default {
    name: "MainInteraction",
    data() {
      return {
        allTipsTrick,
        inputEmail: '',
        showAllTipsTricks: false
      }
    },
    components: {
      Carousel,

    },
    computed: {
      showTipsTricks() {
        if (this.showAllTipsTricks) {
          return this.allTipsTrick
        }
        return this.allTipsTrick.slice(0,4)
      }
    },
    methods: {
      
      tipsImg(path) {
        return require(`@/assets/blog-${path}.jpg`)
      },
      getInput() {
        // this.$emit('getUserInput', this.inputEmail),
        console.log(this.inputEmail)
        this.inputEmail = ''
      }
    }

}
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;

.hide-overflow {
  overflow-x: hidden;
}

.testimonials {
  color: $text-title;
  text-align: center;
  background: $bg-brand;
  background-image: url("@/assets/bg-transparent-3.png");
  padding: 4.75rem 0;
}
.tips {
  position: relative;
  text-align: center;
  padding: 23.25rem 0 6rem;
  .newsletter {
    box-shadow: 0 0 25px 5px rgb(0 0 0 / 20%);
    text-align: left;
    z-index: 50;
    position: absolute;
    top: -5rem;
    width: 100%;
    background-image: url("@/assets/banner-7-2x-scaled.jpg");
    background-size: cover;
    background-blend-mode: multiply;
    background-color: rgba($color: #000000, $alpha: 0.02);
    .wrapper {
      width: min(35rem, 100%);
      padding: 4rem 4rem;
      p {
        padding: 1.75rem 0;
        line-height: 1.8;
      }
      .subscribe {
        gap: 1rem;
        .input {
          border-radius: 2rem;
          height: 2rem;
          width: 20rem;
          padding: 0 1rem;
          border: 0;
          background: $bg-search-bar;
          font-weight: 600;
          &::placeholder {
            color: $text-black;
            font-weight: 400;
          }
          &:focus {
            outline: 0;
          }
        }
      }
    }
  }
  .subtitle {
      color: $text-tertiary;
      padding: 1.5rem 0 3rem;
      font-weight: 600;
    }
  ul {
    flex-wrap: wrap;
    margin-bottom: 3rem;
    gap: 2rem;
    li {
      flex-basis: calc(25% - 2rem * 3 / 4);
      .img-container {
          display: flex;
          position: relative;
          cursor: pointer;
          &:hover {
              .text-hover{
                  opacity: 1;
                  z-index: 6;
              }
          }
          img {
              border-radius: 2px;
              width: 100%;
          }
          .text-hover {
              opacity: 0;
              height: 100%;
              width: 100%;
              position: absolute;
              top: 0;
              padding: 2rem;
              color: $text-title;
              background-blend-mode: multiply;
              background-color: rgba($color: #cdb899, $alpha: 0.7);
              transition: 0.3s;
              &>div {
                  height: inherit;
                  justify-content: center;
                  gap: 1rem;
              }
          }
      }

      .tips-text {
        text-align: left;
        padding: 1rem 2rem;
        font-weight: 600;
        p:first-child {
          margin-bottom: 0.5rem;
        }
      }
    }
  }
}
.product {
  color: $text-title;
  background: $bg-brand;
  background-image: url("@/assets/bg-transparent-3.png");
  .best-product {
    .banner {
      width: 50%;
      background-size: cover;
      background-repeat: no-repeat;
      background-position: center;
      background-blend-mode: multiply;
      background-color: rgba($color: #000000, $alpha: 0.3);
      color: $text-title;
      text-align: center;
      transition: 0.5s;
      &:hover{
        // background-size: 150%;
        transform: scale(1.03);
        background-color: rgba($color: #000000, $alpha: 0.6);
        z-index: 10;
      }
      &__supplies {
        background-image: url("@/assets/banner-8-2x.jpg");
      }
      &__food {
        background-image: url("@/assets/banner-9-2x.jpg");
      }
      p {
        padding: 9rem 0 2rem;
        font-weight: 600;
      }
      button {
        margin: 2rem 0 9rem;
      }
    }
  }
  .company-feature {
    padding: 5rem 1.25rem;
    ul {
      justify-content: space-evenly;
      p {
        margin-top: 1rem;
        color: $bg-card;
      }
    }
  }
}
</style>