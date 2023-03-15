<template>
    <div class="score">
        <p>
            {{ score }}
        </p>
        <h1>{{ rank }}</h1>
    </div>
</template>

<script>
export default {
    name: 'ResultDisplay',
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 250) {
            this.rank = 'ANDA CEPAT'
        } else if (this.score < 400 && this.score > 250) {
            this.rank = 'B AJA'
        } else {
            this.rank = 'LAMBAT'
        }
    }
}
</script>

<style>
.score {
    width: 200px;
    height: 200px;
    background: red;
    color: aqua;
    display: flex;
    /* add this property */
    align-items: center;
    /* add this property */
    justify-content: center;
    /* this will center horizontally */
    margin: auto;
    margin-top: 20px;

}
</style>