<template>
    <div class="product-container">
        <div class="product-left-side">
            <h1>{{ products.name }}</h1>
            <img :src="products.image" alt=""> 
        </div>
        <div class="product-right-side">
            <h2>Product description</h2>
            <h3> {{ products.colors[0].description }}</h3>
            <p v-if="products.colors[0].inStock">Available</p>
            <p v-else>Currently not in stock</p>
            <div class="select-color">
                <ColorChanger v-for="color in products.colors" :key="color.id" :style="{backgroundColor: color.color}" />
                <p>Select your favorite color!</p>

            </div>

        </div>
    </div>
</template>

<script setup>
    import { ref } from "vue"
    import ColorChanger from "./ColorChanger.vue"
    
    const products = ref({
        name: "Socks",
        image: "public/images/socks_blue.jpg",
        colors: [
            {
                id: 0,
                color: "blue",
                quantity: 5,
                image: "public/images/socks_blue.jpg",
                description: "Beautiful blue socks keep you warm and cozy",
                inStock: true,
                onSale: true
            },
            {
                id: 1,
                color: "green",
                quantity: 10,
                image: "public/images/socks_green.jpg",
                description: "Beautiful green socks keep you warm and cozy",
                inStock: false,
                onSale: false
            }
        ]
    })

</script>

<style scoped>
    .product-container {
        display: flex;
    }

    .product-left-side img{
        width: 20rem;
        height: 20rem;
    }

    .product-left-side h1 {
        text-align: center;
    }

    .product-right-side {
        margin-top: 2rem;
        margin-left: 1rem;
    }

    .select-color {
        display: flex;
        align-items: center;
    }

    .select-color p:first-of-type {
        margin-left: 1rem;
    }


</style>