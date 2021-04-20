<template>
  <div v-if="user">
    <Icon class-name="back-icon" name="back-icon" @click="$router.go(-1)" />

    <div class="user-details" v-if="user.picture">
      <img :src="user.picture.large" />

      <p class="name">{{user.name.title}} {{user.name.first}} {{user.name.last}}</p>

      <p class="birth-date">{{birthDate}}</p>

      <p>{{user.location.street.name}} {{user.location.street.number}}, {{user.location.city}} {{user.location.country}}</p>

      <p>{{user.email}}</p>

      <p>{{user.phone}}</p>
    </div>
  </div>
</template>

<script>
import constants from "@/constants";
import Icon from "@/components/reusable/Icon";

export default {
  name: 'User',
  components: {Icon},
  props: ['uuid'],
  data() {
    return {
      user: {}
    }
  },
  computed: {
    birthDate() {
      if (!this.user) {
        return ''
      }
      let date = new Date(this.user.dob.date)

      return `${date.getDate()}.${date.getMonth()}.${date.getFullYear()}`;
    }
  },
  methods: {
    fetchUser() {
      this.axios.get(constants.API_URL).then((response) => {
        this.user = response.data.results.find(user => user.login.uuid === this.uuid)
      })
    }
  },
  created() {
    this.fetchUser()
  }
}
</script>

<style>
  .back-icon {
    margin-left: 25px;
    width: 64px;
    height: 64px;
  }

  .user-details {
    padding: 20px;
  }

  p {
    margin: 10px 0;
  }

  .name {
    margin: 20px 0;
    font-size: 1.8rem;
    font-weight: 600;
  }
</style>
