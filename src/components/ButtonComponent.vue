<template>
    <button  :class="props.class" @click="order">Order now</button>

</template>


<script setup>
    const props = defineProps(["class"])

    function order() {
        console.log(props.class)
    }

</script>


<style scoped>
    .btn-order {
        padding: 0.5rem;
        width: 10rem;
        margin-top: 1rem;
        border-radius: 5px;
        border-style: none;
        box-shadow: 1px 1px;
        background-color: lightblue;
        font-weight: bold
    }

    .disabledButton{
        background-color: gray;
        cursor: not-allowed
    }
    

    .btn-order:active {
        box-shadow: 0px 0px;
        background-color: rgba(58, 105, 121, 0.74);
    }

</style>