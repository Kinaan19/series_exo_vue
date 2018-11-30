<template>
    <div id="Exo02">
        <h3>Hello {{name}} !</h3>
        <input class="mx-3" type="text" placeholder="What's your name ?">
        <button class="btn" @click="clicked">Submit</button>
    </div>
</template>

<script>
export default {
    data(){
        return{
            name: "...",
        }
    },
    methods:{
        clicked(){
            this.name = document.getElementById("Exo02").getElementsByTagName("input")[0].value;
            document.getElementById("Exo02").getElementsByTagName("input")[0].value = "";
        }
    }
    
}
</script>

<style scoped>

</style>

