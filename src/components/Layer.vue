<template>
  <div class="layer">
    <div class="layer-content">
        <span v-if="fr" class="layer-content-1">Envie d'apprendre la langue Française ?</span>
        <span v-else class="layer-content-1">Want to learn French ?</span>
        <div class="line"></div>
        <span v-if="fr" class="layer-content-2">Vous êtes au bon endroit !</span>
        <span v-else class="layer-content-2">You are in the good place !</span>
      <div @click="goDown()" id="arrow1" >
          <span class="fas fa-arrow-down"></span>
      </div>
    </div>
  </div>
</template>

<script>
import $ from 'jquery'
import {globalFr} from '../App.vue'
export default {
  name: 'Layer',
  methods: {
    goDown(){
        $([document.documentElement, document.body]).animate({
          scrollTop: $(this.scrollTo).offset().top - 70
      }, 500)
    }
  },
  computed:{
    fr() {
      return globalFr.fr
    }
  },
  props: {
    scrollTo : String
  }
}
</script>

<style lang="scss">
$dark-grey: rgb(57, 57, 57);
$transparent-white: rgba(255,255,255,0.8);
$transparent-blue:rgba(234, 240, 255, 0.6);
$blue: rgba(35, 71, 255,0.5);

.layer{
  margin-top: 70px;
  width: 100%;
  height: calc(100vh - 20px);
  background-image: url('/images/students.jpg');
  background-position: center;
  background-size: cover;
  overflow: hidden;
  &-content{
    position: relative;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center ;
    width: 100%;
    height: 100%;
    background-color: $transparent-blue;
    padding: 3em;
  }
    
  .line{
    width: 100%;
    height: 1px;
    display: block;
    text-align: right;
    background-color: $dark-grey;
    transform: translateX(20%);
    margin: 1vw;
  }
    
  &-content-1{
    display: block;
    font-size: 4vw;
    padding: 0.5vw;
    width: 100%;
    text-align: right;
    letter-spacing: 0.2em;
    text-transform: uppercase;
  }
  &-content-2{
    display: block;
    font-size: 4.5vw;
    padding: 0.3vw;
    width: 100%;
    text-align: right;
    letter-spacing: 0.2em;
    font-weight: bold;
    text-transform: uppercase;
  }
  .fa-arrow-down{
    position: absolute;
    bottom: 70px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 30px;
    transition: all .5s ease-in-out;
    border-radius: 50%;
      &:hover{
        cursor: pointer;
        font-size: 30px;
        color: $blue;
      }
  }
}

@media(max-width: 768px){
    .layer{
        &-content-1{
            text-align: right;
            font-size: 6vw;
        }
        &-content-2{
            text-align: right;
            font-size: 7vw;
        }
    }

}


</style>
