<template>
    <div class="container">
        <h1>Form</h1>
        <form @submit.prevent="handleSubmit">
            <div>
                <label for="name">Name:</label><br>
                <input placeholder="Enter full name" id="name" v-model="formData.name" type="text">
                <small v-if="errors.name" class="error">{{ errors.name }}</small>
            </div>

            <div>
                <label for="email">Email:</label><br>
                <input placeholder="Enter email" id="email" v-model="formData.email" type="text">
                <small v-if="errors.email" class="error">{{ errors.email }}</small>
            </div>

            <div>
                <label>Gender:</label><br>
                <label><input v-model="formData.gender" type="radio" value="male"> Male</label>
                <label><input v-model="formData.gender" type="radio" value="female"> Female</label>
                <small v-if="errors.gender" class="error">{{ errors.gender }}</small>
            </div>

            <div>
                <label><input v-model="formData.newsletter" type="checkbox"> Subscribe to newsletter</label>
            </div>
               
            <button type="submit">Submit</button>
        </form>
    </div>
</template>

<script setup>
const formData = ref({
    name: '',
    email: '',
    gender: '',
    newsletter: false
})
  
const errors = ref({})
  
const handleSubmit = () => {
    validateForm()
    if (Object.keys(errors.value).length === 0) {
        // Form submission logic goes here
        console.log('Form submitted successfully:', formData.value)
        // You can reset the form here if needed
        formData.value = {
        name: '',
        email: '',
        gender: '',
        newsletter: false
        }

        alert("Form submitted successfully")
    } else {
        console.log('Form has errors. Please fix them.')
    }
};
  
const validateForm = () => {
    errors.value = {}

    // Example validations
    if (!formData.value.name.trim()) {
        errors.value.name = 'Name is required.'
    }

    if (!formData.value.email.trim()) {
        errors.value.email = 'Email is required.'

    } else if (!isValidEmail(formData.value.email)) {
        console.log(111);
        errors.value.email = 'Invalid email format.'
    }

    if (!formData.value.gender) {
        errors.value.gender = 'Gender is required.'
    }
}
  
    const isValidEmail = (email) => {
     
    // Basic email validation regex (you can use a more thorough regex if needed)
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
    console.log(emailRegex.test(email))
    return emailRegex.test(email)
    }
  
</script>

  <style scoped>
  form {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    width: 300px;
    box-shadow: 1px 1px 2px 1px gray;
    padding: 0.5rem 1rem;
  }
  .error {
    color: red;
  }
  .container {
    padding: 2rem
  }
  button {
    width: 100px;
  }
  small {
    display: block;
  }

  form div {
    height: 40px;
  }
  </style>
  