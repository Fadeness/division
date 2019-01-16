<template>
  <div id="app">
    <h1 id="title">The Division Helper</h1>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <GearSet gear-title="Striker's Battlegear"></GearSet>
    <GearSet gear-title="AlphaBridge"></GearSet>
    <GearSet gear-title="Banshee's Shadow"></GearSet>
    <GearSet gear-title="D3-FNC"></GearSet>
    <GearSet gear-title="DeadEYE"></GearSet>
    <GearSet gear-title="Final Measure"></GearSet>
    <GearSet gear-title="FireCrest"></GearSet>
    <GearSet gear-title="Hunter's Faith"></GearSet>
    <GearSet gear-title="Lone Star"></GearSet>
    <GearSet gear-title="Path of the Nomad"></GearSet>
    <GearSet gear-title="Predator's Mark"></GearSet>
    <GearSet gear-title="Sentry's Call"></GearSet>
    <GearSet gear-title="Reclaimer"></GearSet>
    <GearSet gear-title="Tactician's Authority"></GearSet>
  </div>
</template>

<script>
import GearSet from './components/GearSet.vue'

export default {
  name: 'app',
  components: {
    GearSet
  }
}
</script>

<style>
@font-face {
  font-family: "borda";
  src: url("./assets/font/borda.ttf");
}

body {
  margin: 0;
}
#app {
  font-family: "borda";
  text-align: center;
  /* color: #2c3e50; */
  color: #fff;
  background-color: rgb(54, 138, 105);
  display: flex;
  flex-wrap: wrap;
}
#title {
  padding: 20px 0;
  margin: 0;
  width: 100%;

  background-color: rgb(255, 109, 16);
}
</style>
