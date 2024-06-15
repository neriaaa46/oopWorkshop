<template>
    <div class="container">
        <div>
            <a href="https://vuetifyjs.com/en/getting-started/installation/" target="_blank">Installation</a>
            <a href="https://vuetifyjs.com/en/features/theme/" target="_blank">Theme (colors)</a>
            <a href="https://vuetifyjs.com/en/components/all/#containment" target="_blank">Components</a>
        </div>

        <div>
            <v-btn color="primary">primary</v-btn>
            <v-btn color="surface">surface</v-btn>
            <v-btn color="secondary">secondary</v-btn>
            <v-btn color="error">error</v-btn>
            <v-btn color="info">info</v-btn>
            <v-btn color="success">success</v-btn>
            <v-btn color="warning">warning</v-btn>
        </div>

       <v-alert
        text="Lorem ipsum dolor sit amet consectetur adipisicing elit. Commodi, ratione debitis quis est labore voluptatibus! Eaque cupiditate minima, at placeat totam, magni doloremque veniam neque porro libero rerum unde voluptatem!"
        title="Alert title"
        type="success">
       </v-alert>

        <v-sheet width="300">
            <v-form fast-fail @submit.prevent>
            <v-text-field
                v-model="firstName"
                :rules="firstNameRules"
                label="First name"
            ></v-text-field>

            <v-text-field
                v-model="lastName"
                :rules="lastNameRules"
                label="Last name"
            ></v-text-field>

            <v-btn class="mt-2" type="submit" block>Submit</v-btn>
            </v-form>
        </v-sheet>
    </div>
</template>

<script>
  export default {
    data: () => ({
      firstName: '',
      firstNameRules: [
        value => {
          if (value?.length > 2) return true

          return 'First name must be at least 2 characters.'
        },
      ],
      lastName: '123',
      lastNameRules: [
        value => {
          if (/[^0-9]/.test(value)) return true

          return 'Last name can not contain digits.'
        },
      ],
    }),
  }
</script>

<style scoped>
.container {
    padding: 1rem;
    display: flex;
    flex-direction: column;
    gap: 15px;
}

a {
    display: block;
    margin: 1rem;
    text-decoration: underline;
    color: blue;
}
</style>
