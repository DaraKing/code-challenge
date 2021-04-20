<template>
  <div class="user-item" v-if="user">
    <div class="user-image">
      <img :src="user.picture.large" />
    </div>
    <div class="user-data">
      <p>{{user.name.title}} {{user.name.first}}</p>
      <p>{{user.name.last}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserItem",
  props: {
    user: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.user-item {
  width: 80%;
  height: 200px;
  margin: 20px auto;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 1fr);
  grid-column-gap: 0;
  grid-row-gap: 0;
  border-radius: 5px;
  -webkit-box-shadow: 3px 3px 10px 0 rgba(0,0,0,0.75);
  -moz-box-shadow: 3px 3px 10px 0 rgba(0,0,0,0.75);
  box-shadow: 3px 3px 10px 0 rgba(0,0,0,0.75);
}

.user-item:hover {
  cursor: pointer;
  -webkit-box-shadow: 3px 3px 15px 0 rgba(0,0,0,0.75);
  -moz-box-shadow: 3px 3px 15px 0 rgba(0,0,0,0.75);
  box-shadow: 3px 3px 15px 0 rgba(0,0,0,0.75);
}

.user-image { grid-area: 1 / 1 / 3 / 2; }
.user-data {
  grid-area: 1 / 2 / 3 / 4;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.user-data p {
  font-weight: 400;
  padding: 10px 20px;
  font-size: 1.4rem;
}

.user-image img {
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
  width: 100%;
  height: 100%;
}
</style>
