<template>
  <div class="carousel-indicators">
        <button v-for="(item, index) in total" 
            :key="index"
            :class="{ active: currentIndex === index }"
            @click="$emit('switch', index)"
            class="indicator-item"
        ></button>
  </div>
</template>

<script>
export default {
    name: 'CarouselIndicators',
    emits: ['switch'],
    props: {
        total: Number,
        currentIndex: Number
    },
    mounted() {
        console.log()
    }
}
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;

.carousel-indicators {
    position: absolute;
    transform: translateX(-50%);
    left: 50%;
    bottom: 1rem;
    z-index: 10;
    .indicator-item {
        width: 0.6rem;
        height: 0.6rem;
        border: none;
        background: $btn-bg-secondary;
        // opacity: 0.5;
        margin: 0.2rem;
        border-radius: 50%;
        cursor: pointer;
    }
    .active {
        background: $btn-hover-primary;
        // opacity: 1;
    }
}

</style>