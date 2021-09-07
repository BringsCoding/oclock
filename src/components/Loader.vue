<template>
  <h2>Counter Test 1</h2>
  <CircleProgress :percent="percent" :viewport="true" :show-percent="true" />

  <h2>Counter test 2</h2>
  <CircleProgress
    :percent="80"
    :viewport="true"
    :show-percent="true"
    :is-gradient="true"
  />
</template>

<script>
import { ref, onMounted } from "vue";
import CircleProgress from "vue3-circle-progress";
import "vue3-circle-progress/dist/circle-progress.css";
export default {
  name: "App",
  components: {
    CircleProgress: CircleProgress,
  },
  setup() {
    const percent = ref(75);

    onMounted(() => {
      setInterval(() => {
        if (percent.value === 25) {
          percent.value = 100;
        } else {
          percent.value = 25;
        }
      }, 1000);
    });

    return {
      percent,
    };
  },
};
</script>
