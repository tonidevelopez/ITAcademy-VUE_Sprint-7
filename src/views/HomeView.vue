<template>
  <div id="pressupost">
    <div id="serveis">
      <p>Què vols fer?</p>
      <p v-for="servei in serveis" :key="servei.id">
        <input type="checkbox" :id="servei.id" :value="servei.preu" v-model="serveiChecked" @change="calcularTotal">
        {{ servei.descripcio }}
      <div v-if="servei.id === 1 && serveiChecked.includes(500)">
        <Panell @calcPagines="calcPagines" @calcIdiomes="calcIdiomes" />
      </div>
      </p>
      <p id="preu">Preu: {{ preuTotal }}€</p>
    </div>
  </div>
</template>

<script>
import Panell from '../components/Panell.vue'

export default {
  name: 'HomeView',
  components: { Panell },
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
      numIdiomes: 1
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
  }
}
</script>

<style scoped>
#pressupost {
  display: flex;
  justify-content: center;
}

#serveis {
  background-color: orange;
  width: 300px;
  padding: 0 20px;
  border-radius: 10px;
  box-shadow: 5px 5px 5px gray;
}

#preu {
  font-weight: bold;
}
</style>