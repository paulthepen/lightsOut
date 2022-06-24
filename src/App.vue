<template>
    <TheHeader />
    <div>
        <section>
         <lightRow :lightStatus="lightStatus.slice(0,3)" row="0" @toggleLight="toggleLight"/>
         <lightRow :lightStatus="lightStatus.slice(3,6)" row="1" @toggleLight="toggleLight"/>
         <lightRow :lightStatus="lightStatus.slice(6,9)" row="2" @toggleLight="toggleLight" />
        </section>
    </div>
        <roundCounter :round="this.round" />
        <gameOver :round="this.round" :type="this.type" @reset="reset" />
</template>

<script>
import lightRow from './components/LightRow.vue';
import TheHeader from './components/TheHeader.vue';
import roundCounter from './components/RoundCounter.vue';
import gameOver from './components/GameOver.vue';

const rando = () => {
    const e = [];
    for (let i=0; i<=8; i++) {
        e.push(Math.round(Math.random()));
    }
    return e;
}

export default {
    components: {lightRow, TheHeader, roundCounter, gameOver},
    data() {
        return {
            lightStatus: rando(),
            round: 1,
            type: null
        }
    },
    methods: {
        toggleLight(lightObj) {
            if (lightObj.status) {
                this.lightStatus[lightObj.index] = 1;
            } else {
                this.lightStatus[lightObj.index] = 0;
            }

            this.evaluateLights(lightObj.index);
        },
        reset() {
            this.lightStatus =  rando(),
            this.round = 1;
            this.type = null;
        },
        evaluateLights(index){
            const relations = {
                0: [1,3],
                1: [0,2,4],
                2: [1,5],
                3: [0,4,6],
                4: [1,3,5,7],
                5: [2,4,8],
                6: [3,7],
                7: [6,4,8],
                8: [7,5]
            };
            relations[index].forEach(element => {
                if (this.lightStatus[element] == 1) {
                    this.lightStatus[element] = 0;
                } else {
                    this.lightStatus[element] = 1;
                }
            });

            const result = this.lightStatus.filter(e => {
               return  e != 0;
            })

            this.round++;

            if (result.length == 0) {
                this.type = 'won';
            } else if (result.length == 9) {
                this.type = 'lost';
            }
        }
    }
}
</script>

<style scoped>
    section {
        display:flex;
        flex-direction: column;
        margin-top: 40px;
    }
    div {
        display:flex;
        justify-content: center;
    }
</style>

<style>
* { margin: 0; color: #eee;}
    body {
        background-color: #333;
    }
</style>