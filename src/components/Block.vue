<template>
    <div class="block" v-if="showBlock" v-on:click="stopTimer">
        Click Me
    </div>
</template>

<script>
    export default {
        name: "Block",
        props: ['delay'],
        data() {
            return {
                showBlock: false,
                timer: null,
                reactionTime: 0,
            }
        },
        mounted() {
            setTimeout(() => {
                this.showBlock = true;
                this.startTimer();
            }, this.delay);
        },
        methods: {
            startTimer() {
                this.timer = setInterval(() => {
                    this.reactionTime += 5;
                }, 5);
            },
            stopTimer() {
                clearInterval(this.timer);
                console.log('your reaction time is :',this.reactionTime);
                this.$emit('end', this.reactionTime);
            }
        }
    }
</script>

<style scoped>
    .block {
        width: 500px;
        border-radius: 10px;
        background: cornflowerblue;
        color: white;
        text-align: center;
        padding: 150px 0px;
        margin: 30px auto;
    }
</style>