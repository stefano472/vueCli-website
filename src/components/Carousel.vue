<template>
  <div class="carousel">
        <carousel-item v-for="(slide, index) in Slides" 
                :key="slide.id" 
                :index="index" 
                :currentSlide="currentSlide"        
                :slide="slide"
                @mouseenter="stopSlideTimer"
                @mouseout="startSlideTimer"
        >
        </carousel-item>
        <carousel-indicators 
            :total="Slides.length"
            :currentIndex="currentSlide"
            @switch="switchSlide($event)"
        ></carousel-indicators>
  </div>
</template>

<script>
import Slides from "@/data/testimonials.json"

import CarouselItem from "@/components/CarouselItem";
import CarouselIndicators from '@/components/CarouselIndicators.vue';



export default {
    name: "CarouselComponent",
    components: { 
        CarouselItem ,
        CarouselIndicators
    },
    data() {
        return {
            Slides,
            currentSlide: 0,
            slideInterval: null
        }
    },
    methods: {
        setCurrentSlide(index) {
            this.currentSlide = index
        },
        startSlideTimer() {
            this.stopSlideTimer()
            this.slideInterval = setInterval(() => {
                const index = this.currentSlide < this.Slides.length -1 ? this.currentSlide + 1 : 0;
                this.setCurrentSlide(index)
            }, 3000)
        },
        stopSlideTimer(){
            clearInterval(this.slideInterval)
        },
        switchSlide(index) {
            this.currentSlide = index
            this.startSlideTimer()
        }
    },
    mounted() {
        this.startSlideTimer()
    },
    beforeDestroy() {
        this.stopSlideTimer()
    }

}
</script>

<style lang="scss" scoped>
.carousel {
    position: relative;
    height: 26rem;
}
</style>