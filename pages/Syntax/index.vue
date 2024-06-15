<template>
    <div class="container">
        <h1>State: </h1>
        <button @click="count1++">Count1: {{ count1 }}</button>
        <button @click="count2++">Count2: {{ count2 }}</button>


        <h1>Directives: </h1>

        <h2>V-IF:</h2>

        <p v-if="color == 'green'">if color == 'green'</p>
        <p v-else-if="color == 'red'">else if color == 'red'</p>
        <p v-else-if="color == 'blue'">else if color == 'blue'</p>
        <p v-else>else</p>

        <select v-model="color">
            <option disabled value="">Please choose color</option>
            <option>green</option>
            <option>red</option>
            <option>blue</option>
            <option>yellow</option>
        </select>



        <h2>V-SHOW:</h2>

        <p v-show="color2 == 'green'">if color == 'green'</p>
       
        <select v-model="color2">
            <option disabled value="">Please choose color</option>
            <option>green</option>
            <option>red</option>
        </select>


        <h2>V-FOR:</h2>
        <ul>
            <li v-for="user in users" :key="user.firstName">{{ user.firstName }} {{ user.lastName }}</li>
        </ul>


        <h1>Hooks: </h1>

        <h2>onMounted: </h2>
        <p>{{ user }}</p>


        <h2>computed:</h2>
        <ol>
            <li v-for="user in usersStartWithN" :key="user.firstName">{{ user.firstName }} {{ user.lastName }}</li>
        </ol>

        <h2>watch:</h2>
        <button @click="count3++">Count3: {{ count3 }}</button>
    </div>
</template>

<script setup>
const count1 = 0 
const count2 = ref(0)

const color = ref("green")
const color2 = ref("green")

const users = [
    {firstName: "Neria", lastName: "Sivan"},
    {firstName: "David", lastName: "Goor"},
    {firstName: "Ela", lastName: "Peper"},
    {firstName: "Nurit", lastName: "Pip"},
]


const user = ref("Ori")
onMounted(()=> {
    user.value = "Dudu"
})

const usersStartWithN = computed(()=> users.filter(user => user.firstName[0] === "N"))

const count3 = ref(0)

watch(count3, (newVal, oldVal) => {
    alert(`new val: ${newVal}, old val: ${oldVal}`)
})

</script>

<style scoped>
.container {
    padding: 1rem
}

ul, ol {
    margin-left: 1.5rem
}

h1 {
    margin-top: 0.4rem;
}

h2 {
    margin-top: 1.2rem;
}
</style>