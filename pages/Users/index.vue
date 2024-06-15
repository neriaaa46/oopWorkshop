<template>
    <div>
        <h1>Users:</h1>
        <div class="users-containers">
            <NuxtLink v-for="user in users" :key="user.name" :to="`/Users/${user.id}`">
                <div class="user-card">
                    <p>Name: {{ user.name }}</p>
                    <p>Email: {{ user.email }}</p>
                    <p>Phone: {{ user.phone }}</p>
                </div>
            </NuxtLink>
        </div>
    </div>
</template>

<script setup>
const users = ref([])

const getUsers = async () => {
    users.value = await $fetch("https://jsonplaceholder.typicode.com/users")
}

onMounted(() => getUsers())

</script>

<style scoped>
.user-card {
    width: 280px;
    box-shadow: 1px 1px 2px 2px gray; 
    border-radius: 15px;
    padding: 1rem 0.5rem;
}
.user-card:hover {
    cursor: pointer;
    box-shadow: 1px 1px 2px 2px blue; 
    transition: 0.5s;
}
.users-containers {
    padding: 1rem;
    display: flex; 
    flex-wrap: wrap;
    row-gap: 20px;
    column-gap: 10px;
}

</style>