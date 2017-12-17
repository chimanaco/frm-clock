<template>
  <div class="clockWrapper">
    <div class="clock">
      <p class="date">{{ date }}</p>
      <p class="time">{{ time }}</p>
      <p class="city">{{id}}</p>
    </div>
  </div>
</template>

<script>
const week = ['SUN', 'MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT'];
export default {
  name: 'WorldClock',
  props: ['id', 'zone'],
  data() {
    return {
      time: '',
      date: '',
      timeID: '',
      msg: 'Welcome to Your Vue.js App',
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
      this.date = this.showDate(this.zone);
      this.time = this.showTime(this.zone);
    },
    dateToTimeString(dt) {
      const hh = `${this.zeroPadding(dt.getUTCHours(), 2)}`;
      const mm = `${this.zeroPadding(dt.getUTCMinutes(), 2)}`;
      const ss = `${this.zeroPadding(dt.getUTCSeconds(), 2)}`;
      return `${hh}:${mm}:${ss}`;
    },
    dateToDateString(dt) {
      const year = `${dt.getUTCFullYear()}`;
      const month = `${this.zeroPadding(dt.getUTCMonth() + 1, 2)}`;
      const date = `${this.zeroPadding(dt.getUTCDate(), 2)}`;
      const ww = `${week[dt.getUTCDay()]}`;
      return `${year}/${month}/${date} ${ww}`;
    },
    showDate(timeZone) {
      const tzTime = new Date(Date.now() + (timeZone * 3600000));
      return this.dateToDateString(tzTime);
    },
    showTime(timeZone) {
      const tzTime = new Date(Date.now() + (timeZone * 3600000));
      return this.dateToTimeString(tzTime);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.clockWrapper {
  position: relative;
  // background: blue;
  height: 960px;
}

.clock {
  position: absolute;
  width: 100%;
  top: 50%;
  right: 50%;
  transform: translate(50%, -50%);
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
