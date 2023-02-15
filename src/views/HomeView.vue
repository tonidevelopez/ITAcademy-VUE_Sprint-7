<template>
  <div>
    <p>Què vols fer?</p>
    <p v-for="servei in serveis" :key="servei.id">
      <input type="checkbox" :id="servei.id" :value="servei.preu" v-model="serveiChecked" @change="calcularTotal">
      {{ servei.descripcio }}
    </p>
    <p>Preu: {{ preuTotal }}€</p>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
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
      serveiChecked: []
    }
  },
  methods: {
    calcularTotal() {
      this.preuTotal = 0
      this.preuTotal += this.serveiChecked.reduce((a, b) => a + b, 0)

      console.log(this.serveiChecked)
    }
  }
}
</script>