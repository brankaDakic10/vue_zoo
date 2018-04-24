<template>
  <div id="app">
   
    <AnimalList/>
    <ButtonDisabled/>
    <SimpleCalculator/>
  </div>
</template>

<script>
import AnimalList from './components/AnimalList.vue'
import  ButtonDisabled from './components/ButtonDisabled.vue'
import  SimpleCalculator from './components/SimpleCalculator.vue'
export default {
  name: 'app',
  components: {
    AnimalList,
    ButtonDisabled,
    SimpleCalculator
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
