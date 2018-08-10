<template>
  <div>
    <Tab :tab='tabs'></Tab>
    <Slider :slider='sliders'></Slider>
  </div>
</template>

<script>
import Tab from './Tab.vue'
import Slider from './Slider.vue'
export default {
  name: 'app',
  components:{
    Tab,
    Slider
  },
  data(){
    return {
      tabs:{
        imgs:['./img/1.jpg','./img/2.jpg','./img/3.jpg','./img/4.jpg','./img/5.jpg'],
        index:0,
        timer:null
      },
      sliders:{
        imgs:['./img/1.jpg','./img/2.jpg','./img/3.jpg','./img/4.jpg','./img/5.jpg','./img/6.jpg','./img/7.jpg']
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
