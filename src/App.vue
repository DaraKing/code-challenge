<template>
  <div id="app">
    <Header />

    <div id="user-list">
      <UserItem v-for="(user, index) in users"
                v-bind:key="index"
                :user="user" />
    </div>
  </div>
</template>

<script>
import Header from "@/components/partials/Header";
import constants from "@/constants";
import UserItem from "@/components/reusable/UserItem";

export default {
  name: 'App',
  components: {UserItem, Header},
  data() {
    return {
      users: []
    }
  },
  methods: {
    fetchUsers() {
      this.axios.get(constants.API_URL).then((response) => {
        this.users = response.data.results ?? []
      })
    }
  },
  created() {
    this.fetchUsers()
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
}
#app {
  min-height: 100vh;
  width: 100%;
}
</style>
