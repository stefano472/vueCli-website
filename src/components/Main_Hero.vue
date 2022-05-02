<template>
  <div class="hero">
    <div class="hero__top container flex-row font-09">
      <ul class="flex-row">
        <li >
          <font-awesome-icon icon="fa-regular fa-map" />
          <b>International </b>
          <span>shipping services</span>
        </li>
        <li >
          <font-awesome-icon icon="fa-regular fa-clock" />
          <span>See our </span>
          <b>store hours </b>
          <span>and services</span>
        </li>
        <li >
          <font-awesome-icon icon="fa-solid fa-check" />
          <span>We price match to give you the </span>
          <b>best deals</b>
        </li>
      </ul>
    </div>
    <div class="hero__body">
      <div class="container">
        <div class="wrapper">
          <p class="font-09">FIND THE BEST ANIMAL SUPPLIES</p>
          <h1 class="font-30">We know animals are a part of your family, let us help take care of them</h1>
          <button class="btn btn__primary">Learn more about us</button>
        </div>
      </div>
    </div>
    <div class="hero__bottom flex-row">
      <img src="@/assets/food-transparent-5.png" alt="pet food">
      <span>
        Get $25 OFF your first purchase of our homemade pet food!
      </span>
      <a href="#">Visit the shop</a>
    </div>
  </div>
</template>

<script>
export default {
    name: "HeroComponent"

}
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;

.hero{
  margin-top: 8.25rem;
  color: $text-title;
  background: $bg-brand;
  background-image: url("@/assets/bg-transparent-3.png");
  &__top {
    ul {
      list-style: none;
      justify-content: space-around;
      flex-grow: 1;
      svg {
        padding-right: 0.5rem;
      }
    }
  }
  &__body {
    background-image: url("@/assets/banner-5-2x-scaled.jpg");
    background-position: center;
    background-size: cover;
    background-blend-mode: multiply;
    background-color: rgba($color: #000000, $alpha: 0.3);
    .wrapper {
      width: min(35rem, 100%);
      p {
        padding: 9rem 0 2rem;
        font-weight: 600;
      }
      button {
        margin: 2rem 0 9rem;
      }
    }
  }
  &__bottom {
    align-items: center;
    justify-content: center;
    img {
      height: 8rem;
      padding-top: 1rem;
    }
    span {
      font-weight: 600;
      padding: 1rem;
    }
    a {
      color: $bg-search-bar;
      &:hover {
        color: $text-subtitle;
      }
    }
  }
}

</style>