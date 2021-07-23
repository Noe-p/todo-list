<template>
  <Todos/>
</template>

<script>
import Todos from './components/Todos.vue'

export default {
  name: 'App',
  components: {
    Todos
  }
}
</script>

<style>
#app {
  font-family: 'Text', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  font-size: 1.5vw;
  display: flex;
  flex-direction: column;
  align-items: center;
}

body{
  margin:0;
}

/*FONTS*/
@font-face {
   font-family: 'Text-bold';
   src: url("assets/fonts/Montserrat/Montserrat-Bold.ttf");
   font-display: swap;
}

@font-face {
   font-family: 'Text';
   src: url("assets/fonts/Montserrat/Montserrat-Regular.ttf");
   font-display: swap;
}
</style>
