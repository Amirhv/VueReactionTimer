<template>
    <h1>Reaction Timer</h1>
    <button class="btn" v-on:click="start" v-bind:disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" v-bind:delay="delay" v-on:end="endGame"/>
    <Results v-if="showResults" v-bind:score="score"/>
</template>


<script>
    import Block from "./components/Block";
    import Results from "./components/Results";

    export default {
        name: 'App',
        components: {
            Block,
            Results
        },
        data() {
            return {
                isPlaying: false,
                delay: null,
                showResults: false,
                score: null
            }
        },
        methods: {
            start() {
                this.delay = 2000 + (Math.random() * 5000);
                this.isPlaying = true;
                this.showResults = false;
            },
            endGame(reactionTime) {
                this.isPlaying = false;
                this.showResults = true;
                this.score = reactionTime;
            }
        }
    }
</script>


<style>
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }

    .btn {
        display: inline-block;
        font-size: 1.4rem;
        padding: 10px 20px;
        background: hotpink;
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        letter-spacing: 2px;
        margin-bottom: 10px;
    }

    .btn:focus {
        outline: none;
    }

    .btn:active {
        transform: scale(0.9);
    }

    .btn:disabled {
        opacity: 0.34;
        cursor: not-allowed;
    }
</style>
