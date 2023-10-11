<template>

    <div>
        <h1>Buscar un peleador por id</h1>
        <div class="formulario">
            <input type="text" v-model="id" placeholder="Ingrese la ID del peleador a buscar">
            <input type="submit" value="Buscar" @click.prevent="obtenerIdolo(id)">
        </div>

    </div>


</template>

<script>

export default {
    name: 'view-busqueda',
   
    data: function () {
        return {
            id: "",
        }
    },
   
    methods: {
       
        obtenerIdolo() {

            if (this.id == "") {
                alert("Ingrese un valor")

            } else {
                this.$router.push(`/peleadores/${this.id}`)
            }

        },
       
    },

}
</script>

<style scoped>
.formulario {
    display: grid;
    grid-template-columns: 300px 80px;
    grid-template-rows: 30px;
    gap: 10px;
    justify-content: center;
}
</style>