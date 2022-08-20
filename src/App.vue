<template>
  <div id="app">
    <dog-button></dog-button>
    <cat-button></cat-button>
    <display-selection></display-selection>
    
  </div>
</template>

<script>
import CatButton from './components/CatButton.vue';
import DisplaySelection from "./components/DisplaySelection.vue";
import DogButton from "./components/DogButton.vue";

export default {
  name: "App",
  components: {
    DisplaySelection,
    DogButton,
    CatButton,
  },
};
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
</style>
