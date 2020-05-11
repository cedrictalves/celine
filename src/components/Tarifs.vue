<template>
    <div>
        <div v-if="fr" class="tarifs">
            <div class="blue-angle"></div>
            <h1 class="title">TARIFS</h1>
            <p>Vous trouverez ici les tarifs des cours.</p>
            <div class="table-container">
                <table>
                    <tbody>
                        <tr>
                            <th>Durée :</th>
                            <td>1h de cours</td>
                            <td>10h de cours</td>
                        </tr>
                        <tr>
                            <th>Tarifs :</th>
                            <td>25.00€ TTC</td>
                            <td>225.00€ TTC</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div @click="goDown()" id="arrow3" >
                <span class="fas fa-arrow-down"></span>
            </div>
        </div>
        <div v-else class="tarifs">
            <div class="blue-angle"></div>
            <h1 class="title">PRICES</h1>
            <p>You will fin the prices just down here.</p>
            <div class="table-container">
                <table>
                    <tbody>
                        <tr>
                            <th>Duration :</th>
                            <td>1h lesson</td>
                            <td>10h lesson</td>
                        </tr>
                        <tr>
                            <th>Prices :</th>
                            <td>25.00€ Tax incl.</td>
                            <td>225.00€ Tax incl.</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div @click="goDown()" id="arrow3" >
                <span class="fas fa-arrow-down"></span>
            </div>
        </div>
    </div>
</template>

<script>
import {globalFr} from '../App.vue'
import $ from 'jquery'

export default {
    name: 'Tarifs',
    methods: {
        goDown(){
            $([document.documentElement, document.body]).animate({
                scrollTop: $(this.scrollTo).offset().top - 70
            }, 500)
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

.tarifs{
    background: rgb(234, 240, 255);
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-bottom: 8em;
    position: relative;
    .blue-angle{
        width: 150%;
        height: 100px;
        transform: rotate(-1.5deg) translateY(-25px);
        z-index: 2;
        border-top: 1px solid rgba(218, 218, 218, 0.726);
        background: rgb(234, 240, 255);
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

    p{  
        width: 90%;
        text-align: center;
        font-family: Arial;
        margin: 2em;
    }

    img{
        width: 60%;
        height: auto;
        margin: 2em;
    }

    .table-container{
        width: 80%;
        table{ 
            border: 1px solid black;
            background: rgb(151, 173, 244);
            text-align: center;
            width: 100%;
        }
        th, td{
            background: #FFF;
            border: 1px solid black;
            width: 33%;
            padding: 1em;
        }
    }
    #arrow3{
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
            color: rgba(35, 71, 255,0.5);
        }
    }
}

</style>