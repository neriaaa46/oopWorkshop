<template>
    <div class="container">
        <h1>TODOS:</h1>
        <h2>Connect with ASP.net backend server</h2>

        <v-sheet class="mt-8" width="300">
            <v-form @submit.prevent>
                <v-text-field
                    v-model="name"
                    variant="solo"
                    label="Enter task name"
                ></v-text-field>

                <v-checkbox
                    v-model="isComplete"
                    label="Is complete ?"
                    color="primary"
                ></v-checkbox>

                <v-btn class="mt-2" @click="submit" color="primary">Submit</v-btn>
            </v-form>
        </v-sheet>


        <h2 class="mt-5">List: </h2>
        <h3 v-if="loading">Loading...</h3>
        <ul v-else class="ml-5">
            <li class v-for="item in todoList" :key="item.id">
                <span>id: {{ item.id }} --- name: {{ item.name }} --- is complete: {{ item.isComplete }}</span>
                <v-icon @click="deleteTask(item.id)" color="primary" class="ml-4" icon="mdi-delete"></v-icon>
            </li> 
        </ul>
    </div>
</template>

<script setup>
    const todoList = ref([])
    const name = ref("")
    const isComplete = ref(false)
    const loading = ref (true)

    const submit = async () => {
        try {
            const res = await $fetch('https://localhost:7094/api/TodoItems', {
                method: 'POST',
                body: {name: name.value, isComplete: isComplete.value}
            })

            getTodoList()

        } catch (error) {
            console.log(error)
        }
    }

    const deleteTask = async (id) => {
        try {
            const res = await $fetch(`https://localhost:7094/api/TodoItems/${id}`, {
                method: 'DELETE',
            })

            getTodoList()

        } catch (error) {
            console.log(error)
        }
    }

    const getTodoList = async () => {
        try {
            todoList.value = await $fetch('https://localhost:7094/api/TodoItems', {
                method: 'GET',
            })

        } catch (error) {
            console.log(error)

        } finally {
            loading.value = false
        }
    }

    onMounted(() => {
        getTodoList()
    })
</script>

<style scoped>
    .container {
        padding: 1rem;
    }
</style>
