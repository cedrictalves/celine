<template>
    <div v-if="fr" class="about">
        <div class="white-angle"></div>
        <h1 class="title">À PROPOS DE MOI</h1>
        <div class="bio-content">
            <img src="images/french.png" alt="Drapeau France - Céline Alameddin Professeure de Français Langue Étrangère"/>
            <p>Bonjour à tous ! Je m’appelle Céline, je suis basée à Montréal et je suis professeure de français langue étrangère titulaire d’un master dans le même domaine.</p><br>
            <p>Tu es un amoureux de la langue française ? Tu veux apprendre le français pour le travail ? Pour les études ou simplement le plaisir ? Tu n'as pas le temps de te déplacer pour aller dans une école de langue ? Je te propose aujourd'hui de t'aider dans la découverte de la langue et de la culture française à travers des cours particuliers en ligne.</p><br>
            <p>De débutant complet à avancé, pour des objectifs spécifiques liés à ton domaine de travail ou si tu veux tout simplement mieux connaître la langue et la culture française, tu es au bon endroit. Alors, quel que soit ton niveau et ton but, n’hésite pas à me contacter pour qu’on puisse discuter et se lancer ensemble dans une nouvelle aventure.</p><br>
            <p>Enfin, si tu as besoin de plus d’informations à propos de moi et mon parcours, voici mon cv !</p><br>
            <div @click="showCv()" class="cv-button-container"><span class="fas fa-file cv-button"></span></div>
            <span class="my-cv">MON CV</span>
            <div @click="goDown()" id="arrow2" >
                <span class="fas fa-arrow-down"></span>
            </div>
        </div>
    </div>
    <div v-else class="about">
        <div class="white-angle"></div>
        <h1 class="title">ABOUT ME</h1>
        <div class="bio-content">  
            <img src="images/british.png" alt="Drapeau UK - Céline Alameddine Professeure de Français Langue Étrangère">
            <p>Hey there ! My name is Céline and I am a French teacher, based in Montréal, who has a master degree in the same field of study.</p><br>
            <p>You are a French lover ? You want to learn French for your job ? For your studies or just for fun ? You do not have time to take lessons in language school ? I offer to help you in the discover of the French language and culture with online private lessons.</p><br>
            <p>From beginner to advanced level, for specifics goals or just for the pleasure: you are in the best place ! So, whatever your level and your goals, do not hesitate to contact me to discuss about you and embark on a new adventure !</p><br>
            <p>If you want to know more about me and my work path, click on the icon just bellow !</p><br>
            <div @click="showCv()" class="cv-button-container"><span class="fas fa-file cv-button"></span></div>
            <span class="my-cv">MY CV</span>
            <div @click="goDown()" id="arrow2" >
                <span class="fas fa-arrow-down"></span>
            </div>
        </div>
    </div>
</template>

<script>

import $ from 'jquery'
import {globalFr} from '../App.vue'

export default {
    name: 'About',
    methods: {
        goDown(){
            $([document.documentElement, document.body]).animate({
            scrollTop: $(this.scrollTo).offset().top - 70
        }, 500)
        },
        showCv(){
            window.open('images/CV.pdf', '_blank', 'fullscreen=yes'); return false;
        }
    },
    props: {
        scrollTo : String
    },
    computed:{
    fr() {
      return globalFr.fr
    }
  },
}
</script>

<style lang="scss">
$dark-grey: rgb(57, 57, 57);
$light-grey: #D1D1D1;
$red: rgba(255, 53, 53, 0.5);
.about{
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
  background: #FFF;
  .white-angle{
    width: 150%;
    height: 100px;
    transform: rotate(1.5deg) translateY(-25px);
    z-index: 2;
    border-top: 1px solid rgba(125, 125, 125, 0.726);
    background: #FFF;
  }
  .title{
    width: 100%;
    text-align: center;
    padding: 2vw 0;
    font-weight: bold;
    font-size: 2em;
    letter-spacing: .2em;
    margin-top: -2em;
    z-index: 3;
  }
  .bio-content{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    width: 95%;
    p{  
      width: 90%;
      text-align: center;
      font-family: Arial;
      line-height: 30px; 
    }
    img{
      width: 80px;
      height: 50px;
      margin: 1.5em;
      float: left;

    }
  }
  .line2{
    width: 85%;
    height: 1px;
    background-color: $light-grey;
    margin-bottom: 3vw;
    margin-top: 3vw;
  }

  #arrow1{
    position: absolute;
    bottom: 1.6em;
    left: 50%;
    transform: translateX(-50%);
    font-size: 30px;
    transition: all .5s ease-in-out;
    border-radius: 50%;
    &:hover{
      cursor: pointer;
      font-size: 30px;
      color: $red;
    }
  }

  .line3{
    width: 85%;
    height: 1px;
    background-color: $light-grey;
  }

  #arrow2{
    font-size: 30px;
    transition: all .5s ease-in-out;
    border-radius: 50%;
    margin: 2em;
    &:hover{
      cursor: pointer;
      font-size: 30px;
      color: $red;
    }
  }
}

.cv-button-container{
    cursor: pointer;
    margin: 1em auto ;
    width: 80px;
    height: 80px;
    border-radius: 8px;
    box-shadow: 0 5px 5px -5px #000000;
    overflow: hidden;
    background: rgb(151, 173, 244);
    transition: all .3s ease-in;
    display: flex;
    justify-content: center;
    align-items: center;
    &:hover{
      box-shadow: 0 3px 3px -2px #000000; 
      background: $red;
    }
    .cv-button{
      text-decoration: none;
      font-size: 2em;
      color: white;
      justify-content: center;
      align-items: center;
      transition: all .3s ease-in;

    }
    &:hover .cv-button{
      transform: scale(1.2)
    }
    
  .my-cv{
    margin: auto;
  }
}
</style>