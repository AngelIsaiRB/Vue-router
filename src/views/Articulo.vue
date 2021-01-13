<template>
    <Titulo texto="Rutas con parametro"/>
    <h3>Parametro : {{$route.params.id}}</h3>
    <h1>titulo: </h1>
    <h2>{{articulo.title}}</h2>
    <p>{{articulo.body}}</p>
</template>

<script>
import Titulo from '../components/Titulo.vue'

export default {
    components:{
        Titulo
    },
    data() {
        return {
            articulo:{},
            
        }
    },
    methods: {
        async ConsumirApiId() {
            try {
                const data= await fetch(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`);
                this.articulo = await data.json();               
            } catch (error) {
                console.log(error)
            }
        }
    },
    created () {
        this.ConsumirApiId();
        
    },
}
</script>

<style>

</style>