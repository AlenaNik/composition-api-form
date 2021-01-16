<template>
  <div class="container">
    <form class="card" @submit.prevent="submit">

      <h1>Auth</h1>

      <pre>{{ form.email }}</pre>
      <div class="form-control" :class="{invalid: !form.email.valid && form.email.touched}">
        <label for="email">Email</label>
        <input type="email" id="email" v-model="form.email.value" @blur="form.email.blur">
        <small v-if="form.email.errors.required && form.email.touched">Email can't be empty</small>
      </div>

      <pre>{{ form.password }}</pre>

      <div class="form-control" :class="{invalid: !form.password.valid && form.password.touched}">
        <label for="password">Password</label>
        <input type="password" id="password" v-model="form.password.value" @blur="form.password.blur">
        <small v-if="form.password.errors.required && form.password.touched">Password can't be empty</small>
        <small v-if="form.password.errors.minLength && form.password.touched">Password can't be less then 8</small>
      </div>

      <button class="btn primary" type="submit">Submit</button>
    </form>
  </div>

</template>

<script>

import { useForm } from "./use/form";

const required = val => !!val;
const minLength = num => val => val.length >= num;

export default {
  setup() {
    const form = useForm({
      email: {
        value: '',
        validators: {
          required
        }
      },
      password: {
        value: '',
        validators: {
          required,
          minLength: minLength(8)
        }
      }
    });

    function submit() {

    }
    return {
      form,
      submit
    }
  },
}
</script>

