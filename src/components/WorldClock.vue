<template>
  <div class="clockWrapper">
    <div class="clock">
      <p class="city">{{ city }}</p>
      <p class="time">{{ time }}</p>
      <p class="date">{{ date }}</p>
    </div>
  </div>
</template>

<script>
const week = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];
const month = ['January', 'February', 'March', 'April', 'May', 'June',
  'July', 'August', 'September', 'October', 'November', 'December'];

export default {
  name: 'WorldClock',
  props: ['city', 'zone'],
  data() {
    return {
      time: '',
      date: '',
      timeID: '',
      msg: 'Welcome to Your Vue.js App',
    };
  },
  created() {
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
      this.tzTime = this.getTimeZoneTime(this.zone);
      this.date = this.showDate(this.tzTime);
      this.time = this.showTime(this.tzTime);
    },
    dateToTimeString(dt) {
      const hh = `${this.zeroPadding(dt.getUTCHours(), 2)}`;
      const mm = `${this.zeroPadding(dt.getUTCMinutes(), 2)}`;
      const ss = `${this.zeroPadding(dt.getUTCSeconds(), 2)}`;
      return `${hh}:${mm}:${ss}`;
    },
    dateToDateString(dt) {
      // const yy = `${dt.getUTCFullYear()}`;
      // const mm = `${this.zeroPadding(dt.getUTCMonth() + 1, 2)}`;
      const mm = `${month[dt.getUTCMonth()]}`;
      const dd = `${this.zeroPadding(dt.getUTCDate(), 2)}`;
      const ww = `${week[dt.getUTCDay()]}`;
      return `${ww} ${dd} ${mm}`;
    },
    getTimeZoneTime(timeZone) {
      const tzTime = new Date(Date.now() + (timeZone * 3600000));
      return tzTime;
    },
    showDate(tzTime) {
      const dateString = this.dateToDateString(tzTime);
      return dateString;
    },
    showTime(tzTime) {
      const timeString = this.dateToTimeString(tzTime);
      return timeString;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.clockWrapper {
  position: relative;
  height: 640px;
}

.clock {
  position: absolute;
  width: 100%;
  top: 50%;
  right: 50%;
  transform: translate(50%, -50%);
}

p.time {
  font-weight: bold;
  font-size: 200px;
}

p.date {
  font-size: 75px;
  //color: #CCC;
}

p.city {
  margin-bottom: 10px;
  font-weight: bold;
  font-size: 65px;
}
</style>
