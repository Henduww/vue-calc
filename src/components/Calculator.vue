<template>
    <div class="calculator">
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
    <div>
        <dynamic-list :list="history" class="calc-history" />
    </div>
</template>

<script>
import CalculatorButton from './CalculatorButton.vue'
import DynamicList from './DynamicList.vue'

export default {
    data: function() {
        return {
            equation: "",
            ans: 0,
            history: []
        }
    },
    components: {
        DynamicList,
        CalculatorButton
    },
    methods: {
        onCalcBtnClick(val) {
            if (val === "=") {
                let ans = eval(this.equation)
                this.history.push(this.equation + " = " + ans)
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
    .calculator {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    gap: 5px;
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