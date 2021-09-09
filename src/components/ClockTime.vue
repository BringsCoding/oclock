<template>
  <section>
    <p class="lights">lights 💡</p>
    <div class="clocktime">
      <span v-if="dateTime.hours <= 9">{{ "0" + dateTime.hours }}</span>
      <span v-else>{{ dateTime.hours }}</span
      >:
      <span v-if="dateTime.minutes <= 9">{{ "0" + dateTime.minutes }}</span>
      <span v-else>{{ dateTime.minutes }}</span
      >:
      <span v-if="dateTime.seconds <= 9">{{ "0" + dateTime.seconds }}</span>
      <span v-else>{{ dateTime.seconds }}</span>
    </div>
  </section>
  <section>
    <div class="flex-box-progressbar">
      <label for="file">Stunden</label>
      <progress id="file" :value="dateTime.hours" max="24"></progress>
      <p>{{ dateTime.hours }} H</p>
    </div>
    <div class="flex-box-progressbar">
      <label for="file">Minuten</label>
      <progress id="file" :value="dateTime.minutes" max="60"></progress>
      <p>{{ dateTime.minutes }} Min</p>
    </div>
    <div class="flex-box-progressbar">
      <label for="file">sekunden</label>
      <progress id="file" :value="dateTime.seconds" max="60"></progress>
      <p>{{ dateTime.seconds }} Sec</p>
    </div>
  </section>
  <section>
    <p style="font-family: Bebas Neue">Heute ist</p>
    <div class="flex-date">
      <p>{{ days[dateTime.day] }}</p>
      <p>{{ dateTime.datenumber }}</p>
      <p>{{ months[dateTime.month] }}</p>
      <p>{{ dateTime.year }}</p>
    </div>
    <div class="flex-weekend">
      <p>
        {{ days[dateTime.day] }} =
        <span v-if="dateTime.day < 5">{{
          " Es ist noch kein Wochenden..."
        }}</span>
        <span v-else>{{ "Es ist Wochenden" }}</span>
      </p>
    </div>
  </section>
  <section>
    <div class="block">
      <div class="maincontainer">
        <div class="thecard">
          <div class="thefront">
            <div class="flipCartFlex">
              <p>{{ Bundestagswahl.day }}</p>
              .
              <p>{{ Bundestagswahl.month }}</p>
              .
              <p>{{ Bundestagswahl.year }}</p>
            </div>

            <p>Noch</p>
            <p>{{ Bundestagswahl.day - dateTime.datenumber }}</p>
            <p>Tage Bis zur Bundestagswahl</p>
          </div>
          <div class="theback">
            <p class="rotate">
              am 26.9.2021 sind Bundestagswahlen Bitte geh wählen
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
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
      Bundestagswahl: {
        day: 26,
        month: 9,
        year: 2021,
      },
      formulaRace: {
        day: 12,
        month: 9,
        year: 2021,
      },
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
/* For the clock */
.clocktime {
  font-size: 3.75rem;
  font-family: "Anton", sans-serif;
  color: black;
  background-color: aquamarine;
  border: solid 4px red;
  border-radius: 8px;
}

.lights {
  border: solid 4px blue;
  border-radius: 8px;
  margin: 0.3125rem;
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
.flex-box-progressbar {
  display: inline-grid;
  margin: 0.625rem;
  margin-top: 1.875rem;
  font-family: "Bebas Neue", cursive;
  font-size: 1.25rem;
}
/* Progressbar */
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
  gap: 0.625rem;
  font-family: "Bebas Neue", cursive;
  font-size: 1.875rem;
}
/* Flip card */
.block {
  display: flex;
}
.maincontainer {
  position: relative;
  height: 12.5rem;
  width: 9.375rem;
  border-radius: 6px;
  background-color: rgb(149, 149, 149);
  margin: 0 auto;
  margin-bottom: 0.3125rem;
}

.thecard {
  position: absolute;
  width: 100%;
  height: 100%;

  border-radius: 6px;
  transform-style: preserve-3d;
  transition: all 0.8s cubic-bezier(0.4, 0, 1, 1);
  background-color: blue;
}

.thecard:hover {
  transform: rotateY(180deg);
}

.thefront {
  position: absolute;
  width: 100%;
  height: 100%;
  border: 3px solid yellow;
  border-radius: 5px;
  backface-visibility: hidden;
  color: black;
  font-size: 0.9375rem;
  text-align: center;
  background: rgb(2, 0, 36);
  background: rgb(209, 149, 149);
  margin: 0 auto;
  margin-bottom: 0.3125rem;
}

.flipCartFlex {
  display: flex;
  justify-content: center;
  gap: 0.0625rem;
}

.theback {
  position: absolute;
  width: 105%;
  height: 100%;
  border-radius: 5px;
  border: 3px solid salmon;
  backface-visibility: hidden;
  color: rgb(0, 0, 0);
  transform: rotateY(180deg);
  transform-style: preserve-3d;
  background: rgb(2, 0, 36);
  background: linear-gradient(
    34deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(88, 88, 255, 1) 0%,
    rgba(80, 99, 255, 1) 0%,
    rgba(139, 3, 255, 1) 57%,
    rgba(84, 93, 255, 1) 100%
  );
}

.rotate {
  border: 5px;
  font-size: 0.9375rem;
  text-align: center;
  margin-top: 3.125rem;
  font-family: "Roboto", sans-serif;
  color: azure;
}
</style>
