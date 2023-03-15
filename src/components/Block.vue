<template>
    <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
/* eslint-disable */
export default {
    name: 'Block',
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        // console.log('compoennt mounted')
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer() {
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },
        stopTimer() {
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }
    // updated() {
    //     console.log('component update')
    // },
    // unmounted() {

    // }
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: skyblue;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>