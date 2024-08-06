<template>
    <div>
      <h1>Login</h1>
      <form @submit.prevent="login">
        <input type="text" v-model="username" placeholder="Username" />
        <input type="password" v-model="password" placeholder="Password" />
        <button type="submit">Login</button>
      </form>
      <p v-if="error">{{ error }}</p>
    </div>
  </template>
  
  <script>
  import axios from "axios";
  
  export default {
    data() {
      return {
        username: "test",
        password: "HR1qGSAqpfrEWpZDnWBZxrh8Ll/DmFsYxjASiMqKCdqJzvb0nhAb2annRb7TeQV7RsxIqw0gd1nGyDRXm8/PpA==",
        error: null,
      };
    },
    methods: {
      async login() {
        try {
          const response = await axios.post(`${process.env.VUE_APP_HTTP_PREFIX}/login`, {
            username: this.username,
            password: this.password,
          });
          console.log(response.data);
        } catch (error) {
          this.error = error.response ? error.response.data : "An error occurred";
        }
      },
    },
  };
  </script>
  