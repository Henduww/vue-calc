<template>
<div class="container">
  <div class="target">
    <calculator />
  </div>
  <Moveable
      className="moveable"
      :target="['.target']"
      :draggable="true"
      :resizable="true"
      @drag="onDrag"
      @resize="onResize"
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
    onResize({ target, width, height}) {
      console.log('onResize', width, height)
      target.style.width = `${width}px`
      target.style.height = `${height}px`
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

  @media (max-width: 600px) {
    .target {
      width: 100%;
    }
  }

  @media (min-width: 600px) {
    .target {
      height: 600px;
      width: 400px;
    }
  }
</style>
