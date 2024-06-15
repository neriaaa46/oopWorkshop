<template>
    <div>
        <h1>User id - {{ id }}</h1>
        <div class="user-card">
            <p>Name: {{ user.name }}</p>
            <p>Email: {{ user.email }}</p>
            <p>Phone: {{ user.phone }}</p>
            <p>Address: {{ user.address?.city }} - {{ user.address?.street }}</p>
            <p>Website: {{ user.website }}</p>
        </div>
    </div>
</template>

<script setup>
const route = useRoute()
const id = ref(route.params.id)
const user = ref({})

const getUser = async () => {
    user.value = await $fetch(`https://jsonplaceholder.typicode.com/users/${id.value}`)
}

onMounted(() => getUser())
</script>

<style scoped>
.user-card {
    margin: 1rem;
    width: 300px;
    box-shadow: 1px 1px 2px 2px gray; 
    border-radius: 15px;
    padding: 0.3rem 0.5rem;
}
</style>