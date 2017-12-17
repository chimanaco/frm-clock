<template>
  <div id="app">
    <WorldClock v-bind:id="item" v-bind:zone="zone"></WorldClock>
    <WorldClock v-bind:id="item2" v-bind:zone="zone2"></WorldClock>
  </div>
</template>

<script>
import WorldClock from './components/WorldClock';

export default {
  name: 'app',
  components: {
    WorldClock,
  },
  data() {
    return {
      item: 'Tokyo',
      zone: 9,
      item2: 'Vancouver',
      zone2: -8,
    };
  },
};

</script>

<style>
body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  background: #000;
  color: #FFF;
  //font-size: 50px;
}

#app {
  // position: absolute;
  width: 100%;
  // top: 50%;
  // transform: translate(0, -50%);
  font-family: Helvetica, Arial, sans-serif;
  // font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 200px;
  text-align: center;
}

p {
  margin: 0;
  padding: 0;
  line-height: 1;
}

p.date, p.city {
  font-size: 110px;
}

</style>
