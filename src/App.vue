<template>
  <div id="app">
    <div class="container">
      <img class="sars" src="./assets/sars.png" alt="sars"/>
      <Header/>
      <div class="cases-wrapper">
        <p class="cases confirmed">zakażonych <span class="cases__confirmed">{{ confirmed() }}<span class="cases-num">+{{ differenceConfirmed() }}</span></span></p>
        <p class="cases deaths">zmarłych <span class="cases__deaths">{{ deaths() }}<span class="cases-num">+{{ differenceDeaths() }}</span></span></p>
        <p class="cases recovered">wyleczonych <span class="cases__recovered">{{ recovered() }}<span class="cases-num">+{{ differenceRecovered() }}</span></span></p>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue';

export default {
  name: 'App',
  data() {
    return {
      cases: null
    }
  },
  methods: {
    confirmed(){
      return this.cases.filter((v, i, arr) => i === arr.length - 1)[0].Confirmed.toLocaleString()
    },
    deaths(){
      return this.cases.filter((v, i, arr) => i === arr.length - 1)[0].Deaths.toLocaleString()
    },
    recovered(){
      return this.cases.filter((v, i, arr) => i === arr.length - 1)[0].Recovered.toLocaleString()
    },
    differenceConfirmed(){
      const last = this.cases.filter((v, i, arr) => i === arr.length - 1)[0].Confirmed;
      const beforeLast = this.cases.filter((v, i, arr) => i === arr.length - 2)[0].Confirmed;
      return last - beforeLast;
    },
    differenceDeaths(){
      const last = this.cases.filter((v, i, arr) => i === arr.length - 1)[0].Deaths;
      const beforeLast = this.cases.filter((v, i, arr) => i === arr.length - 2)[0].Deaths;
      return last - beforeLast;
    },
    differenceRecovered(){
      const last = this.cases.filter((v, i, arr) => i === arr.length - 1)[0].Recovered;
      const beforeLast = this.cases.filter((v, i, arr) => i === arr.length - 2)[0].Recovered;
      return last - beforeLast;
    }
  },
  components: {
    Header
  },
  async created(){
    const promise = await fetch('https://api.covid19api.com/total/dayone/country/poland');
    const cases = await promise.json();
    return this.cases = cases;
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

.cases {
position: relative;
}

.cases-num{
position: absolute;
font-size: 18px;
color: #0ee76f;
right: -14px;
top: -27px;
}

.cases-wrapper{
display: flex;
flex-direction: row;
justify-content: space-between;
font-size: 38px;
margin-top: 143px;
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
