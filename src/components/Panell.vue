<template>
    <div class="web-options">
        <div class="inputs">
            <label for="pagines">Número de pàgines</label>
            <Botons @totalQuantitat="calcPagines" />
            <!-- Button trigger modal -->
            <button type="button" class="btn btn-secondary rounded-circle info" data-bs-toggle="modal"
                data-bs-target="#infoPaginesModal">i</button>
            <!-- Modal -->
            <div class="modal fade" id="infoPaginesModal" tabindex="-1" aria-hidden="true">
                <div class="modal-dialog">
                    <div class="modal-content">
                        <div class="modal-body">
                            Aquí ha d'indicar el nombre de pàgines que vol al seu lloc web.
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="inputs">
            <label for="idiomes">Número d'idiomes &nbsp</label>
            <Botons @totalQuantitat="calcIdiomes" />
            <!-- Button trigger modal -->
            <button type="button" class="btn btn-secondary rounded-circle info" data-bs-toggle="modal"
                data-bs-target="#infoIdiomesModal">i</button>
            <!-- Modal -->
            <div class="modal fade" id="infoIdiomesModal" tabindex="-1" aria-hidden="true">
                <div class="modal-dialog">
                    <div class="modal-content">
                        <div class="modal-body">
                            Aquí ha d'indicar quants idiomes tindrà el seu lloc web.
                        </div>
                    </div>
                </div>
            </div>

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
    width: 320px;
    border: 2px solid black;
    border-radius: 10px;
    padding: 20px;
    margin: 5px 0;
    line-height: 3rem;
    background-color: white;
}

.inputs {
    display: flex;
    justify-content: space-between;
}

.info {
    width: 23px;
    height: 23px;
    padding: 0;
    margin-top: 15px;
    font-family: 'Courier New', Courier, monospace;
    font-weight: bold;
}

.modal {
    padding-top: 280px;
    text-align: center;
}
</style>