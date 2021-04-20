<template>
  <img :class="className" :alt="name" :src="require(`../../assets/${name}.svg`)" @click="$emit('click')">
</template>

<script>
export default {
  name: "Icon",
  props: {
    name: {
      type: String,
      required: true
    },
    className: {
      type: String,
      required: false
    }
  }
}
</script>

<style scoped>

</style>
