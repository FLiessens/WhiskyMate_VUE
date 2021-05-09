<template>
  <div id="app">
  <h1> My Whisky Mate </H1>
  <whiskyList></whiskyList>
  <div> 

  </div>
  </div>

</template>
<script>
//imports 
import whiskyList from './whiskyList'
export default {
  name: 'app',
  components:{whiskyList},
  }

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: white;
  background-color :#524e4e ;
border-radius: 1rem;
padding : 2rem; 
  
}

h1{
  font-weight: bold;
  font-size: 3rem;
  background-color : #1F293A;
  border-radius : 2rem ; 
  padding : 1rem;
  margin: 2rem;
}
h2{
  font-weight : italic; 
  font-size:20pt;
}

</style>
