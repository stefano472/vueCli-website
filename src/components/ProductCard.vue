<template>
<div class="card">
    <div v-if="item.onSale.length > 1" class="sale flex-row font-09" >Sale!</div>

    <div class="img-container">
        <img :src="item.imgPath" :alt="item.name">
        <div class="text-hover">
            <div class="flex-column align">
                <div class="star font-07">
                    <font-awesome-icon v-for="number in item.rating" 
                            :key="'fillStar:' + number"  
                            icon="fa-solid fa-star" 
                    />
                    <font-awesome-icon v-for="number in (5 - item.rating)" 
                            :key="'emptyStar:' + number" 
                            icon="fa-regular fa-star" 
                    /> 
                </div>
                <p class="font-09">ADD TO CART / QUICK VIEW</p>
            </div>
        </div>
    </div>

    <h3>{{item.name}}</h3>

    <p v-if="item.onSale.length === 0">{{item.price}}</p>

    <p v-else class="on-sale flex-row">
        <span class="font-07">{{item.price}}</span> 
        <span>{{item.onSale}}</span>
    </p>
</div>
</template>

<script>
export default {
    props: {
        item: Object
    }
}
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;

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
    z-index: 5;
}

h3 {
padding-top: 1rem;
cursor: pointer;
    &:hover {
        color: $text-subtitle;
    }
}

.card > p {
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

</style>