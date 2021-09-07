<template>
  <p class="lights">Lights</p>
  <div class="clocktime">
    {{ dateTime.hours }}:
    <span v-if="dateTime.minutes <= 9">{{ "0" + dateTime.minutes }}</span>
    <span v-else>{{ dateTime.minutes }}</span
    >:
    <span v-if="dateTime.seconds <= 9">{{ "0" + dateTime.seconds }}</span>
    <span v-else>{{ dateTime.seconds }}</span>
  </div>
  <div class="flex-box-houre">
    <label for="file">Stunden</label>
    <progress id="file" :value="dateTime.hours" max="24"></progress>
    <p>{{ dateTime.hours }} H</p>
  </div>
  <div class="flex-box-houre">
    <label for="file">Minuten</label>
    <progress id="file" :value="dateTime.minutes" max="60"></progress>
    <p>{{ dateTime.minutes }} Min</p>
  </div>
  <div class="flex-box-houre">
    <label for="file">sekunden</label>
    <progress id="file" :value="dateTime.seconds" max="60"></progress>
    <p>{{ dateTime.seconds }} Sec</p>
  </div>
  <p style="font-family: Bebas Neue">Heute ist</p>
  <div class="flex-date">
    <p>{{ days[dateTime.day] }}</p>
    <p>{{ dateTime.datenumber }}</p>
    <p>{{ months[dateTime.month] }}</p>
    <p>{{ dateTime.year }}</p>
  </div>
</template>

<script>
const date = new Date();
export default {
  name: "App",
  data() {
    return {
      dateTime: {
        hours: date.getHours(),
        minutes: date.getMinutes(),
        seconds: date.getSeconds(),
        datenumber: date.getDate(),
        day: date.getDay(),
        month: date.getMonth(),
        year: date.getFullYear(),
      },
      timer: undefined,
      days: [
        "Sonntag",
        "Montag",
        "Dienstag",
        "Mittwoch",
        "Donnerstag",
        "Freitag",
        "Samstag",
      ],
      months: [
        "Januar",
        "Februar",
        "März",
        "April",
        "Mai",
        "Juni",
        "Juli",
        "August",
        "September",
        "Oktober",
        "November",
        "Dezember",
      ],
    };
  },
  methods: {
    setDateTime() {
      const date = new Date();
      this.dateTime = {
        hours: date.getHours(),
        minutes: date.getMinutes(),
        seconds: date.getSeconds(),
        day: date.getDay(),
        datenumber: date.getDate(),
        month: date.getMonth(),
        year: date.getFullYear(),
      };
    },
  },
  beforeMount() {
    this.timer = setInterval(this.setDateTime, 1000);
  },
  beforeUnmount() {
    clearInterval(this.timer);
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Anton&display=swap");
@import url("https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap");

*,
*::before,
*::after {
  box-sizing: border-box;
}

.clocktime {
  font-size: 60px;
  font-family: "Anton", sans-serif;
  color: black;
  background-color: aquamarine;
  border: solid 4px red;
  border-radius: 8px;
}

.lights {
  border: solid 4px blue;
  border-radius: 8px;
  margin: 5px;
}

.lights:hover + .clocktime {
  background-color: blueviolet;
}

.flex-progress {
  display: flex;
  margin: 0 auto;
  justify-content: center;
}
.flex-times {
  display: flex;
}
.flex-box-houre {
  display: inline-grid;
  margin: 10px;
  margin-top: 30px;
  font-family: "Bebas Neue", cursive;
  font-size: 20px;
}

progress {
  border: black solid 1px;
  border-radius: 10px;
  background-color: black;
}

progress {
  color: lightblue;
  border-radius: 10px;
}

progress::-webkit-progress-value {
  background: lightblue;
  border-radius: 10px;
}

progress::-moz-progress-bar {
  background: lightcolor;
  border-radius: 10px;
}

progress::-webkit-progress-value {
  background: rgb(154, 219, 2);
  border-radius: 10px;
}

progress::-webkit-progress-bar {
  background: rgb(0, 0, 187);
  border-radius: 10px;
}

.flex-date {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
  font-family: "Bebas Neue", cursive;
  font-size: 30px;
}
</style>
