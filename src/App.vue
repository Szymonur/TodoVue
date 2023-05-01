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
  background: rgb(9,181,125);
  background: linear-gradient(132deg, rgba(9,181,125,1) 27%, rgba(41,136,63,0.8295693277310925) 100%);
}
#app {
  font-family: Helvetica, Arial, sans-serif;
}
</style>
