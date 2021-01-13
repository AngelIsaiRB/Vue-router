<template>
    <Titulo texto="Titulo de mi blog"/>
    <button @click="ConsumirApi">comsumir APi</button>
    <div v-for="item in arrayBlog" :key="item.id">
        <p>{{item.id}}: {{ item.title }}</p>
    </div>
</template>

<script>
import Titulo from "../components/Titulo"

export default {
    components:{
        Titulo,
    },
    data() {
        return {
            arrayBlog: []
        }
    },
    methods: {
        async ConsumirApi() {
            try {
                const data= await fetch("https://jsonplaceholder.typicode.com/posts");
                const array = await data.json();
                this.arrayBlog=array;
            } catch (error) {
                console.log(error)
            }
        }
    },
    created(){
        this.ConsumirApi()
    }
}
</script>

<style>

</style>