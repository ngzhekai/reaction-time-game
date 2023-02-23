<template>
    <p class="result">Your Reaction Time is: {{ score }}ms</p>
    <div>
        <img :src="rankIcon" :alt="rank">
        <p class="rank">{{ rank }}</p>
    </div>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null,
            rankIcon: null
        }
    },
    mounted() {
        if (this.score < 200) {
            this.rank = 'Ninja Fingers!'
            this.rankIcon = './src/assets/ninja.png'
        }
        else if (this.score < 400) {
            this.rank = 'Rapid Reflexes'
            this.rankIcon = "./src/assets/bunny.png"
        }
        else {
            this.rank = 'Snail pace...'
            this.rankIcon = "./src/assets/snail.png"
        }
    }
}
</script>

<style scoped>
.result {
    color: rgba(0, 0, 0, 0.64);
    font-size: 1.8em;
}

@media (prefers-color-scheme: dark) {
    .result {
        color: rgba(235, 235, 235, 0.64);
    }
}

.rank {
    font-size: 1.4em;
    color: hsla(160, 100%, 37%, 1);
    font-weight: bold;
}

img {
    width: 160px;
    height: 160px;
    margin: auto 10px;
    background-size: cover;
}

div {
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 10px auto;
    background-color: hsla(160, 100%, 37%, 0.2);
    width: 95%
}

@media(min-width: 1024px) {
    .result {
        font-size: 2.3em;
    }

    .rank {
        font-size: 2.2em;
    }

    img {
        width: 220px;
        height: 220px;
    }

    div {
        width: 50%;
    }
}
</style>