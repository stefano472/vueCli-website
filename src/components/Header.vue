<template>
  <header>
    <div class="top-header container flex-row">
      <a href="#" class="flex-row">
        <img src="@/assets/dark-pet-logo.png" alt="logo">
      </a>
      <div class="search-bar flex-row">
        <button @click="getInput" class="submit">
          <font-awesome-icon icon="fa-solid fa-magnifying-glass" />
        </button>
        <input v-model="inputSearch" type="text" class="input" placeholder="Search...">
      </div>
      <div class="question">
        <b>Questions? </b>
        <span>Call us: 1.800.123.4567</span>
      </div>
      <div class="icons flex-row">
        <font-awesome-icon icon="fa-solid fa-bag-shopping" />
        <font-awesome-icon icon="fa-solid fa-user-large" />
      </div>
    </div>
    <div class="bottom-header">
      <ul class="flex-row font-09">
        <li v-for="({active, item}, index) in arrayMenuList" :key="item[0] " class="header-item flex-row">
          <a href="#" @click="changeActiveStatus(index)" :class="{active}" class="link-item">{{item[0]}}</a>
          <font-awesome-icon v-if="item[1]" :class="{active}" class="chevron font-07" icon="fa-solid fa-chevron-down" />
          <ul v-if="item[1]" class="dropdown-menu">
            <li v-for="(menuItem, index) in item[1]" :key="menuItem + index" class="flex-column">
              <a href="#">{{menuItem}}</a>
            </li>
          </ul>
        </li>
      </ul>
    </div>
    <div class="advertising flex-column font-07">
      <div class="card flex-column">
        <div class="toggle-icon">
          <img src="@/assets/demos.svg" alt="" class="regular">
          <img src="@/assets/demos.svg" alt="" class="transform">
        </div>
        <p>Demos</p>
      </div>
      <div class="card flex-column">
        <div class="toggle-icon">
          <img src="@/assets/on-sale.svg" alt="" class="regular">
          <div class="transform flex-row">
            <font-awesome-icon icon="fa-solid fa-dollar-sign" />
            <span class="font-12">39</span>
          </div>
        </div>
        <p>Buy Now</p>
      </div>
    </div>
  </header>
</template>

<script>
import arrayMenuList from "@/data/navbar.json"

export default {
    name: "HeaderComponent",
    data() {
      return {
        arrayMenuList,
        inputSearch: ''
      }
    },
    methods: {
      changeActiveStatus(i) {
        this.arrayMenuList.forEach((item, index) => {
            item.active = (i===index)
        })
      },
      getInput() {
        console.log(this.inputSearch),
        // this.$emit('getUserInput', this.inputSearch),
        this.inputSearch = ''
      }
    }
}

</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;


header {
  --size: 2.2rem;
  width: 100%;
  position: fixed;
  z-index: 1000;
  top: 0;
  background: $bg-primary;
  .top-header{
    justify-content: space-between;
    img {
      height: var(--size);
    }
    .search-bar {
      border-radius: var(--size);
      background: $bg-search-bar;
      height: var(--size);
      padding: 0.1rem;
      .submit {
        cursor: pointer;
        border: 0;
        border-radius: 50%;
        background: $btn-bg-secondary;
        width: var(--size);
        height: var(--size);
        color: $bg-search-bar;
        &:hover {
          color: $text-black
        }
      }
      .input {
        width: 15rem;
        padding: 0 1rem;
        border: 0;
        background: transparent;
        font-weight: 600;
        &::placeholder {
          font-weight: 400;
          color: $text-black;
        }
        &:focus {
          outline: 0;
        }
      }
    }
    .icons {
      gap: 1rem;
      &>* {
        cursor: pointer;
        width: calc(var(--size) / 1.8);
        height: calc(var(--size) / 1.8);
        &:hover {
          color: $text-subtitle;
        }
      }
    }
  }
  .bottom-header {
    box-shadow: 0 -1px 0 $bg-search-bar;
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
        .active {
          color: $text-primary;
        }
        .chevron {
          margin-left: 0.4rem;
        }
        &:hover{
          color: $text-primary;
          a {
            color: $text-primary;
          }
          .dropdown-menu {
            display: block;
          }
        }
      }
      .dropdown-menu {
        display: none;
        position: absolute;
        top: 3.55rem;
        left: 0;
        li {
          background: $bg-primary;
          width: 12rem;
          padding: 1rem 1.25rem;
          a{
            font-weight: 600;
            text-decoration: none;
            color: $text-primary;
          }
          &:hover {
            background: $btn-bg-secondary;
            a {
              color: $text-title;
            }
          }
        }
        li ~ li {
          box-shadow: 0 -1px 0 $bg-search-bar;
        }
      }
    }
  }
  .advertising {
    position: fixed;
    top: 9rem;
    right: 1rem;
    gap: 0.3rem;
    .card {
      font-weight: 600;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      overflow: hidden;
      width: calc(var(--size) * 1.8);
      height: calc(var(--size) * 1.8);
      border-radius: 5px;
      gap: 0.2rem;
      background: $bg-primary;
      box-shadow: 0 0 25px 5px rgb(0 0 0 / 20%);
      .toggle-icon {
        position: relative;
        height: calc(var(--size) * 0.8) ;
        width: calc(var(--size) * 0.8);
        .regular {
          position: absolute;
          top: 0;
          filter: invert(13%) sepia(53%) saturate(402%) hue-rotate(76deg) brightness(96%) contrast(90%);
          transition: transform .2s cubic-bezier(.21,.6,.35,1);
        }
        .transform {
          position: absolute;
          top: 0;
          transform: translateX(4rem);
          filter: invert(65%) sepia(16%) saturate(704%) hue-rotate(81deg) brightness(94%) contrast(87%);
          transition: transform .2s cubic-bezier(.21,.6,.35,1);
        }
      }
      &:hover {
        .regular {
          transform: translateX(-4rem);
        }
        .transform {
          transform: translateX(0rem);
        }
        p {
          color: $text-subtitle;
        }  
      }
    }
  }
}
</style>