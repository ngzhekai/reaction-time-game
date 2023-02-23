<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click on me
    </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: 0,
            reactionTime: 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = Date.now()
        },
        stopTimer() {
            this.reactionTime = Date.now() - this.timer
            console.log(this.reactionTime)
            this.$emit('reactTime', this.reactionTime)
        }
    }
}
</script>

<style>
.block {
    width: 350px;
    height: auto;
    border-radius: 20px;
    background: #0faf87;
    color: #181818;
    text-align: center;
    padding: 50px 0;
    margin: 40px auto;
    font-size: 3em;
    text-transform: capitalize;
}

.block:hover {
    background: hsla(160, 100%, 37%, 0.2);
    color: white;
}

@media(max-width: 390px){
    .block {
        width: 100%;
    }
}
</style>