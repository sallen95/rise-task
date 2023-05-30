<template>
  <SemiDoughnut />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import SemiDoughnut from "./components/SemiDoughnut.vue";

export default defineComponent({
  name: "App",
  components: {
    SemiDoughnut,
  },
  data: () => ({
    earned: 21.65,
    totalCredits: 25.85,
  }),
});
</script>

<style lang="scss">
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
