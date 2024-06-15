<template>
    <div class="card" @click="changeColor">
        <h1>{{ props.title }}</h1>
        <img :src="props.img" alt="img"></img>
        <p>{{ props.description }}</p>
    </div>
</template>

<script setup>
const props = defineProps(['title', 'img', 'description', 'color'])
const emit = defineEmits(['change-color'])

const changeColor = () => {
    emit("change-color", "gray")
}

</script>

<style scoped>
.card {
    padding: 0.5rem 1rem;
    width: 280px;
    height: 400px;
    box-shadow: 1px 1px 2px 1px gray;
    color: v-bind('props.color');
    margin: 1rem;
    cursor: pointer;
}


img {
    width: 240px;
    height: 260px;
}
</style>