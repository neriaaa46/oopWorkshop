<template>
    <div>
        <div class="menu">
            <p v-for="link in links" :key="link.name">
                <NuxtLink :to="link.link">{{ link.name }}</NuxtLink>
            </p>
            <v-switch @click="toggleTheme" class="switch" label="Dark"></v-switch>
        </div>
        <slot></slot>
    </div>
</template>

<script setup>
import { useTheme } from 'vuetify'

const theme = useTheme()

const links = [
    {name: "Home", link: "/"},
    {name: "Routing", link: "/Users"},
    {name: "Syntax", link: "/Syntax"},
    {name: "Components", link: "/Components"},
    {name: "Form", link: "/Form"},
    {name: "Vuetify", link: "/Vuetify"},
    {name: "ASP.net", link: "/Asp"},
]

function toggleTheme () {
  theme.global.name.value = theme.global.current.value.dark ? 'light' : 'dark'
}
</script>

<style scoped>
.menu {
    background: rgb(59, 59, 188);
    width: 100%;
    height: 50px;
    color: white;
    font-size: 18px;
    display: flex;
    align-items: center;
    padding: 0 0.5rem;
    gap: 1rem
}
p:hover {
    cursor: pointer;
    font-weight: bold;
}
.switch {
    margin: auto 1.5rem;
}
</style>