<template>
  <section>
    <h1>Users Page</h1>
    <ul>
      <li v-for="user of users" :key="user.id">
        <a href="#" @click.prevent="openUser(user)">{{ user.name }} ---></a>
        <a href="#" @click.prevent="openUser(user)">mail: {{ user.email }}</a>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  async fetch({ store }) {
    if (store.getters['users/users'].length === 0) {
      await store.dispatch("users/fetch");
    }
  },
  data: () => ({
    pageTitle: "Users page",
  }),
  computed: {
    users() {
      return this.$store.getters['users/users'];
    },
  },
  methods: {
    openUser(user) {
      this.$router.push("./users/" + user.id);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>