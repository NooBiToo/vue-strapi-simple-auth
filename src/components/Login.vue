<template>
  <div>
    <form class="login" @submit.prevent="login">
      <h1>Sign in</h1>
      <label>Email</label>
      <input required v-model="identifier" type="text" placeholder="Name" />
      <label>Password</label>
      <input
        required
        v-model="password"
        type="password"
        placeholder="Password"
      />
      <hr />
      <button type="submit">Login</button>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      identifier: "user@strapi.io",
      password: "123456",
    };
  },
  methods: {
    login: function() {
      let identifier = this.identifier;
      let password = this.password;
      this.$store
        .dispatch("login", { identifier, password })
        .then(() => this.$router.push("/"))
        .catch((err) => console.log(err));
    },
  },
};
</script>
