<template>
  <div>
    <form @submit.prevent="login">
      <label for="email">Email:</label>
      <input v-model="email" type="email" id="email" value />

      <label for="password">Password:</label>
      <input v-model="password" type="password" id="password" value />

      <button type="submit" name="button">Login</button>

      <p>{{ error }}</p>

      <router-link to="/register">
        Don't have an account? Register.
      </router-link>
    </form>
  </div>
</template>

<script>
export default {
  name: "LoginUser",
  data() {
    return {
      email: "",
      password: "",
      error: null,
    };
  },
  methods: {
    login() {
      this.$store
        .dispatch("login", {
          email: this.email,
          password: this.password,
        })
        .then(() => this.$router.push({ name: "dashboard" }))
        .catch((err) => {
          console.log("err", err);
          this.error = err.response.data.error;
        });
    },
  },
};
</script>

<style scoped></style>
