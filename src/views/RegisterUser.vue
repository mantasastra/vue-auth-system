<template>
  <div>
    <form @submit.prevent="register">
      <label for="name">Name:</label>
      <input v-model="name" type="text" id="name" value />

      <label for="email">Email:</label>
      <input v-model="email" type="email" id="email" value />

      <label for="password">Password:</label>
      <input v-model="password" type="password" id="password" value />

      <button type="submit" name="button">Register</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "RegisterUser",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    register() {
      this.$store
        .dispatch("register", {
          name: this.name,
          email: this.email,
          password: this.password,
        })
        .then(() => {
          this.$router.push({ name: "dashboard" });
        });
    },
  },
};
</script>

<style scoped></style>
