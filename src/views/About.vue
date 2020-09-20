<template>
  <div class="user-page">
    <template v-if="isLoggedIn">
      <p>{{USERINFO.username}}</p>
      <p>{{USERINFO.email}}</p>
      <p>{{USERINFO.role.name}}</p>
    </template>
    <template v-else>
      <h1>Вы не вошли в свой профиль</h1>
    </template>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import axios from "axios";

export default {
  name: "About",
  data() {
    return {
      info: null,
    };
  },
  computed: {
    ...mapGetters(["USERINFO"]),
    isLoggedIn: function() {
      return this.$store.getters.isLoggedIn;
    },
  },
  mounted() {
    axios
      .get("http://localhost:1337/bullets")
      .then((response) => (this.info = response.data));
  },
};
</script>

<style>
</style>
