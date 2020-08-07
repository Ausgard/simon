<template>
    <div class="simon">
        <h1 class="simon__headline">Simon Says</h1>
        <div class="simon__board">
            <button class="simon__item" :class="'simon__item--' + gameBtn.title" v-for="gameBtn of gameBoard" :id="gameBtn.id" @click="boardHandler" type="button"></button>
        </div>
        <div class="simon__control">
            <p class="simon__control-text">Выберите уровень</p>
            <form class="simon__control-level-buttons" >
                <div class="simon__control-level-btn">
                    <label for="low">Легкий</label>
                    <input class="simon__control-level" type="radio" id="low" value="low" @change="lvlSelected" v-model="picked">
                </div>
                <div class="simon__control-level-btn">
                    <label for="middle">Средний</label>
                    <input class="simon__control-level" type="radio" id="middle" value="middle" @change="lvlSelected" v-model="picked">
                </div>
                <div class="simon__control-level-btn">
                    <label for="hard">Сложный</label>
                    <input class="simon__control-level" type="radio" id="hard" value="hard" @change="lvlSelected" v-model="picked">
                </div>
            </form>
            <p class="simon__control-text simon__control-text--score">Ваш рекорд {{clickCount}}</p>
            <button class="simon__control-start" type="button" @click="sessionInit">Let's play</button>
        </div>
    </div>

</template>

<script>
    export default {
        data() {
            return {
                picked: '',
                btnPushed: '',
                newClick: '',
                clickCount: 0,
                scoreData: [],
                userScoreData: [],
            }
        },
        methods: {
            sessionInit(event, userScore, scoreData, clickCount) {
                if(event) {
                    this.clickCount++
                    this.scoreData = getRandomNumber(1,5,clickCount)
                }
                console.dir('Рандом ' + this.scoreData)
            },

            // boardHandler(btnPushed, scoreData, userScoreData, clickCount) {
            //     this.btnPushed = btnPushed.target.id
            //     this.userScoreData.push(Number(this.btnPushed))

            //     console.dir(this.scoreData)
            //     console.dir(this.userScoreData)

            //     if(this.userScoreData.length) {
            //         for(let i = 0; this.userScoreData.length; i++) {
            //             if(this.userScoreData[i] === this.scoreData[i]) {
            //                 return console.dir('true')
                            
            //             } else {
            //                 return console.dir('false')
                            
            //             }
            //         }
            //     }
            // },

            lvlSelected(picked) {
                console.dir(this.picked)
            },
        }, ///methods

        props: {
            gameBoard: {
                type: Array
            }
        } 
    }
    
    // test(function() {
    //     b(global)
    // })
    
    // function test(b) {
    //     b()
    // }

    // function b(c) {
    //     console.dir(c)
    // }

    function getRandomNumber(min, max, c) {
        let arr = []
        while(c > arr.length) {
            arr.push( (Math.random() * (max - min) + min) ^ 0 )
        }
        return arr
    }
    // console.dir(getRandomNumber(1, 5, 5))
</script>





























<style scoped lang="sass">
    .simon,
    .simon__control
        display: flex
        flex-direction: column
        align-items: center

    .simon
        display: flex
        flex-direction: row
        justify-content: center
        align-items: center  
        flex-wrap: wrap

    .simon__headline
        font-size: 25px
        width: 100%
        margin: 50px 0

    .simon__control-text,
        font-size: 18px

    .simon__control-text--score
        font-size: 20px


    .simon__board
        display: flex
        flex-direction: row
        align-items: center
        flex-wrap: wrap
        width: 300px
        height: 300px
        border-radius: 50%
        overflow: hidden
        margin: 0 25px 0 0

    .simon__item
        width: 150px
        height: 150px
        opacity: 0.5
        border: none
        outline: none

    .simon__item--red
        background-color: red

    .simon__item--blue
        background-color: blue

    .simon__item--yellow
        background-color: yellow

    .simon__item--green
        background-color: green

    .simon__control-level-btn
        display: flex
        flex-direction: row
        justify-content: space-between
        align-items: center
        margin: 15px 0
        input
            width: 25px
            height: 25px
            margin: 0 0 0 15px      

    .simon__control-start
        width: 255px
        height: 40px
        color: white
        font-size: 16px
        background-color: #27c289
        border: solid 2px #27c289
        border-radius: 5px
        transition: 0.2s
        margin: 1rem 0 0 0

        &:hover
            background-color: white
            color: #27c289
            transition: 0.2s
</style>