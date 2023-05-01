<template>
    <ToDo> </ToDo>
</template>

<script>
import  ToDo from "./components/ToDo.vue"
export default {
  name: 'App',
  components: {
    ToDo
  }
}
</script>

<style>
body{
  overflow: hidden;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
}
#app {
  font-family: Helvetica, Arial, sans-serif;
}
</style>
