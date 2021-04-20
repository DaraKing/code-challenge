<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>

<script>
import Header from "@/components/partials/Header";
export default {
  components: {Header}
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
