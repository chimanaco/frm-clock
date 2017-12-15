<template>
  <div id="app">
    <Clock :blink="true" />
  </div>
</template>

<script>
import Clock from 'vue-digital-clock';

export default {
  name: 'app',
  components: {
    Clock,
  },
};
</script>

<style>
body {
  width: 100%;
  height: 100%;
  background: #000;
  color: #FFF;
}

#app {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 200px;
  text-align: center;
}
</style>
