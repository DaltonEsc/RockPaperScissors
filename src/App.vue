<template>
    <div id="app">

        <div class='header'>
            <h1>Rock Paper Scissors</h1>
        </div>
        <div class='body'>
            <div class='score'>
                <div id='userLabel' class='badge'>Player</div>
                <div id='compLabel' class='badge'>Comp</div>
                <span id='userScore'>{{userscore}}</span>:<span id='compScore'>{{compscore}}</span>
            </div>

            <div class='result'>
                <p>{{result}}</p>
            </div>

            <div class='choices'>
                <div v-on:click="userclicked('Paper')" id='P' class="choice">
                    <img src="./assets/Paper.png" alt="">
                </div>
                <div v-on:click="userclicked('Rock')" id="r" class="choice">
                    <img src="./assets/Rock.png" alt="">
                </div>
                <div v-on:click="userclicked('Scissors')" id='s' class="choice">
                    <img src="./assets/Scissors.png" alt="">
                </div>
            </div>

            <p id='actionMessage'>Make a Move</p>

            <div class="moves">
                <div class="usermove">
                    <p>You Picked</p>
                    <img :src="usermove" alt=''>
                    <p>{{userchoice}}</p>
                </div>
                <div class="compmove">
                    <p>Computer Picked </p>
                    <img :src="compmove" alt=''>
                    <p>{{compchoice}}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'app',
        data() {
            return {
                userscore: 0,
                compscore: 0,
                result: 'Let The Game Begin',
                usermove: "",
                compmove: "",
                userchoice: '',
                compchoice: '',
            }
        },
        methods: {
            /*
            1 = paper, 2 = rock, 3 scissors
            1 beats 2, 2 beats 3, 3 beats 1
             */
            userclicked: function (choice) {
                this.comparison(choice, this.computerchocie())

            },
            computerchocie: function () {
                return Math.floor(Math.random() * 3) + 1;
            },
            comparison: function (choice, compchoice) {
                if (choice === 'Paper') {
                    this.usermove = "https://img.icons8.com/color/48/000000/hand.png";
                    this.userchoice = 'Paper';
                    if (compchoice === 1) {
                        this.result = "Tie";
                        this.compmove =  "https://img.icons8.com/color/48/000000/hand.png";
                        this.compchoice = 'Paper';
                    } else if (compchoice === 2) {
                        this.result = "You Win: Paper Covers Rock";
                        this.compmove = "https://img.icons8.com/color/48/000000/hand-rock.png";
                        this.compchoice = 'Rock';
                        this.userscore += 1;
                    } else if (compchoice === 3) {
                        this.result = "You Loose: Scissors Cuts Paper";
                        this.compmove = "https://img.icons8.com/color/48/000000/hand-scissors.png";
                        this.compchoice = 'Scissors';
                        this.compscore += 1;
                    }
                } else if (choice === 'Rock') {
                    this.usermove = "https://img.icons8.com/color/48/000000/hand-rock.png";
                    this.userchoice = 'Rock';
                    if (compchoice === 1) {
                        this.result = "You Loose: Paper Covers Rock";
                        this.compmove =  "https://img.icons8.com/color/48/000000/hand.png";
                        this.compchoice = 'Paper';
                        this.compscore += 1;
                    } else if (compchoice === 2) {
                        this.result = "Tie";
                        this.compmove = "https://img.icons8.com/color/48/000000/hand-rock.png";
                        this.compchoice = 'Rock';
                    } else if (compchoice === 3) {
                        this.result = "You Win: Rock Smashes Scissors";
                        this.compmove = "https://img.icons8.com/color/48/000000/hand-scissors.png";
                        this.compchoice = 'Scissors';
                        this.userscore += 1;
                    }
                } else if (choice === 'Scissors') {
                    this.usermove = "https://img.icons8.com/color/48/000000/hand-scissors.png";
                    this.userchoice = 'Scissors';
                    if (compchoice === 1) {
                        this.result = "You Win: Scissors Cuts Paper";
                        this.compmove =  "https://img.icons8.com/color/48/000000/hand.png";
                        this.compchoice = 'Paper';
                        this.userscore += 1;
                    } else if (compchoice === 2) {
                        this.result = "You Loose: Rock Smashes Scissors";
                        this.compmove = "https://img.icons8.com/color/48/000000/hand-rock.png";
                        this.compchoice = 'Rock';
                        this.compscore += 1;
                    } else if (compchoice === 3) {
                        this.result = "Tie";
                        this.compmove = "https://img.icons8.com/color/48/000000/hand-scissors.png";
                        this.compchoice = 'Scissors';
                    }
                }
            }
        }
    }
</script>

<style>
    @import url('https://fonts.googleapis.com/css?family=Asap:400,500,700&display=swap');

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        background-color: #292C34;
        font-family: Asap, sans-serif;
        font-weight: bold;

    }

    .body {
        background-color: #292C34;
        width: 100%;
    }

    .header {
        background: white;
        padding: 20px;
    }

    .header > h1 {
        background-color: white;
        color: #292C34;
        text-align: center;
    }

    .score {
        margin: 20px auto;
        border: 3px solid white;
        border-radius: 4px;
        width: 30vh;
        color: white;
        font-size: 46px;
        text-align: center;
        padding: 15px 20px;
        position: relative;
    }

    .badge {
        background-color: #E2584D;
        color: white;
        font-size: 14px;
        padding: 2px 10px;
    }

    #userLabel {
        position: absolute;
        top: 30px;
        left: -30px;
    }

    #compLabel {
        position: absolute;
        top: 30px;
        right: -30px;
    }

    .result {
        font-size: 40px;
        color: white;
    }

    .result > p {
        text-align: center;

    }

    .choices {
        margin-top: 50px;
        text-align: center;
    }

    .choice {
        border: 4px solid white;
        border-radius: 50%;
        padding: 12px;
        margin: 0 20px;
        display: inline-block;

    }

    .choice:hover {
        cursor: pointer;

    }

    #actionMessage {
        margin-top: 20px;
        text-align: center;
        color: white;
        font-size: 20px;
    }

    .moves {
        margin: 20px auto;
        position: relative;
        text-align: center;
        font-size: 30px;
    }

    .usermove {
        position: absolute;
        top: 10%;
        left: 20%;
        color: white;
    }

    .compmove {
        position: absolute;
        top: 10%;
        right: 20%;
        color: white;
    }
</style>
