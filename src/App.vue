<template>
  <div id="app">
  <div id="clock">
    <p class="date">{{ date }}</p>
    <p class="time">{{ time }}</p>
  </div>
  </div>
</template>

<script>
const week = ['SUN', 'MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT'];

export default {
  name: 'app',
  components: {
  },
  data() {
    return {
      time: '',
      date: '',
      timeID: '',
    };
  },
  created() {
    // this.updateTime();
    this.timeID = setInterval(this.updateTime, 1000);
  },
  methods: {
    zeroPadding(num, digit) {
      let zero = '';
      let i;
      for (i = 0; i < digit; i += 1) {
        zero += '0';
      }
      return (zero + num).slice(-digit);
    },
    updateTime() {
      const cd = new Date();
      this.time = `${this.zeroPadding(cd.getHours(), 2)}:${this.zeroPadding(cd.getMinutes(), 2)}:${this.zeroPadding(cd.getSeconds(), 2)}`;
      this.date = `${this.zeroPadding(cd.getFullYear(), 4)}-${this.zeroPadding(cd.getMonth() + 1, 2)}-${this.zeroPadding(cd.getDate(), 2)} ${week[cd.getDay()]}`;
    },
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

p {
  margin: 0;
  padding: 0;
  line-height: 1;
}

p.date {
  font-size: 110px;
}

</style>
