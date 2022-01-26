<template>
<div class="container">
  <div class="target">
    <calculator />
  </div>
  <Moveable
      className="moveable"
      :target="['.target']"
      :draggable="true"
      :scalable="true"
      @drag="onDrag"
      @scale="onScale"
  />
</div>
</template>

<script>
import Moveable from 'vue3-moveable'
import Calculator from './components/Calculator.vue'

export default {
  name: 'App',
  
  components: {
    Calculator,
    Moveable
  },
  methods: {
    onDrag({ target, transform }) {
      target.style.transform = transform
    },
    onScale({ target, drag }) {
      target.style.transform = drag.transform
    },
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

  .target {
    position: absolute;
    
  }
</style>
