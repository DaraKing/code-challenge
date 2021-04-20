<template>
  <div id="user-list">
    <UserItem v-for="(user, index) in users"
              v-bind:key="index"
              :user="user" />
  </div>
</template>

<script>
import constants from "@/constants";
import UserItem from "@/components/reusable/UserItem";

export default {
  name: 'App',
  components: {UserItem},
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
