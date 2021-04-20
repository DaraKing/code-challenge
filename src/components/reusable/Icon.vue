<template>
  <img :alt="name" :src="require(`../../assets/${name}.svg`)">
</template>

<script>
export default {
  name: "Icon",
  props: {
    name: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>

</style>
