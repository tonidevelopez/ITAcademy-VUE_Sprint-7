<template>
    <div class="botons">
        <button @click="sumarQuantitat">+</button>
        <input type="number" v-model="quantitat">
        <button @click="restarQuantitat">-</button>
    </div>
</template>

<script>
export default {
    name: 'Botons',
    emits: ['totalQuantitat'],

    data() {
        return {
            quantitat: 1
        }
    },
    methods: {
        sumarQuantitat() {
            this.quantitat < 1 ? this.quantitat = 1 : this.quantitat++
        },
        restarQuantitat() {
            this.quantitat > 1 ? this.quantitat-- : this.quantitat = 1
        },
        totalQuantitat() {
            this.$emit('totalQuantitat', this.quantitat)
        }
    },
    watch: {
        quantitat() {
            if (this.quantitat < 1) {
                alert("Has d'introduir mínim 1 unitat")
                this.quantitat = 1
            } else {
                this.totalQuantitat()
            }
        }
    }
}
</script>

<style scoped>
input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
}

input[type=number] {
    width: 1.5rem;
    border: none;
}

.botons {
    display: flex;
    align-items: center;
}

button {
    background-color: orange;
    color: white;
    border: none;
    border-radius: 5px;
    width: 2rem;
    height: 2rem;
    font-size: 1.5rem;
}
</style>