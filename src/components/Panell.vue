<template>
    <div class="web-options">
        <div class="inputs">
            <label for="pagines">Número de pàgines</label>
            <Botons @totalQuantitat="calcPagines" />
        </div>
        <div class="inputs">
            <label for="idiomes">Número d'idiomes</label>
            <Botons @totalQuantitat="calcIdiomes" />
        </div>
    </div>
</template>

<script>
import Botons from './Botons.vue'
export default {
    name: 'Panell',
    components: { Botons },
    emits: ['calcPagines', 'calcIdiomes'],

    data() {
        return {
            numPagines: 1,
            numIdiomes: 1,
        }
    },
    methods: {
        calcPagines(numPagines) {
            this.$emit('calcPagines', numPagines)
        },
        calcIdiomes(numIdiomes) {
            this.$emit('calcIdiomes', numIdiomes)
        }
    }
}
</script>

<style scoped>
.web-options {
    width: 230px;
    border: 2px solid black;
    border-radius: 10px;
    padding: 20px;
    margin: 5px;
    line-height: 3rem;
}

.inputs {
    display: flex;
    justify-content: space-between;
}
</style>