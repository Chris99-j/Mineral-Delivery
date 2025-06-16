<template>
  <WaterHome />
</template>

<script>
import WaterHome from './views/WaterHome.vue';


export default {
  name: 'App',
  components: {
    WaterHome,
  },
};
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
<style>
body {
  margin: 0;
  background-image: url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=1400&q=80');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  font-family: Arial, sans-serif;
}
</style>