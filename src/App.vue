<template>
  <div id="app">
    <div id="frEn" @click="frEn()">EN</div>
    <NavBar/>
    <layer scrollTo=".about"/>
    <About scrollTo=".tarifs"/>
    <Tarifs scrollTo=".contact"/>
    <Contact/>
  </div>
</template>

<script>
import Vue from 'vue'
import NavBar from './components/NavBar.vue'
import Layer from './components/Layer.vue'
import About from './components/About.vue'
import Tarifs from './components/Tarifs.vue'
import Contact from './components/Contact.vue'
import $ from 'jquery'
export const globalFr = new Vue({
  data:{
    fr: true
  }
})
export default {
  name: 'App',
  components: {
    NavBar, Layer, About, Tarifs ,Contact
  },
  methods:{
    frEn(){
      if (globalFr.fr ==  true){
        $('#frEn').text('FR')
        globalFr.fr = false
      }
      else{
        $('#frEn').text('EN')
        globalFr.fr = true
      }
    }
  }
}

</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Reenie+Beanie&family=Roboto&display=swap');
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  font-family: 'Roboto', sans-serif;
  overflow-x: hidden !important;
  color: rgb(57, 57, 57);
}

#frEn{
  cursor: pointer;
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 99909;
  user-select: none;
  font-weight: bold;
}
</style>
