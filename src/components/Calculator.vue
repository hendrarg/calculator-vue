<template>
  <p class="text-white text-center text-2xl py-8">Calculator with vue js</p>
  <div class="w-1/4 mx-auto p-3 bg-slate-700">
    <!-- Calculator Result -->
    <div class="w-full rounded m-1 p-3 text-right text-white font-bold bg-slate-600 mb-3">
      {{ calculatorValue || 0 }}
    </div>
    <div class="grid grid-cols-4 gap-2">
      <div
        class="text-white text-center bg-slate-600 rounded py-1 hover:bg-slate-500"
        v-for="n in calculatorElements"
        :key="n"
        :class="{ 'bg-vue-green': ['C', '*', '/', '-', '+', '%', '='].includes(n) }"
        @click="action(n)"
      >
        {{ n }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Calculator",
  data() {
    return {
      calculatorValue: "",
      calculatorElements: ["C", "*", "/", "-", 7, 8, 9, "+", 4, 5, 6, "%", 1, 2, 3, "=", 0, "."],
      oprator: null,
      previousCalculatorValue: "",
    };
  },
  methods: {
    action(n) {
      // Append value
      if (!isNaN(n) || n === ".") {
        this.calculatorValue += n + "";
      }
      // Clear value
      if (n === "C") {
        this.calculatorValue = "";
      }
      // Percentage
      if (n === "%") {
        this.calculatorValue = this.calculatorValue / 100 + "";
      }
      if (["/", "*", "-", "+"].includes(n)) {
        this.oprator = n;
        this.previousCalculatorValue = this.calculatorValue;
        this.calculatorValue = "";
      }
      if (n === "=") {
        this.calculatorValue = eval(this.previousCalculatorValue + this.oprator + this.calculatorValue);
        this.previousCalculatorValue = "";
        this.oprator = null;
      }
    },
  },
};
</script>

<style scoped>
.bg-vue-green {
  background: #10b981;
}
</style>
