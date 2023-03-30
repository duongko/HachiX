<template>
  <div id="app">
    <SlideShow />
  </div>
</template>

<script>
import SlideShow from "./components/SlideShow/SlideShow.vue";
export default {
  name: "app",
  components: {
    SlideShow
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

h2, h4{
	margin: 0;
	padding: 0 20px;
	text-align: left;
}

body {
  margin: 0px;
}
</style>