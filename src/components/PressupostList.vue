<template>
    <div class="llistatPressupost">
        <h3>Llistat de Pressupostos</h3>
        <p v-for=" item in llistaPressupost">
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
            llistaTotalPressupost: this.llistaPressupost
        }
    }
}

</script>

<style scoped>
.llistatPressupost {
    text-align: center;
    line-height: 1rem;
    margin: 20px;
    padding: 10px;
}

.llistatPressupost h3 {
    text-decoration: underline;
    margin: 20px;
}
</style>