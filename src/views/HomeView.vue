<template>
  <div id="pressupost">
    <div id="serveis">
      <p id="titol">Què vols fer?</p>
      <p v-for="servei in serveis" :key="servei.id">
        <input type="checkbox" :id="servei.id" :value="servei.preu" v-model="serveiChecked" @change="calcularTotal">
        {{ servei.descripcio }}
      <div v-if="servei.id === 1 && serveiChecked.includes(500)">
        <Panell @calcPagines="calcPagines" @calcIdiomes="calcIdiomes" />
      </div>
      </p>
      <p id="preu">Preu: {{ preuTotal }}€</p>
    </div>
    <div class="namePressupost">
      <label for="nomPressupost">Nom del pressupost:</label>
      <input type="text" id="nomPressupost" v-model="nomPressupost">
      <label for="nomClient">Client:</label>
      <input type="text" id="nomClient" v-model="nomClient">
    </div>
    <button class="btn btn-primary btn-sm" @click="guardaPressupost">Guardar Pressupost</button>
  </div>
  <div>
    <PressupostList :llistaPressupost="llistaPressupost" />
  </div>
</template>

<script>
import Panell from '../components/Panell.vue'
import PressupostList from '../components/PressupostList.vue'

export default {
  name: 'HomeView',
  components: { Panell, PressupostList },
  data() {
    return {
      serveis: [
        {
          id: 1,
          descripcio: "Una pàgina web (500 €)",
          preu: 500,
        },
        {
          id: 2,
          descripcio: "Una consultoria SEO (300 €)",
          preu: 300,
        },
        {
          id: 3,
          descripcio: "Una campanya de Google Ads (200 €)",
          preu: 200,
        }
      ],
      preuTotal: 0,
      serveiChecked: [],
      numPagines: 1,
      numIdiomes: 1,
      nomPressupost: "",
      nomClient: "",
      llistaPressupost: []
    }
  },
  methods: {
    calcularTotal() {
      this.preuTotal = 0
      this.preuTotal += this.serveiChecked.reduce((a, b) => a + b, 0)
      if (this.serveiChecked.includes(500)) {
        this.preuTotal += this.numPagines * this.numIdiomes * 30
      } else {
        this.numPagines = 1
        this.numIdiomes = 1
      }
    },
    calcPagines(value) {
      this.numPagines = value;
      this.calcularTotal()
    },
    calcIdiomes(value) {
      this.numIdiomes = value;
      this.calcularTotal()
    },
    guardaPressupost() {
      if (this.nomPressupost != "" && this.nomClient != "" && this.preuTotal != 0) {
        this.llistaPressupost.push({
          nomPressupost: this.nomPressupost,
          nomClient: this.nomClient,
          preuTotal: this.preuTotal,
        })
        this.nomClient = ""
        this.nomPressupost = ""
        this.serveiChecked = []
        this.preuTotal = 0
      } else {
        alert("Has d'omplir tots els camps i seleccionar almenys un servei")
      }
      console.table(this.llistaPressupost)
    }
  }
}
</script>

<style scoped>
#pressupost {
  display: flex;
  align-items: center;
  flex-direction: column;
  gap: 20px;
}

#serveis {
  background-color: orange;
  width: 360px;
  padding: 10px 20px 0px;
  border-radius: 10px;
  box-shadow: 5px 5px 5px gray;
}

#titol {
  font-weight: bold;
}

#preu {
  font-weight: bold;
  font-size: 1.3rem;
}

.namePressupost {
  display: flex;
  flex-direction: column;
  width: 400px;
}
</style>