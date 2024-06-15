<template>
    <div class="container">
       <Card
        v-for="(card, index) in cards" 
        :key="card.title"
        :title="card.title"
        :img="card.img"
        :description="card.description"
        :color="card.color"
        @change-color="changeColor($event, index)"
        >
    </Card>
    </div>
</template>

<script setup>
    const cards = ref([
        {title: "Street", img: "https://www.w3schools.com/html/img_chania.jpg", description: "New street in israel", color: "red"},
        {title: "Boy", img: "https://www.w3schools.com/html/img_girl.jpg", description: "Beautiful clothes for the holiday", color: "green"},
        {title: "House", img: "https://www.w3schools.com/html/pic_trulli.jpg", description: "A spectacular house in Thailand", color: "orange"},
    ])

    const changeColor = (color, index) => {
     cards.value[index].color = color
    }
</script>

<style scoped>
.container {
    display: flex;
    gap: 1rem;
}

</style>