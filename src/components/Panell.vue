<template>
    <div class="web-options">
        <div>
            <label for="pagines">Número de pàgines </label>
            <input type="text" id="pagines" v-model="numPagines" @input="calcPagines">
        </div>
        <div>
            <label for="idiomes">Número d'idiomes </label>
            <input type="text" id="idiomes" v-model="numIdiomes" @input="calcIdiomes">
        </div>
    </div>
</template>

<script>
export default {
    name: 'Panell',
    data() {
        return {
            numPagines: 1,
            numIdiomes: 1,
        }
    },
    methods: {
        calcPagines() {
            this.$emit('calcPagines', this.numPagines)
        },
        calcIdiomes() {
            this.$emit('calcIdiomes', this.numIdiomes)
        }
    }
}
</script>

<style scoped>
.web-options {
    width: 300px;
    border: 2px solid black;
    border-radius: 10px;
    padding: 20px;
    margin: 5px;
}
</style>