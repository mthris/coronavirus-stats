<template>
  <div id="app">
    <div class="container">
      <img class="sars" src="./assets/sars.png" alt="sars"/>
      <Header/>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue';

export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@900&display=swap');
*{
margin: 0;
padding: 0;
}

body {
overflow-x: hidden;
}

html, body {
height:100%;
width:100%;
}

.container{
max-width: 1200px;
width: 90%;
margin: 0 auto;
position: relative;
}

.sars {
position: absolute;
left:0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #db1637;
  color: #ffffff;
  font-family: 'Roboto', sans-serif;
  min-height: 100%;
}
</style>
