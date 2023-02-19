<template>
    <form action="" class="review-container">
        <input type="text" name="username" placeholder="Enter name">
        <input type="number" name="rating" placeholder="Enter rating" min="1" max="5">
        <textarea name="review" placeholder="Enter review"></textarea>
        <input type="submit">
    </form>


</template>


<script setup>


</script>


<style scoped>
    .review-container {
        display: flex;
        flex-direction: column;
        width: 20vw;
        gap: 1rem;
        border: 1px solid black;
        margin-top: 1rem;
    }


</style>