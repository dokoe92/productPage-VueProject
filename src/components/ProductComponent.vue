<template>
    <div class="product-container">
        <div class="product-left-side">
            <h1>{{ product.name }}</h1>
            <img :src="productImage" alt=""> 
        </div>
        <div class="product-right-side">
            <h2>Product description</h2>
            <p> {{ productDescription }}</p>
            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quo, explicabo obcaecati eos beatae earum sapiente consequatur voluptatem excepturi facere in?</p>
            <p v-if="checkStock">Available</p>
            <p v-else>Currently not in stock</p>
            <div class="select-color">
                <ColorChanger v-for="(color, index) in product.colors" :key="color.id" :style="{backgroundColor: color.color}" :index="index" @selectColor="selectColor"/>
                <p>Select your favorite color!</p>
            </div>
            <ButtonComponent  class="btn-order" :class="{disabledButton: !checkStock}" />
        </div>
    </div>
    <ReviewField></ReviewField>
</template>

<script setup>
    import { ref, computed } from "vue"
    import ColorChanger from "./ColorChanger.vue"
    import ButtonComponent from "./ButtonComponent.vue"
    import ReviewField from "./ReviewField.vue"
    
    const product = ref({
        name: "Socks",
        colors: [
            {
                id: 0,
                color: "blue",
                quantity: 5,
                image: "public/images/socks_blue.jpg",
                description: "Beautiful blue socks keep you warm and cozy",
                onSale: true
            },
            {
                id: 1,
                color: "green",
                quantity: 0,
                image: "public/images/socks_green.jpg",
                description: "Beautiful green socks keep you warm and cozy",
                onSale: false
            }
        ]
    })

    const selectedItem = ref("0")

    function selectColor(event) {
         selectedItem.value = event;
    }


    const productImage = computed(() => {
        return product.value.colors[selectedItem.value].image;
    })

    const productDescription = computed(() => {
        return product.value.colors[selectedItem.value].description
    })

    const checkStock = computed(() => {
        if (product.value.colors[selectedItem.value].quantity > 0) {
            return true
        } else {
            return false
        }
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
        width: 20vw;
    }

    .select-color {
        display: flex;
        align-items: center;
    }

    .select-color p:first-of-type {
        margin-left: 1rem;
    }




</style>