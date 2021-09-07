<template>
  <ClockTime />
  <button @click="goToDark" type="button" class="btn btn-primary">
    Darke Mode
  </button>
</template>

<script>
import ClockTime from "./components/ClockTime.vue";

export default {
  name: "App",
  components: {
    ClockTime,
  },
  methods: {
    goToDark() {
      document.documentElement.classList.toggle("dark-mode");
    },
  },
};
</script>

<style>
html,
body {
  background-color: rgb(209, 149, 149);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.dark-mode {
  filter: invert(100%);
}
</style>
