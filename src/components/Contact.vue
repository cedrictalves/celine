<template>
    <div class="contact">
        <div class="white-angle"></div>
        <h1 class="title">CONTACT</h1>
        <div v-if="fr" class="contact-content">
            <p>Pour réservez un cours ou pour plus d'informations, n'hésitez pas à me contacter grâce aux liens juste en dessous.</p>
        </div>
        <div v-else class="contact-content">
            <p>To book a course or for more information, do not hesitate to contact me using the links just below.</p>
        </div>
        <ul class="contact-nav">
            <li class="mail">
                <a href="mailto:celine.alameddine@hotmail.fr"><span class="fas fa-envelope"></span></a>
            </li>
            <li class="linkedin">
                <a href="https://www.linkedin.com/in/c%C3%A9line-alameddine-239105139/" target="_blank"><span class="fab fa-linkedin"></span></a>
            </li>
        </ul>
        <div @click="goUp()" id="arrowUp" >
            <span class="fas fa-arrow-up"></span>
        </div>
        <span class="copyright">© 2020 Céline Alameddine</span>
    </div>
</template>

<script>
import {globalFr} from '../App.vue'
import $ from 'jquery'
export default {
    name: 'Contact',
    methods:{
        goUp(){
            $([document.documentElement, document.body]).animate({
            scrollTop: 0
        }, 500)
        }
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
.contact{
    background: #FFF;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-bottom: 8em;
    position: relative;
    .white-angle{
    width: 150%;
    height: 100px;
    transform: rotate(1.5deg) translateY(-25px);
    z-index: 2;
    border-top: 1px solid rgba(218, 218, 218, 0.726);
    background: #FFF;
  }
    .title{
        margin-top: -2em;
         z-index: 3;
        width: 100%;
        text-align: center;
        padding: 2vw 0;
        font-weight: bold;
        font-size: 2em;
        letter-spacing: .2em;
    }

    .contact-content{
        padding-bottom: 4em;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 90%;
        p{  
        width: 90%;
        text-align: center;
        font-family: Arial;
        margin-bottom: 0.6em;
        }
    }

    .contact-nav{
        display: flex;
        li{
            list-style-type: none;
            margin: 1em;
            width: 100px;
            height: 100px;
            border-radius: 30px;
            box-shadow: 0 5px 15px -5px #000000;
            overflow: hidden;
            background: rgb(151, 173, 244);
            transition: all .3s ease-in;
            a{  
                display: flex;
                width: 100px;
                height: 100px;
                text-decoration: none;
                font-size: 3em;
                color: white;
                justify-content: center;
                align-items: center;
                transition: all .3s ease-in;
                &:hover{
                    transform: scale(1.2)
                }
            }
            &:hover{
                box-shadow: 0 3px 3px -2px #000000; 

            }
        }
        .linkedin:hover{
            background: #0077B5;
        }
        .mail:hover{
            background: #dd4b39;

        }
    }
    #arrowUp{
        position: absolute;
        bottom: 1em;
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
  .copyright{
      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      font-size: .8em;
      font-family: sans-serif;
  }
}

</style>