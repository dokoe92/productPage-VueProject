<template>
    <div class="circle" @mouseover="chooseColor" :index="index"></div>
</template>


<script setup>

    const emits = defineEmits(["selectColor"])
    const props = defineProps(["index"])

    function chooseColor() {
        const index = props.index
        emits("selectColor", index)
    }

</script>


<style scoped>
    .circle {
        width: 2rem;
        height: 2rem;
        border: 1px solid black;
        border-radius: 50px;
        
    }


</style>