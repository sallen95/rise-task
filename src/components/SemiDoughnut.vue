<template>
  <div class="semi-doughnut">
    <div class="credit-graph">
      <p class="credit-text">Total Credits</p>
      <p class="credit-number">25.85</p>
      <div class="graph" style="--fill: #a590c0" />
      <div class="graph" style="--fill: #785c9c" :style="transformStyle" />
    </div>
    <div class="legend">
      <div class="legend-div">
        <div class="legend-box" style="--color: #785c9c" />
        <p class="legend-text">{{ this.earned }} Earned</p>
      </div>
      <div class="legend-div">
        <div class="legend-box" style="--color: #a590c0" />
        <p class="legend-text">{{ this.projected }} Projected</p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SemiDoughnut",
  data: () => ({
    totalCredits: 25.85,
    earned: 21.65,
    projected: 4.2,
  }),
  computed: {
    earnedPercentage(): number {
      return (100 * this.earned) / this.totalCredits;
    },
    transformStyle(): { transform: string } {
      return {
        transform: `rotate(calc(1deg * ${this.earnedPercentage} * 1.8))`,
      };
    },
  },
});
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Lato&display=swap");
.semi-doughnut {
  display: flex;
  font-family: "Lato", sans-serif;
}
.credit-graph {
  width: 200px;
  height: 100px;
  position: relative;
  display: flex;
  flex-direction: column-reverse;
  overflow: hidden;
}
.credit-text {
  font-size: 22px;
  line-height: 28px;
  font-weight: 400;
  margin: 0;
}
.credit-number {
  font-size: 28px;
  line-height: 36px;
  font-weight: 600;
  margin: 0;
}
.graph {
  width: 170px;
  height: 85px;
  border: 15px solid var(--fill);
  border-top: none;
  position: absolute;
  transform-origin: 50% 0% 0;
  border-radius: 0 0 200px 200px;
  top: 100%;
  transform: rotate(180deg);
}
.legend {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-left: 25px;
  font-size: 14px;
  line-height: 20px;
  font-weight: 500;
  padding-top: 15px;
}
.legend-div {
  display: flex;
  align-items: center;
  height: 27px;
}
.legend-box {
  width: 15px;
  height: 15px;
  margin-right: 12px;
  background: var(--color);
}
</style>
