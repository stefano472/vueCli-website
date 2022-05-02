<template>
<!-- dipende se voglio utilizzare il display none oppure l'opacity per l'animazione...
con il display non posso fare transition, però al contrario così sono costretto
 a dare un altezza al contenitore -->
<!-- v-show="currentSlide === index" -->
    <div  
        @mouseover="$emit('mouseenter')"
        @mouseleave="$emit('mouseout')"
        :class="index === currentSlide? 'active': ''"
        class="carousel-item flex-column"
    >
        <img :src="userImg(slide.id)" :alt="'avatar-' + slide.id">
        <p>
            <font-awesome-icon class="quote font-30" icon="fa-solid fa-quote-left" />
            <span>{{slide.name}}</span>
        </p>
        <i class="font-09">{{slide.text}}</i>
    </div>
</template>

<script>
export default {
    name: "CarouselItem",
    emits: ['mouseenter', 'mouseout'],
    props: {
        currentSlide: Number,
        index: Number,
        slide: Object
    },
    computed: {
        transitionEffect() {
            return 'slide-in'
        }
    },
    methods: {
        userImg(path) {
        return require(`@/assets/avatar-${path}.jpg`)
      },
    }

}
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;


.carousel-item {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translatex(-50%);
    opacity: 0;
    transition: 500ms opacity ease-in-out;
    &.active {
        opacity: 1;
        z-index: 10;
    }
    // transition-delay: 500ms;
    border-radius: 50%;
    align-items: center;
    justify-content: center;
    margin: 2.5rem auto 3.5rem;
    width: 50%;
    img {
    margin-bottom: 1rem;
    margin-inline: auto;
    border-radius: 50%;
    width: 15rem;
    aspect-ratio: 1/1;
    }
    p {
    position: relative;
    width: fit-content;
    .quote {
        color: $text-subtitle;
        position: absolute;
        top: -2rem;
        left: -4rem;
    }
    }
    i {
        font-weight: 600;
        width: 80%;
        margin-top: 1rem;
        color: $text-subtitle;
    }
}
</style>