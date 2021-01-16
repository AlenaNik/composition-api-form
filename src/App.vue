<template>
  <div class="container">
    <form class="card" @submit.prevent="submit">

      <h1>Auth</h1>

      <pre>{{ form.email }}</pre>
      <div class="form-control">
        <label for="email">Email</label>
        <input type="email" id="email" v-model="form.email.value">
      </div>

      <pre>{{ form.password }}</pre>

      <div class="form-control">
        <label for="password">Password</label>
        <input type="password" id="password" v-model="form.password.value">
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
        value: 'email@email.com',
        validators: {
          required
        }
      },
      password: {
        value: 'my_password',
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

