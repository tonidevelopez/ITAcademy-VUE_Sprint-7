<template>
    <div class="llistatPressupost">
        <h3>Llistat de Pressupostos</h3>
        <div class="botons">
            <button @click="ordenarNom">Ordenar per Nom</button>
            <button @click="ordenarData">Ordenar per Data</button>
            <button @click="reiniciarOrdre">Reiniciar ordre</button>
        </div>
        <div class="input-group mb-3">
            <input type="search" class="form-control rounded" placeholder="Cercar Pressupost..."
                v-model="pressupostCercat" />
            <button type="button" class="btn btn-primary" @click="cercarPressupost">Cercar</button>
        </div>
        <p v-for=" item in pressupostActual">
            <strong>Pressupost: </strong>{{ item.nomPressupost }}
            <strong>Client: </strong>{{ item.nomClient }}
            <strong>Preu: </strong>{{ item.preuTotal }}
            <strong>Data: </strong>{{ item.data.toISOString() }}
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
            pressupostFiltrat: [],
            pressupostActual: this.llistaPressupost,
            pressupostCercat: "",
        }
    },

    methods: {
        ordenarNom() {
            this.pressupostActual = this.pressupostOrdenat
            this.pressupostOrdenat.sort((a, b) => a.nomPressupost.localeCompare(b.nomPressupost))
        },
        ordenarData() {
            this.pressupostActual = this.pressupostOrdenat
            this.pressupostOrdenat.sort((a, b) => a.data.toString().localeCompare(b.data.toString()))
        },
        reiniciarOrdre() {
            this.ordenarData()
        },
        cercarPressupost() {
            if (this.pressupostCercat != "") {
                this.pressupostFiltrat = this.llistaPressupost.filter(item => item.nomPressupost.includes(this.pressupostCercat))
                this.pressupostActual = this.pressupostFiltrat
            }
            if (this.pressupostFiltrat.length == 0) {
                alert("No s'ha trobat")
            }
            this.pressupostCercat = ""
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

.input-group {
    width: 400px;
    margin: 0 auto;
}
</style>