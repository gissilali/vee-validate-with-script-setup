
<template>
  <div>
    <Form action="" @click="handleSubmit">
      <Field :rules="validateEmail" type="email" name="email" v-model="email" />
      <ErrorMessage name="email" class="color-red" />
      <button type="submit">Submit</button>
    </Form>
  </div>
</template>



<script setup>
import { ref } from "vue"
import { Form, Field, ErrorMessage } from 'vee-validate';

const email = ref('')

const handleSubmit = () => {
  console.log("Submitting...")
}

const validateEmail = () => {
  // if the field is empty
  if (!email) {
    return 'This field is required';
  }
  // if the field is not a valid email
  const regex = /^[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}$/i;
  if (!regex.test(email)) {
    return 'This field must be a valid email';
  }
  // All is good
  return true;
}

</script>

<style >
.color-red {
  color: red;
}
</style>
