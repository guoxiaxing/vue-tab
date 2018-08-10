<template>
  <div>
    <Tab :tab='tabs'></Tab>
  </div>
</template>

<script>
import Tab from './Tab.vue'
export default {
  name: 'app',
  components:{
    Tab
  },
  data(){
    return {
      tabs:{
        imgs:['./img/1.jpg','./img/2.jpg','./img/3.jpg','./img/4.jpg','./img/5.jpg'],
        index:0,
        timer:null
      }
    }
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
