<template>
    <div id="app">

        <div class='header'>
            <h1>Rock Paper Scissors</h1>
        </div>
        <div class='body'>
            <div class='score'>
                <div id='userLabel' class='badge'>Player</div>
                <div id='compLabel' class='badge'>Comp</div>
                <span id='userScore'>0</span>:<span id='compScore'>0</span>
            </div>

            <div class='result'>
                <p>The Result</p>
            </div>

            <div class='choices'>
                <div id='P' class="choice">
                    <img src="assets/Paper.png" alt=''>
                </div>
                <div id="r" class="choice">
                    <img src="assets/rock.png" alt=''>
                </div>
                <div id='s' class="choice">
                    <img src="assets/Scissors.png" alt=''>
                </div>
            </div>
            <p id='actionMessage'>Make a Move</p>
        </div>
    </div>
</template>

<script>


    export default {
        name: 'app',
        components: {}
    }
</script>

<style>
    @import url('https://fonts.googleapis.com/css?family=Asap:400,500,700&display=swap');

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        background-color: #292C34;
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
        font-family: Asap, sans-serif;
    }

    .score {
        margin: 20px auto;
        border: 3px solid white;
        border-radius: 4px;
        width: 20vh;
        color: white;
        font-size: 46px;
        text-align: center;
        padding: 15px 20px;
        font-family: Asap, sans-serif;
        position: relative;
    }

    .badge {
        background-color: #E2584D;
        color: white;
        font-size: 14px;
        padding: 2px 10px;
        font-family: Asap, sans-serif;
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
        font-weight: bold;
        font-family: Asap, sans-serif;
    }

    .choices {
        margin-top: 50px;
        text-align: center;
    }

    .choice {
        border: 4px solid white;
        border-radius: 50%;
        padding: 10px;
        margin: 0 20px;
        display: inline-block;
        transition: all .3s ease;
    }

    .choice:hover {
        cursor: pointer;
        background-color: gray;
    }

    #actionMessage {
        margin-top: 20px;
        text-align: center;
        color: white;
        font-family: Asap, sans-serif;
        font-weight: bold;
        font-size: 20px;
    }

</style>
