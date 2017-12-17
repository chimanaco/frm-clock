<template>
  <div id="app">
    <WorldClock v-bind:city="cities[0]" v-bind:zone="zones[0]"></WorldClock>
    <WorldClock v-bind:city="cities[1]" v-bind:zone="zones[1]"></WorldClock>
    <WorldClock v-bind:city="cities[2]" v-bind:zone="zones[2]"></WorldClock>
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
      cities: ['VANCOUVER / CANADA', 'TOKYO / JAPAN', 'AMSTERDAM / NETHERLANDS'],
      zones: [-8, 9, 1],
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
  font-family: Helvetica, Arial, sans-serif;
  // font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #FFF;
}

#app {
  width: 100%;
  text-align: center;
}

p {
  margin: 0;
  padding: 0;
  line-height: 1;
}

</style>
