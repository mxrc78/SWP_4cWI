<template>
<section>
  <ul>
    <my-wheater>

    </my-wheater>
  </ul>
</section>

</template>

<script>
import myWheater from "./components/myWheater.vue"


export default {

  name: 'App',
  components: {
    myWheater
  }
}
</script>




<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
