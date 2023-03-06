<template>
    <div class="llistatPressupost">
        <h3>Llistat de Pressupostos</h3>
        <div class="botons">
            <button @click="ordenarNom">Ordenar per Nom</button>
            <button @click="ordenarData">Ordenar per Data</button>
            <button @click="reiniciarOrdre">Reiniciar ordre</button>
        </div>
        <p v-for=" item in llistaPressupost">
            <strong>Data: </strong>{{ item.data.toUTCString() }}
            <strong>Pressupost: </strong>{{ item.nomPressupost }}
            <strong>Client: </strong>{{ item.nomClient }}
            <strong>Preu: </strong>{{ item.preuTotal }}
        </p>
    </div>
</template>

<script>
export default {
    name: 'PressupostList',
    props: ['llistaPressupost'],

    data() {
        return {
            pressupostOrdenat: this.llistaPressupost,
        }
    },

    methods: {
        ordenarNom() {
            this.pressupostOrdenat.sort((a, b) => a.nomPressupost.localeCompare(b.nomPressupost))
        },
        ordenarData() {
            this.pressupostOrdenat.sort((a, b) => a.data.toString().localeCompare(b.data.toString()))
        },
        reiniciarOrdre() {
            this.ordenarData()
        }
    }
}

</script>

<style scoped>
.llistatPressupost {
    text-align: center;
    line-height: 1rem;
    padding: 10px;
}

.llistatPressupost h3 {
    text-decoration: underline;
    margin-top: 30px;
}

.botons {
    margin-top: 10px;
    margin-bottom: 20px;
    display: flex;
    justify-content: center;
    gap: 10px;
}

button {
    font-size: .8rem;
    border-radius: 5px;
}
</style>