<template>
    <p class="rank">{{ rank }}</p>
    <p>Reaction Time : {{ score }}ms</p>
</template>

<script>
    export default {
        name: "Results",
        props: ['showResults', 'score'],
        data() {
            return {
                rank: null
            }
        },
        mounted() {
            if (this.score <= 250) {
                this.rank = "Ninja Fingers";
            } else if (this.score <= 400) {
                this.rank = "Rapid Reflex";
            } else {
                this.rank = "Slow Pace";
            }
        }
    }
</script>

<style scoped>
    .rank {
        font-size: 1.4rem;
        color: cornflowerblue;
    }
</style>