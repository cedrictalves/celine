<template>
  <div class="navBar">
    <div id="logo-container" @click="goUp()">  
        <span id="logo" href="">Céline Alameddine</span><br>
        <span v-if="fr" id="logo-description-fr">Professeure de Français Langue Étrangère</span>
        <span v-else id="logo-description-en">French Foreign Language Teacher</span>
    </div>
    <ul v-if="fr" class="navBar-list">
        <li id="propos" @click="goDownTo('.about'),navBarShow()"><span>À propos</span></li>
        <li id="tarifs" @click="goDownTo('.tarifs'),navBarShow()"><span>Tarifs</span></li>
        <li id="contact" @click="goDownTo('.contact'),navBarShow()"><span>Contact</span></li>
    </ul>
     <ul v-else class="navBar-list">
        <li id="propos" @click="goDownTo('.about'),navBarShow()"><span>About me</span></li>
        <li id="tarifs" @click="goDownTo('.tarifs'),navBarShow()"><span>Prices</span></li>
        <li id="contact" @click="goDownTo('.contact'),navBarShow()"><span>Contact</span></li>
    </ul>
    <div @click="navBarShow()" class="hamburger">
        <div class="hamburger-line1"></div>
        <div class="hamburger-line2"></div>
        <div class="hamburger-line3"></div>
    </div>
  </div>
</template>

<script>

import $ from 'jquery'
import {globalFr} from '../App.vue'

export default {
  name: 'NavBar',
  data(){
    return{
      open: false,
    }
  },
  props: {
    msg: String
  },
  computed:{
    fr() {
      return globalFr.fr
    }
  },
  methods:{
    goUp(){
            $([document.documentElement, document.body]).animate({
            scrollTop: 0
        }, 500)
    },
    // show and hide the menu on tablets
    navBarShow(){
      if (this.open == false){
        $('.hamburger-line1').css('transform', 'rotate(45deg) translate(11px, 2px)')
                             .css('background-color', 'rgba(35, 71, 255,0.5)')
        $('.hamburger-line2').css('opacity', '0')
                             .css('transform', 'translateX(-20px)')
        $('.hamburger-line3').css('transform', 'rotate(-45deg) translate(11px, -2px)')
                             .css('background-color', 'rgba(255, 53, 53, 0.5)')
        $('.navBar-list').css('left', '0%')
        this.open = true
      } else{
        $('.hamburger-line1').css('transform', 'rotate(0deg) translate(0px, 0px)')
                             .css('background-color', 'rgb(43, 43, 43)')
        $('.hamburger-line2').css('opacity', '1')
                             .css('transform', 'translateX(0px)')
        $('.hamburger-line3').css('transform', 'rotate(0deg) translate(0px, 0px)')
                             .css('background-color', 'rgb(43, 43, 43)')
        $('.navBar-list').css('left', '-100%')
        this.open = false
      }
    },
    // links scroll to elemen
    goDownTo(classOfElem){
      $([document.documentElement, document.body]).animate({
        scrollTop: $(classOfElem).offset().top - 70
      }, 500)
    }
  },
}
</script>


<style lang="scss">
// COLORS
$dark-grey: rgb(57, 57, 57);
$light-grey: #D1D1D1;
$break-white: rgb(255, 255, 255);
$black: #232323;
$blue: rgba(35, 71, 255,0.5);
$red: rgba(255, 53, 53, 0.5);

// NAVBAR
.navBar{
    width: 100%;
    margin: auto;
    height: 70px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: $break-white;
    box-shadow: 0px 0px 10px 0px $dark-grey;
    position: fixed;
    z-index: 999;
    #logo-container{
        cursor: pointer;
        #logo{
            font-family: 'Reenie Beanie', cursive;
            color: $dark-grey;
            font-size: 1.7em;
            margin-left: 2.8em;
        }
        #logo-description-fr{
            margin-left: 3em;
            font-size: 0.7em;
            letter-spacing: .1em;
        }
        #logo-description-en{
            margin-left: 5em;
            font-size: 0.7em;
            letter-spacing: .1em;
        }
    }
    .navBar-list{
            display: flex;
            margin-right: 3em;
        li{
            list-style: none;
            transition: all .2s linear;
            border-left: 4px solid transparent;
            border-right: 4px solid transparent;
            span{
                display: flex;
                justify-content: center;
                align-items: center;
                height: 70px;
                width: 200px;
                text-align: center;
                text-decoration: none;
                color: $dark-grey;
                cursor: pointer;  
            }
        &:nth-child(1):hover{
            background-color: $blue;
            font-weight: bold;
            color: $break-white;
        }
        &:nth-child(2):hover{
            font-weight: bold;
            color: $black;
            border-left: 4px solid $blue;
            border-right: 4px solid $red;
        }
        &:nth-child(3):hover{
            background-color: $red;
            font-weight: bold;
            color: $break-white;
        }
    }
    }
    // hamburger
    .hamburger{
        width: 20px;
        height: 20px;
        display: none;
        flex-direction: column;
        justify-content: space-between;
        margin-right: 2em;
        cursor: pointer;
        .hamburger-line1, .hamburger-line2, .hamburger-line3{
        width: 100%;
        height: 2px;
        opacity: 1;
        background: $dark-grey;
        transition: all .5s ease-in-out;
        }
    }
}


// TABLETS AND MOBILE
@media(max-width: 1024px){
    .navBar{
        .hamburger{
            display: flex;
        }
        .navBar-list{
            flex-direction: column;
            position: absolute;
            left: -100%;
            top: 70px;
            margin-bottom: 70px;
            text-align: center;
            justify-content: center;
            background: $break-white;
            width: 100%;
            height: calc(100vh - 70px);
            transition: all .5s ease-in-out;
            li{
                    margin-bottom: 0.3em;
                    margin-top: 0.3em;
                span{
                    font-size: 2em;
                    width: 100%;
                }
            }
        }
    }
}
</style>
