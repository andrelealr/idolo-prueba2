<template>
    <div>
        <div v-if="peleador">
            <h1>¡Peleador encontrado. Excelente🤟😎!</h1>
            <h3>ID: {{ peleador.id }}</h3>
            <h3>Nombre: {{ peleador.nombre }}</h3>
            <img :src="peleador.imgSrc" alt="" width="600">
        </div>
        <div v-if="!peleador">
            <h1>¡Lo sentimos!</h1>
            <h1>El peleador que buscas no existe😢</h1>
        </div>
    </div>
</template>

<script>

export default {
    name: 'component-name',
    
    data: function () {
        return {
            peleador: {
                id: "",
                nombre: "",
                imgSrc: ""
            }
        }
    },
    
    methods: {
       
        async obtenerIdolo() {
            try {
                const path = process.env.NODE_ENV === "production" ? "/Artes-Marciales/" : "/"
                let data = await fetch(`${path}peleadores.json`)
                if (!data.ok) throw ('Error en petición')

                let json = await data.json()

                this.peleador = json.find((peleador) => peleador.id == this.$route.params.id)

                console.log(this.peleador)
            }
            catch (error) {
                console.log(error)
            }
        },
      
    },
   
    created() {
        this.obtenerIdolo()
    }
   
}
</script>

<style scoped>
</style>