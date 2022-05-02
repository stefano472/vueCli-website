<template>
  <footer>

    <div class="flex-column">
      <div class="top-footer container flex-row font-09">
        <div class="links links__logo flex-column">
          <img src="@/assets/mobile-light-pet-logo-2x.png" alt="logo-img">
          <span>1234 Avada Avenue Avadaville</span>
          <span>info@your-company.com</span>
          <span>Call us: (+1) 2345678</span>
        </div>

        <div class="links links__shop">
          <h2 class="font-12">Shop by brand</h2>
          <ul>
            <li>Bed</li>
            <li>Food</li>
            <li>Toys</li>
            <li>Transport</li>
          </ul>
        </div>

        <div class="links links__useful-link">
          <h2 class="font-12">Useful links</h2>
          <ul>
            <li>My account</li>
            <li>Orders</li>
            <li>Checkout</li>
            <li>Cart</li>
          </ul>
        </div>

        <div class="links links__subscribe flex-column">
          <h2 class="font-12">Subscribe to our newsletter</h2>
          <input v-model="inputEmail" type="text" class="input" placeholder="Insert your email ...*">
          <button @click="getInput" class="btn btn__secondary">Subscribe</button>  
        </div>
      </div>

      <div class="navigation container">
        <div class="nav">
          <ul class="flex-row font-09">
            <li v-for="{item} in navbar" :key="item[0] " class="header-item flex-row">
              <a href="#" class="link-item">{{item[0]}}</a>
            </li>
          </ul>
        </div>
        <div class="social flex-row">
          <font-awesome-icon class="font-12" icon="fa-brands fa-facebook-f" />
          <font-awesome-icon class="font-12" icon="fa-brands fa-twitter" />
          <font-awesome-icon class="font-12" icon="fa-brands fa-instagram" />
          <font-awesome-icon class="font-12" icon="fa-brands fa-youtube" />
        </div>
      </div>

      <div class="copyright">
        <p class="font-09">© Copyright 2012 - 2022 | Avada Theme by ThemeFusion | All Rights Reserved | Powered by WordPress</p>
      </div>

    </div>
  </footer>
</template>

<script>
import navbar from "@/data/navbar.json"

export default {
    name: "FooterComponent",
    data() {
      return {
        inputEmail: '',
        navbar
      }
    },
    methods: {
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

footer {
  background: $bg-brand;
  color: $text-title;

  .top-footer {
    padding: 6rem 0 4rem;
    align-items: flex-start;
    gap: 2rem;
    .links{
      flex-basis: calc(25% - 2rem * 3 / 4);
      &__logo {
        img {
          width: 80%;
          padding-bottom: 2rem;
        }
        span ~ span {
          margin-top: 1rem;
        }
      }
      &__shop,
      &__useful-link {
        h2 {
          padding-bottom: 2rem;
        }
        li {
          cursor: pointer;
          &:hover {
            color: $text-subtitle;
          }
          & ~ li {
            margin-top: 1rem;
          } 
        }
      }
      &__subscribe {
        border-radius: 5px;
        background: #273f29;
        background-image: url("@/assets/bg-transparent-3.png");
        padding: 2rem;
        gap: 1rem;
        .input {
          margin: 0.5rem 0;
          border-radius: 2rem;
          height: 2rem;
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
  .navigation {
    padding: 2.75rem 0;
    box-shadow: 0 -1px 0 $bg-search-bar;
    .nav {
      ul {
        justify-content: center;
        .header-item {
          cursor: pointer;
          position: relative;
          padding: 1.25rem;
          color: $text-secondary;
          .link-item {
            font-weight: 600;
            color: $text-secondary;
            text-decoration: none;
          }
          &:hover{
            a {
              color: $text-subtitle;
            }
          }
        }
      }
    }
    .social {
      margin: 1.25rem 0;
      justify-content: center;
      gap: 1rem;
    }
  }
  .copyright{
    padding: 2rem;
    text-align: center;
    background: #000;
  }
}
</style>