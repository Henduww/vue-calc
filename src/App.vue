<template>
<div class="container">
  <div class="target wrapper">
    <div class="display">
      <p id="Equation">{{ equation }}</p>
    </div>
    <calculator-button @clicked="onCalcBtnClick" val="C" />
    <calculator-button @clicked="onCalcBtnClick" val="ANS" />
    <calculator-button @clicked="onCalcBtnClick" val="DEL" />
    <calculator-button @clicked="onCalcBtnClick" val=" + " />
    <calculator-button @clicked="onCalcBtnClick" val="1" />
    <calculator-button @clicked="onCalcBtnClick" val="2" />
    <calculator-button @clicked="onCalcBtnClick" val="3" />
    <calculator-button @clicked="onCalcBtnClick" val=" - " />
    <calculator-button @clicked="onCalcBtnClick" val="4" />
    <calculator-button @clicked="onCalcBtnClick" val="5" />
    <calculator-button @clicked="onCalcBtnClick" val="6" />
    <calculator-button @clicked="onCalcBtnClick" val=" * " />
    <calculator-button @clicked="onCalcBtnClick" val="7" />
    <calculator-button @clicked="onCalcBtnClick" val="8" />
    <calculator-button @clicked="onCalcBtnClick" val="9" />
    <calculator-button @clicked="onCalcBtnClick" val=" / " />
    <calculator-button />
    <calculator-button @clicked="onCalcBtnClick" val="0" />
    <calculator-button @clicked="onCalcBtnClick" val="." />
    <calculator-button @clicked="onCalcBtnClick" val="=" />
  </div>
  <Moveable
      className="moveable"
      v-bind:target="['.target']"
      v-bind:draggable="true"
      v-bind:scalable="true"
      @drag="onDrag"
      @scale="onScale"
  />
</div>
</template>

<script>
import Moveable from 'vue3-moveable'
import CalculatorButton from './components/CalculatorButton.vue'

export default {
  name: 'App',
  data: function() {
    return {
      equation: "",
      ans: 0
    }
  },
  components: {
    CalculatorButton,
    Moveable,
  },
  methods: {
    onDrag({ target, transform }) {
      target.style.transform = transform
    },
    onScale({ target, drag }) {
      target.style.transform = drag.transform
    },
    onCalcBtnClick(val) {
      if (val === "=") {
        let ans = eval(this.equation)
        this.equation = ans.toString()
        this.ans = ans
      }
      else if (val === "C")
        this.equation = ""
      else if (val === "DEL")
        this.equation = this.equation.slice(0, -1)
      else if (val === "ANS")
        this.equation += this.ans
      else 
        this.equation += val
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
}

.display {
  grid-column: 5/1;
  height: 70px;
}

.display > p {
  float: right;
  margin-right: 25px;
}

</style>
